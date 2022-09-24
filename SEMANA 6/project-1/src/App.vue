<script>
export default {
  name: "App"
};
</script>

<template>
  <nav class="flex flex-row gap-4"  >
    <router-link class="col 2 rbutton" to="/">Go to Home</router-link>
    <router-link class="col 2 rbutton" to="/product">Product</router-link>
    <router-link class="col 2 rbutton" to="/comment">Comment</router-link>
    <router-link class="col 2 rbutton" to="/post">Post</router-link>
  </nav>

  <main>
    <router-view />
  </main>

</template>

<style>
.rbutton{
  color: #EEEEEE;
  cursor: pointer;
  text-decoration: none;
  cursor: pointer;
  font-family: "Montserrat SemiBold";
  font-size: 20px;
}
</style>
