<template>
  <nav class="navbar">
    <div class="container">
      <div class="navbar-brand">
        <span class="navbar-burger burger" @click="showNav = !showNav" :class="{ 'is-active': showNav }">
            <span></span>
            <span></span>
            <span></span>
        </span>
      </div>
      <div class="navbar-menu" :class="{ 'is-active': showNav }">
        <div class="navbar-end">
          <div :key="item.path" v-for="item in items">
            <router-link :to="item.path" active-class="is-active" class="navbar-item" exact>{{ item.name }}
            </router-link>
          </div>
          <div>
            <a href="http://bit.ly/2lzOIHe" class="navbar-item">
              Pesquisa
            </a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
    export default {
        name: "v-nav",
        created() {
            this.$router.options.routes.forEach(route => {
                this.items.push({
                    name: route.name,
                    path: route.path
                });
            });
        },
        data() {
            return {
                items: [],
                showNav: false
            };
        }
    };
</script>
