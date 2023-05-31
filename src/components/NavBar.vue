<template>
  <div id="nav">
    <RouterLink to="/" id="logo-url">
      <img :src="logo" :alt="alt" id="logo" />
    </RouterLink>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/pedidos">Pedidos</RouterLink>
  </div>
</template>

<script>
import { RouterLink } from "vue-router";

export default {
  name: "NavBar",
  props: ["logo", "alt"],
};
</script>
<style>
#nav {
  background-color: #222;
  border-bottom: 4px solid #111;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#nav #logo-url {
  margin: auto;
  margin-left: 0;
}

#logo {
  height: 40px;
  width: 40px;
}

#nav a {
  text-decoration: none;
  color: #fcba03;
  margin: 12px;
  transition: 0.5s;
}
#nav a:hover {
  color: #fff;
}
</style>
