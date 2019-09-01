<template>
    <div class="card" >
      <div class="card-body">
        <div class="card mb-3" style="max-width: 540px;" v-for="(item, key) in list" :key="key">
          <div class="row no-gutters">
            <div class="col-md-4">
<!--              t<img class="card-img" :src="item.">-->
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">{{item.name}}</h5>
                <p class="card-text text-overflow:ellipsis">{{item.access_desc}}</p>
                  <p class="card-text text-overflow:ellipsis">{{item.distance+' km'}}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'CompsiteList',
  props: {
    list: Array
  },
  data () {
  }
}
</script>

<style lang="stylus" scoped>
 .card-text
   overflow: hidden;
   -webkit-line-clamp: 2;
   text-overflow: ellipsis;
   display: -webkit-box;
   -webkit-box-orient: vertical;
</style>
