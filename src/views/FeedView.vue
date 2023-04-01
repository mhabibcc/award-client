<script setup>
  import SideNav from '../components/SideNav.vue';
  import CardComponent from '../components/CardComponent.vue';
  import FilterComponent from '../components/FilterComponent.vue';
</script>

<template>
  <div class="wrapper">
    <SideNav/>
    <FilterComponent/>
    <nav class="navbar fixed-top navbar-light bg-light">
      <div class="container-fluid">
      <span class="navbar-toggler-icon" @click="openNav()"></span>
      <a class="navbar-brand" href="#"><strong>Awards</strong></a>
      <span class="navbar-brand" @click="openFilter()"><i class="bi bi-filter"></i></span>
      </div>
    </nav>

    <div class="feed content-wrapper">
      <CardComponent v-for="item in data" :exchange="item.pointExchange" :img-url="item.awardImage" :type="item.awardType" :name="item.awardName"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      serverHost: import.meta.env.VITE_SERVER_HOST,
      filter: {
        point: null,
        type: null,
      },
      data: [],
      nextCursor: 0,
    }
  },
  beforeMount() {
    this.handlefilter()
  },
  mounted() {
    this.getNext()
  },
  methods: {
    openNav(){
      document.getElementById("mySidenav").style.width = "250px";
      document.getElementById("cover").style.width = "100%";
    },
    openFilter(){
      document.getElementById("filterComponent").style.width = "100%";
    },
    handlefilter(cursor = 0) {
          this.isBusy = true
          // const page = 1

          const url = new URL(window.location.href);
          const params = new URLSearchParams(url.search);
          params.append('cursor', cursor);
          if (this.filter.point !== null && this.filter.point !== '') {
            params.append('point', this.filter.point);
          }
          if (this.filter.type !== null && this.filter.type !== '') {
              params.append('type', this.filter.type)
          }
          axios.get(`${this.serverHost}awards?${params.toString()}`)
          .then((data) => {
            this.data.push(...data.data)
            if (this.data.length > 0) {
              var lastIndex = this.data.length - 1
              this.nextCursor = this.data[lastIndex].id
            }
          })
          .catch((err) => {
            console.log(err)
          })
      },
      getNext() {
        window.onscroll = () => {
          let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight + 1.5 > document.documentElement.offsetHeight;
          console.log("scrolled ", bottomOfWindow, document.documentElement.scrollTop, window.innerHeight, document.documentElement.scrollTop + window.innerHeight + 1.5,document.documentElement.offsetHeight)
          if (bottomOfWindow) {
            this.handlefilter(this.nextCursor)
          }
        }
    }
  }
}
</script>

<style>
@media (min-width: 1024px) {
  .feed {
    min-height: 100vh;
    display: grid;
    align-items: center;
  }
}
</style>
