<template>
    <div class="position-fixed" ref="basicMapbox" style="height:100%;width:100%;">
  </div>
</template>
<script>
import mapboxgl from 'mapbox-gl'
export default {
  name: 'Map',
  data () {
    return {
    }
  },
  mounted () {
    this.init()
  },
  methods: {
    init () {
      mapboxgl.accessToken = 'pk.eyJ1IjoiZmFuemhhbzEyMyIsImEiOiJjanp5d2cxN2YwaWtsM2NydWYxOWRqZmhrIn0.5YEdP_KBjRxdNYn44r9nPQ'
      var coordinates = document.getElementById('coordinates')
      const map = new mapboxgl.Map({
        container: this.$refs.basicMapbox,
        style: 'mapbox://styles/fanzhao123/cjzzce9c613621dtgb0rgvus5',
        center: [148.961177, -37.813330],
        zoom: 6
      })

      map.addControl(new mapboxgl.GeolocateControl({
        positionOptions: {
          enableHighAccuracy: true
        },
        trackUserLocation: true,
        showUserLocation: true,
        zoom: 14
      }))

      var marker = new mapboxgl.Marker({
        draggable: true
      })
      function onDragEnd () {
        var lngLat = marker.getLngLat()
        coordinates.style.display = 'block'
        coordinates.innerHTML = 'Longitude: ' + lngLat.lng + '<br />Latitude: ' + lngLat.lat
      }
      marker.on('dragend', onDragEnd)
      map.addControl(new mapboxgl.MapboxGeocoder({
        accessToken: mapboxgl.accessToken
      }))
    }
  },
  computed: {
  }
}
</script>

<style lang="stylus" scoped>
  @import url('https://api.tiles.mapbox.com/mapbox-gl-js/v0.44.2/mapbox-gl.css')
</style>
