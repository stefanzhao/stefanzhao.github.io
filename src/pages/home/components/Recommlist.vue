<template>
  <section class="bg-light" id="portfolio">
    <div class="container">
      <div class="row">
        <div class="col-lg-12 text-center">
          <h2 class="section-heading text-uppercase">Recommended for you</h2>
          <!--          <h3 class="section-subheading text-muted">Lorem ipsum dolor sit amet consectetur.</h3>-->
        </div>
      </div>
      <div class="row">

        <div class="col-md-4 col-sm-6 portfolio-item" v-for="(obj, key) in portfolioJSON" :key="key">
          <a class="portfolio-link" data-toggle="modal" href="#portfolioModal2">
            <div class="portfolio-hover">
              <div class="portfolio-hover-content">
                <i class="fas fa-plus fa-3x"></i>
              </div>
            </div>
            <img class="img-fluid" :src="obj.imgUrl">
          </a>
          <div class="portfolio-caption">
            <h4>{{ obj.title }}</h4>
            <p class="text-muted">{{ obj.desc }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data: () => ({
    portfolioJSON: [
      {
        imgUrl: 'https://a0.muscache.com/im/pictures/82af5bc4-ed5b-44d9-9209-ac0f2fbf8986.jpg?aki_policy=large',
        title: 'Sheepyard Flat',
        desc: 'Brocks Road, Howqua Hills, Victoria'
      },
      {
        imgUrl: 'https://a0.muscache.com/im/pictures/c674c063-129c-4e55-9031-c02037034a78.jpg?aki_policy=large',
        title: 'McGaurans Beach',
        desc: '26 McGaurans Beach Rd, Giffard, Victoria'
      },
      {
        imgUrl: 'https://a0.muscache.com/im/pictures/33648231-ea24-46d5-9d9f-887cc1417ff2.jpg?aki_policy=large',
        title: 'Yanakie Caravan Park',
        desc: '390 Foley Road, Yanakie, Victoria, 3960, AU'
      },
      {
        imgUrl: 'https://a0.muscache.com/im/pictures/e9262129-79e8-4d03-a714-b01c702cb281.jpg?aki_policy=large',
        title: 'Tidal River Camping & Caravan Site',
        desc: 'Wilsons Promontory Rd, Tidal River, Victoria'
      },
      {
        imgUrl: 'https://a0.muscache.com/im/pictures/2d81fac2-0df0-4129-b6a2-af760f049a76.jpg?aki_policy=large',
        title: 'Bear Gully Camp Site',
        desc: '465 Bear Gully Rd, Tarwin Lower, Victoria'
      },
      {
        imgUrl: 'https://a0.muscache.com/im/pictures/89d213eb-1904-44c9-b8ae-815e9935a52a.jpg?aki_policy=large',
        title: 'Skipworth Reserve',
        desc: '4350 Mansfield-Woods Point Road, Kevington, Victoria'
      }
    ]
  })
}
</script>

<style lang="css">
</style>
