<template>
    <div>
        <div id="mySidenav" class="sidenav">
            <div class="logo">
                <img src="/award-cropped.png" alt="">
                <h4><strong>Awards Menu</strong></h4>
            </div>
            <a class="a active" href="#">Home</a>
            <a class="a" href="#">Cards</a>
            <a class="a" href="#">Profile</a>
            <router-link class="a" :to="`/`">Logout</router-link>
        </div>
        <div id="cover" @click="closeNav()">
        </div>
    </div>
</template>

<script>
export default {
    data() {
    return {
      
    }
  },
  methods: {
    closeNav(){
      document.getElementById("mySidenav").style.width = "0px";
      document.getElementById("cover").style.width = "0px";
    }
  }
}
</script>

<style scoped>
#cover {
    background-color: rgba(0, 0, 0, 0.311);
    width: 0;
    height: 100%;
    position: fixed;
    z-index: 1031;
    top: 0;
    left: 0;
    overflow-x: hidden;
    padding-top: 60px; /* Place content 60px from the top */
}
/* The side navigation menu */
.sidenav {
  height: 100%; /* 100% Full-height */
  width: 0; /* 0 width - change this with JavaScript */
  position: fixed; /* Stay in place */
  z-index: 1032; /* Stay on top */
  top: 0; /* Stay at the top */
  left: 0;
  background-color: #fff;
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 60px; /* Place content 60px from the top */
  transition: 0.5s; /* 0.5 second transition effect to slide in the sidenav */
}

.sidenav .logo{
    width: 250px;
}

.sidenav .logo img{
    width: 100px;
    padding: 8px 8px 8px 32px;
}

.sidenav h4{
  padding: 8px 8px 8px 32px;
}

/* The navigation menu links */
.sidenav .a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 1em;
  color: #818181;
  display: block;
  transition: 0.3s;
}

/* When you mouse over the navigation links, change their color */
.sidenav .a:hover {
  color: #262525;
}

.sidenav .active {
  color: #262525;
}

/* Style page content - use this if you want to push the page content to the right when you open the side navigation */
#main {
  transition: margin-left .5s;
  padding: 20px;
}

/* On smaller screens, where height is less than 450px, change the style of the sidenav (less padding and a smaller font size) */
@media screen and (max-height: 450px) {
  .sidenav {padding-top: 15px;}
  .sidenav a {font-size: 18px;}
}
</style>