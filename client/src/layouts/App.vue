<script>
  export default {
    name: 'App',

    data () {
      return {
        isCustomer: false,
        isAdmin: false
      }
    },

    mounted () {
      this.init()
    },

    updated () {
      this.init()
    },

    methods: {
      init () {
        this.$icons.replace()
        this.identifySidebar()
      },
      identifySidebar () {
        if (this.$route.name.match(/back\./g)) {
          this.isCustomer = false
          this.isAdmin = true
        } else {
          this.isAdmin = false
          this.isCustomer = true
        }
      }
    }
  }
</script>

<template>
  <div data-component="layout-app">
    <nav-bar/>
    <div class="container-fluid">
      <div class="row">
        <nav class="col-md-2 d-none d-md-block bg-light sidebar">
          <side-bar-customer v-if="isCustomer"/>
          <side-bar-admin v-else/>
        </nav>

        <main role="main" class="col-md-9 ml-sm-auto col-lg-10 pt-3 px-4">
          <router-view/>
        </main>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
  @import "../assets/scss/app";
</style>
