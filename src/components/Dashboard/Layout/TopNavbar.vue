<template>
  <nav class="navbar navbar-expand-lg" style="background-color: #F2F6FC">
    <div class="container-fluid">
      <a class="navbar-brand" href="#"><font color="#000000" size="2">Workload status tracking system based on </font><font color="#002089" size="2">Scrum</font><font color="#000000" size="2"> solution via posts upon </font><font color="#002089" size="2">Facebook</font><font color="#000000" size="2"> page. </font></a>
    </div>
  </nav>
</template>

<script>
  export default {
    computed: {
      routeName () {
        const {name} = this.$route
        return this.capitalizeFirstLetter(name)
      }
    },
    data () {
      return {
        activeNotifications: false
      }
    },
    methods: {
      capitalizeFirstLetter (string) {
        return string.charAt(0).toUpperCase() + string.slice(1)
      },
      toggleNotificationDropDown () {
        this.activeNotifications = !this.activeNotifications
      },
      closeDropDown () {
        this.activeNotifications = false
      },
      toggleSidebar () {
        this.$sidebar.displaySidebar(!this.$sidebar.showSidebar)
      },
      hideSidebar () {
        this.$sidebar.displaySidebar(false)
      }
    }
  }

</script>

<style>

</style>
