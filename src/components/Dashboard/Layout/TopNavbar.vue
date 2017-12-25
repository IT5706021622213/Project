<template>
  <nav class="navbar navbar-expand-lg" style="background-color: #272728">
    <div class="container-fluid">
      <a class="navbar-brand" href="#"><font color="#FFF" size="2">Workload status tracking system based on Scrum solution via posts upon Facebook page</font></a>
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
