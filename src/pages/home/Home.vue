<template>
  <div id="app">

    <!-- Navigation -->
    <nav class="navbar navbar-expand-lg navbar-dark fixed-top" id="mainNav">
      <div class="container">
        <a class="navbar-brand js-scroll-trigger" href="#page-top">Camping Me</a>
        <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
          Menu
          <i class="fas fa-bars"></i>
        </button>
        <div class="collapse navbar-collapse" id="navbarResponsive">
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
        </div>
      </div>
    </nav>

    <!-- Header -->
    <header class="masthead">
      <div class="container">
        <div class="intro-text">
          <div class="intro-heading text-uppercase"> {{str2}} </div>
          <div class="col-md-10 col-lg-8 col-xl-7 mx-auto">
            <form>
              <div class="form-row">
                <div class="col-12 col-md-9 mb-2 mb-md-0">
                  <input type="search" class="form-control form-control-lg" placeholder="Search for Campsites near...">
                </div>
                <div class="col-12 col-md-3">
                  <router-link to="/search" tag="button" class="btn btn-block btn-lg btn-primary">Search
                  </router-link>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </header>

    <!-- recommondation Grid -->
    <home-recomm></home-recomm>

    <!-- Footer -->
    <footer>
      <div class="container">
        <div class="row">
          <div class="col-md-4">
            <span class="copyright">Copyright &copy; Camping Me 2019</span>
          </div>
<!--          <div class="col-md-4">-->
<!--            <ul class="list-inline social-buttons">-->
<!--              <li class="list-inline-item">-->
<!--                <a href="#">-->
<!--                  <i class="fab fa-twitter"></i>-->
<!--                </a>-->
<!--              </li>-->
<!--              <li class="list-inline-item">-->
<!--                <a href="#">-->
<!--                  <i class="fab fa-facebook-f"></i>-->
<!--                </a>-->
<!--              </li>-->
<!--              <li class="list-inline-item">-->
<!--                <a href="#">-->
<!--                  <i class="fab fa-linkedin-in"></i>-->
<!--                </a>-->
<!--              </li>-->
<!--            </ul>-->
<!--          </div>-->
<!--          <div class="col-md-4">-->
<!--            <ul class="list-inline quicklinks">-->
<!--              <li class="list-inline-item">-->
<!--                <a href="#">Privacy Policy</a>-->
<!--              </li>-->
<!--              <li class="list-inline-item">-->
<!--                <a href="#">Terms of Use</a>-->
<!--              </li>-->
<!--            </ul>-->
<!--          </div>-->
        </div>
      </div>
    </footer>

  </div>
</template>

<script>
import HomeRecomm from './components/Recommlist'
export default {
  name: 'Home',
  components: {
    HomeRecomm
  },
  data: function () {
    return {
      str: 'start you camping',
      i: 0,
      timer: 0,
      str2: ''
    }
  },
  methods: {
    typing () {
      if (this.i <= this.str.length) {
        this.str2 = this.str.slice(0, this.i++)
        this.timer = setTimeout(() => {
          this.typing()
        }, 200)
      } else {
        clearTimeout(this.timer)
      }
    }
  },
  mounted () {
    this.typing()
  }
}
</script>

<style lang="stylus" scoped>
  .router-link-active{
    text-decoration: none;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  body {
    background: black;
  }

</style>
