<template>
  <nav class="navbar navbar-expand-lg" style="">
    <div class="col-md-10">
      <a class="navbar-brand" href="#"><font color="#272829" size="2">Workload status tracking system based on Scrum solution via posts upon Facebook page.</font></a>
    </div>
    <div class="col-md-2">
      <a class="navbar-brand" href="#"><font color="#272829" size="2">Date : {{ datetime }} {{ datetimeday }} {{ datetimemonth }} {{ datetimeyear }}</font></a>
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
        activeNotifications: false,
        datetime: '',
        datetimeday: '',
        datetimemonth: '',
        datetimeyear: ''
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
    },
    mounted () {
      let that = this
      // that.datetime = Date()
      that.datetime = Date().substr(0, 3)
      that.datetimeday = Date().substr(8, 2)
      that.datetimemonth = Date().substr(4, 3)
      that.datetimeyear = Date().substr(11, 4)
    }
  }

</script>

<style>

</style>
