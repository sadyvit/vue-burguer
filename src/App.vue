<template>
  <div>
  <NavBar :logo="logo_src" :alt="alt_name" />
  <RouterView />
    <Footer>AAAAAAAAAAAAAAA
      
    </Footer>
</div>
</template>

<script>
import { RouterView } from "vue-router";
import { defineComponent } from "vue";
import NavBar from "./components/NavBar.vue";
import Footer from "./components/Footer.vue";

export default defineComponent({
  name: "App",
  components: {
    NavBar,
    Footer,
  },
  data() {
    return {
      logo_src: "/img/logo.png",
      alt_src: "Make your Burger",
    };
  },
});
</script>

<style>
* {
  font-family: Helvetica, sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main-container {
  min-height: 250px;
  margin: 50px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin: 30px;
  color: #222;
}
</style>
