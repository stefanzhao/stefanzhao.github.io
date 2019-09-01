<template>
<div>
  <nav class="navbar navbar-expand-lg navbar-dark fixed-top " id="mainNav">
    <div class="container">
      <router-link class="navbar-brand js-scroll-trigger" to="/">Camping Me</router-link>
      <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
        Menu
        <i class="fas fa-bars"></i>
      </button>
      <div class="collapse navbar-collapse flex-column  ml-lg-0 ml-3 " id="navbarResponsive">
        <ul class="navbar-nav text-uppercase ml-auto">
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" >Help</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger">Sign Up</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger">Log in</a>
          </li>
        </ul>
        <ul class="navbar-nav text-uppercase ml-auto">
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" @click="sortDistance">sort by distance</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" @click="fliterHeritage">heritage</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" @click="filterPicnic">picnic</a>
          </li>
        <form class="form-inline ml-auto">
          <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
          <button class="btn btn-outline-light my-2 my-sm-0" type="submit">Search</button>
        </form>
        </ul>
      </div>
    </div>
  </nav>

  <div class="row">
    <div class="col-sm-6"  id="searchlist">
      <search-list :list="mapList"></search-list>
    </div>
    <div class="col-sm-6 " id="searchmap">
      <search-map></search-map>
    </div>
  </div>

  <footer>
    <div class="container">
      <div class="row">
        <div class="col-md-4">
          <span class="copyright">Copyright &copy; Camping Me 2019</span>
        </div>
      </div>
    </div>
  </footer>
  </div>
</template>

<script>
import SearchList from './components/CompsiteList'
import SearchMap from './components/Map'
import axios from 'axios'
export default {
  name: 'Search',
  components: {
    SearchList,
    SearchMap
  },
  data () {
    return {
      mapList: [],
      fliterList: [],
      orgMap: []
    }
  },
  methods: {
    getListInfo () {
      axios.get('http://localhost:8080/data/maplist.json')
        .then(this.getListInfosucc)
    },
    getListInfosucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.mapList = data.mapList
        for (let i in this.mapList) {
          var dis = this.$options.methods.distance(this.mapList[i].lat, this.mapList[i].lon, -37.813330, 144.961177)
          // console.log(dis)
          dis = parseFloat(dis).toFixed(2)
          this.$set(this.mapList[i], 'distance', dis)
        }
        // console.log(this.mapList)
      }
    },
    fliterHeritage () {
      const filterList = []
      for (let i in this.mapList) {
        if (this.mapList[i].heritage === 'Y') {
          filterList.push(this.mapList[i])
          // console.log(filterList)
        }
      }
      this.mapList = filterList
    },
    filterPicnic () {
      const filterList = []
      for (let i in this.mapList) {
        if (this.mapList[i].picnic === 'Y') {
          filterList.push(this.mapList[i])
          // console.log(filterList)
        }
      }
      this.mapList = filterList
    },
    distance (lat1, lon1, lat2, lon2) {
      var p = 0.017453292519943295 // Math.PI / 180
      var c = Math.cos
      var a = 0.5 - c((lat2 - lat1) * p) / 2 +
        c(lat1 * p) * c(lat2 * p) *
        (1 - c((lon2 - lon1) * p)) / 2

      return 12742 * Math.asin(Math.sqrt(a)) // 2 * R; R = 6371 km
    },
    sortDistance () {
      function compare (a, b) {
        if (a.distance < b.distance) { return -1 }
        if (a.distance > b.distance) { return 1 }
        return 0
      }
      return this.mapList.sort(compare)
    }

  },
  mounted () {
    this.getListInfo()
  }
}
</script>

<style lang="stylus" scoped>
  .map-container-6{
    overflow:hidden;
    padding-bottom:56.25%;
    position:relative;
    height:0;
  }
  .map-container-6 iframe{
    left:0;
    top:0;
    height:100%;
    width:100%;
    position:absolute;
  }
  #mainNav
   background : #1d2124
  .card-img
    position:relative
    top:50%
    transform:translateY(-50%)
    padding-left :.4rem
  #searchlist
    padding-top : 10rem
    padding-left : 2rem
  #searchmap
    padding-top :10rem
</style>
