<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">

        <div class="col-md-6">
          <div class="dashboardone">
            <div class="col-md-12" style="padding-top:1px; padding-left:20px; padding-bottom: 1px;">
              <h4>Summary Operating Results</h4>
            </div>
            <hr>
            <div class="col-md-12" style="padding-top:1px; padding-left:20px; padding-bottom: 1px;">
              <progress class="progress is-info" v-bind:value="count" max="30"> {{ count }} %</progress>
              <progress class="progress is-danger" v-bind:value="sumtodo" max="30"> {{ sumall - count }} %</progress>
              <progress class="progress is-warning" v-bind:value="sumprogress" max="30"> {{ sumprogress }} %</progress>
              <progress class="progress is-success" v-bind:value="donecount" max="30"> {{ donecount }} %</progress>
            </div>
            <hr>
            <div style="padding-top:1px; padding-left:20px; padding-bottom: 1px;">
              <i class="fa fa-circle text-info"></i> All Workload : {{ count }} % <br>
              <i class="fa fa-circle text-danger"></i> To Do : {{ sumall - count }} % <br>
              <i class="fa fa-circle text-warning"></i> In progress : {{ sumprogress }} % <br>
              <i class="fa fa-circle text-success"></i> Done : {{ donecount }} % <br>
            </div>
          </div>
        </div>

        <div class="col-md-6">
          <div class="dashboardone">
            <div class="col-md-12" style="padding-top:1px; padding-left:20px; padding-bottom: 1px;">
              <h4>Performance Report</h4>
            </div>
            <hr>
            <div class="col-md-12" style="padding-top:1px; padding-left:20px; padding-bottom: 1px;">
              <progress class="progress is-info" v-bind:value="PerformanceA" max="30"> {{ PerformanceA }} %</progress>
              <progress class="progress is-warning" v-bind:value="PerformanceSum" max="30"> {{ PerformanceSum }} %</progress>
              <progress class="progress is-success" v-bind:value="PerformanceB" max="30"> {{ PerformanceB }} %</progress>
              <progress class="progress is-primary" v-bind:value="PerformanceOnTime" max="30"> {{ PerformanceOnTime }} %</progress>
              <progress class="progress is-danger" v-bind:value="PerformanceDelay" max="30"> {{ PerformanceDelay }} %</progress>
            </div>
            <hr>
            <div style="padding-top:1px; padding-left:20px; padding-bottom: 1px;">
              <i class="fa fa-circle text-info"></i> All work is done : {{ PerformanceA }} % <br>
              <i class="fa fa-circle text-warning"></i> All work is doing : {{ PerformanceA - PerformanceB }} % <br>
              <i class="fa fa-circle text-success"></i> All work is success : {{ PerformanceB }} % <br>
              <i class="fa fa-circle text-primary"></i> All work done on time : {{ PerformanceOnTime }} % <br>
              <i class="fa fa-circle text-danger"></i> All work done is delayed : {{ PerformanceDelay }} % <br>
              <div style="padding-top:10px;" align="center">
                <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalA">
                  Apinan Singbut
                </button>
                <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalB">
                  P'Tang Ratabhoom Boongate
                </button>
              </div>
            </div>
          </div>
        </div>

      </div>

      <br>

      <div class="row">
        <!-- <div class="col-md-6">
          <chart-card :chart-data="pieChart.data" chart-type="Pie">
            <template slot="header">
              <h4 class="card-title">Email Statistics</h4>
              <p class="card-category">Last Campaign Performance</p>
            </template>
            <template slot="footer">
              <div class="legend">
                <i class="fa fa-circle text-info"></i> Open
                <i class="fa fa-circle text-danger"></i> Bounce
                <i class="fa fa-circle text-warning"></i> Unsubscribe
              </div>
              <hr>
              <div class="stats">

                <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalA">
                  Launch demo modal A
                </button>

              </div>
            </template>
          </chart-card>
        </div> -->

        <!-- <div class="col-md-6">
          <chart-card
            :chart-data="barChart.data"
            :chart-options="barChart.options"
            :chart-responsive-options="barChart.responsiveOptions"
            chart-type="Bar">
            <template slot="header">
              <h4 class="card-title">2014 Sales</h4>
              <p class="card-category">All products including Taxes</p>
            </template>
            <template slot="footer">
              <div class="legend">
                <i class="fa fa-circle text-info"></i> Tesla Model S
                <i class="fa fa-circle text-danger"></i> BMW 5 Series
              </div>
              <hr>
              <div class="stats">

                <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalB">
                  Launch demo modal B
                </button>

              </div>
            </template>
          </chart-card>
        </div> -->

        <!-- งานทั้งหมด : {{ count }} <br>
        To Do : {{ sumall - count }}<br>
        In Progress : {{ sumprogress }} <br>
        Done : {{ donecount }}<br><br> -->

        <!-- Performance<br>
        งานทั้งหมดที่มีคนทำ : {{ PerformanceA }}<br>
        งานทั้งหมดที่กำลังทำอยู่ : {{ PerformanceA - PerformanceB }}<br>
        งานทั้งหมดที่ทำเสร็จแล้ว : {{ PerformanceB }}<br>
        งานทั้งหมดที่ทำเสร็จตามเวลา : {{ PerformanceOnTime }}<br>
        งานทั้งหมดที่ทำเสร็จล่าช้า : {{ PerformanceDelay }}<br><br>

        Apinan Singbut<br>
        งานทั้งหมดที่ Apinan เป็นคนทำ : {{ ApinanA }}<br>
        งานทั้งหมดที่ Apinan กำลังทำอยู่ : {{ ApinanA - ApinanB }}<br>
        งานทั้งหมดที่ Apinan ทำเสร็จแล้ว : {{ ApinanB }}<br>
        งานทั้งหมดที่ Apinan ทำเสร็จตามเวลา : {{ ApinanOnTime }}<br>
        งานทั้งหมดที่ Apinan ทำเสร็จล่าช้า : {{ ApinanDelay }}<br><br>

        P'Tang Ratabhoom Boongate<br>
        งานทั้งหมดที่ P'Tang Ratabhoom Boongate เป็นคนทำ : {{ TangA }}<br>
        งานทั้งหมดที่ P'Tang Ratabhoom Boongate กำลังทำอยู่ : {{ TangA - TangB }}<br>
        งานทั้งหมดที่ P'Tang Ratabhoom Boongate ทำเสร็จแล้ว : {{ TangB }}<br>
        งานทั้งหมดที่ P'Tang Ratabhoom Boongate ทำเสร็จตามเวลา : {{ TangOnTime }}<br>
        งานทั้งหมดที่ P'Tang Ratabhoom Boongate ทำเสร็จล่าช้า : {{ TangDelay }}<br> -->

        <!-- Modal A -->
        <div class="modal fade" id="exampleModalA" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
          <div class="modal-dialog" role="document">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">Apinan Singbut</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                  <span aria-hidden="true">&times;</span>
                </button>
              </div>
              <div class="modal-body">
                <progress class="progress is-info" v-bind:value="ApinanA" max="30"> {{ ApinanA }} %</progress>
                <progress class="progress is-warning" v-bind:value="ApinanA" max="30"> {{ ApinanSum }} %</progress>
                <progress class="progress is-success" v-bind:value="ApinanB" max="30"> {{ ApinanB }} %</progress>
                <progress class="progress is-primary" v-bind:value="ApinanOnTime" max="30"> {{ ApinanOnTime }} %</progress>
                <progress class="progress is-danger" v-bind:value="ApinanDelay" max="30"> {{ ApinanDelay }} %</progress>
                <hr>
                <i class="fa fa-circle text-info"></i> All work at Apinan Singbut is done : {{ ApinanA }} % <br>
                <i class="fa fa-circle text-warning"></i> All the work that Apinan Singbut is doing : {{ ApinanA - ApinanB }} % <br>
                <i class="fa fa-circle text-success"></i> All work at Apinan Singbut is success : {{ ApinanB }} % <br>
                <i class="fa fa-circle text-primary"></i> All work at Apinan Singbut is Finished in time : {{ ApinanOnTime }} % <br>
                <i class="fa fa-circle text-danger"></i> All work at Apinan Singbut is Delayed : {{ ApinanDelay }} % <br>
              </div>
              <div class="modal-footer">

              </div>
            </div>
          </div>
        </div>
        <!-- End Modal A -->

        <!-- Modal B -->
        <div class="modal fade" id="exampleModalB" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
          <div class="modal-dialog" role="document">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">P'Tang Ratabhoom Boongate</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                  <span aria-hidden="true">&times;</span>
                </button>
              </div>
              <div class="modal-body">
                <progress class="progress is-info" v-bind:value="TangA" max="30"> {{ TangA }} %</progress>
                <progress class="progress is-warning" v-bind:value="TangSum" max="30"> {{ TangSum }} %</progress>
                <progress class="progress is-success" v-bind:value="TangB" max="30"> {{ TangB }} %</progress>
                <progress class="progress is-primary" v-bind:value="TangOnTime" max="30"> {{ TangOnTime }} %</progress>
                <progress class="progress is-danger" v-bind:value="TangDelay" max="30"> {{ TangDelay }} %</progress>
                <hr>
                <i class="fa fa-circle text-info"></i> All work at P'Tang Ratabhoom Boongate is done : {{ TangA }} % <br>
                <i class="fa fa-circle text-warning"></i> All the work that P'Tang Ratabhoom Boongate is doing : {{ TangA - TangB }} % <br>
                <i class="fa fa-circle text-success"></i> All work at P'Tang Ratabhoom Boongate is success : {{ TangB }} % <br>
                <i class="fa fa-circle text-primary"></i> All work at P'Tang Ratabhoom Boongate is Finished in time : {{ TangOnTime }} % <br>
                <i class="fa fa-circle text-danger"></i> All work at P'Tang Ratabhoom Boongate is Delayed : {{ TangDelay }} % <br>
              </div>
              <div class="modal-footer">

              </div>
            </div>
          </div>
        </div>
        <!-- End Modal B -->

      </div>
    </div>
  </div>
</template>
<script>
  import ChartCard from 'src/components/UIComponents/Cards/ChartCard.vue'
  import StatsCard from 'src/components/UIComponents/Cards/StatsCard.vue'
  import Card from 'src/components/UIComponents/Cards/Card.vue'
  import LTable from 'src/components/UIComponents/Table.vue'
  import Checkbox from 'src/components/UIComponents/Inputs/Checkbox.vue'
  import axios from 'axios';

  export default {
    components: {
      Checkbox,
      Card,
      LTable,
      ChartCard,
      StatsCard
    },
    data () {
      return {
        data: [300, 50, 100],
        posts: [],
        comments: [],
        errors: [],
        todo: [],
        todoo: [],
        progress: [],
        done: [],
        datetime: '',
        testy: 'hello',
        count: 0,
        todocount: 0,
        sumtodo: 0,
        progresscount: 0,
        sumprogress: 0,
        donecount: 0,
        feedid: 0,

        PerformanceA: 0,
        PerformanceB: 0,
        PerformanceSum: 0,
        PerformanceOnTime: 0,
        PerformanceDelay: 0,

        ApinanA: 0,
        ApinanB: 0,
        ApinanSum: 0,
        ApinanOnTime: 0,
        ApinanDelay: 0,

        TangA: 0,
        TangB: 0,
        TangSum: 0,
        TangOnTime: 0,
        TangDelay: 0,

        editTooltip: 'Edit Task',
        deleteTooltip: 'Remove',
        number:10,
        pieChart: {
          data: {
            labels: ['40%', '20%', '40%'],
            series: [40, 20, 40]
          }
        },
        barChart: {
          data: {
            labels: ['Jan', 'Feb', 'Mar', 'Apr', 'Mai', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
            series: [
              [542, 443, 320, 780, 553, 453, 326, 434, 568, 610, 756, 895],
              [412, 243, 280, 580, 453, 353, 300, 364, 368, 410, 636, 695]
            ]
          },
          options: {
            seriesBarDistance: 10,
            axisX: {
              showGrid: false
            },
            height: '245px'
          },
          responsiveOptions: [
            ['screen and (max-width: 640px)', {
              seriesBarDistance: 5,
              axisX: {
                labelInterpolationFnc (value) {
                  return value[0]
                }
              }
            }]
          ]
        }
      }
    },
    computed: {
      chartData () {
        return {
          labels: [
            'Red',
            'Blue',
            'Yellow'
          ],
          datasets: [{
            data: this.data,
            backgroundColor: [
              '#FF6384',
              '#36A2EB',
              '#FFCE56'
            ]
          }]
        }
      }
    },
    mounted () {
      let that = this
      that.datetime = Date().substr(8, 2)
      setInterval(() => {
        // https://github.com/vuejs/vue/issues/2873
        // Array.prototype.$set/$remove deprecated (use Vue.set or Array.prototype.splice instead)
        this.data.forEach((item, i) => {
          this.data.splice(i, 1, Math.ceil(Math.random() * 1000))
        })
      }, 1024)
    },
    watch: {
      count () {
        this.pieChart.data.series[0] = this.count
      }
    },
    // Fetches posts when the component is created.
    created () {
      let that = this
      axios.get('https://graph.facebook.com/138501810233037?fields=feed&access_token=EAACEdEose0cBAD7ikBUNoJNMNw2SNbq0BxAalhMZC94EmewnGkcFwIOJZBmndyIXvD4tEYfKGUrarjMMLq83zxsbdJFtYFvqTSchg9Hmqfs0KECJCEWrnIi7NEZBMPa6R5xuHi6Cl4ZAqwt41YBVZCknTn2pblZAXtuOOA01rfeKqC1onKOGE0bZC5prGl8x9sZD')
      .then(response => {
        this.posts = response.data
        // console.log(this.posts.feed.data)s
        // let cut = posts => this.posts.filter(this.posts.feed.data.message.substr(0, 5) === '#ToDo')

        this.posts.feed.data.forEach(function (message) {
          if (message.message.substr(0, 5) === '#ToDo') {
            let newmessage = {
              id: message.id,
              name: '',
              msg: message.message.substr(6),
              status: 'ยังไม่ได้ทำ',
              date: '',
              dmy: '',
              ondelay: '',
              dash: ''
            }
            // console.log(comment.id)
            that.todo.push(newmessage)
            that.progress.push(newmessage)
            that.done.push(newmessage)
            that.count++
            that.test = that.count

            // if (that.todo.status === 'กำลังทำ') {
            //   console.log('connect')
            // }

            // console.log(that.test.id)
            // that.todo.push(message.message.substr(6))
            // that.todo.push(message.id)
            // that.feedid = message.id
            // console.log(that.feedid)
          }
        })
      })
      axios.get('https://graph.facebook.com/138501810233037?fields=feed{comments}&access_token=EAACEdEose0cBAD7ikBUNoJNMNw2SNbq0BxAalhMZC94EmewnGkcFwIOJZBmndyIXvD4tEYfKGUrarjMMLq83zxsbdJFtYFvqTSchg9Hmqfs0KECJCEWrnIi7NEZBMPa6R5xuHi6Cl4ZAqwt41YBVZCknTn2pblZAXtuOOA01rfeKqC1onKOGE0bZC5prGl8x9sZD')
      .then(response => {
        this.comments = response.data
        // console.log(this.comments.feed.data[0].comments.data[0].from.name)
        // console.log(this.comments.feed.data[0].comments.data[0].message)
        this.comments.feed.data.forEach(function (comment) {
          // let result = that.todo.find(item => item === comment.fields
          // console.log(result);
          // that.progress.push(result)
          // console.log(comment.id)
          comment.comments.data.forEach(function (progress) {
            // console.log(progress.message);
            // console.log(progress.from.name);ssssssssss

            // comment start
            if (progress.message === '#start') {
              let result = that.todo.find(item => item.id === comment.id)

              result.status = 'กำลังทำ'
              result.date = progress.created_time.substr(8, 2)
              result.dmy = progress.created_time.substr(0, 10)
              result.name = progress.from.name
              that.progresscount++
              that.sumall = (that.progresscount + that.donecount)
              that.sumprogress = that.progresscount - that.donecount
              that.sumtodo = (that.progresscount + that.donecount)-that.count
              that.todo.push(result)
              // if (that.todo.name === 'Apinan Singbut') {
              //   that.ApinanA++
              //   console.log(that.ApinanA)
              // }

              // console.log(that.datetime)
              // console.log(that.test.id)

            }
            // End comment start
            if (progress.message === '#end') {
              let result = that.todo.find(item => item.id === comment.id)
              if (result.status === 'กำลังทำ') {


              result.status = 'ทำเสร็จแล้ว'
              result.ondelay = progress.created_time.substr(8, 2)
              if (result.date === result.ondelay) {
                result.dash = 'On time'

              }
              else {
                result.dash = 'Delay'

              }
              // console.log(result.status)
              that.donecount++
              that.todo.push(result)

              // console.log(that.test.id)sssหsss
            }
            }

            let results = that.todo.find(item => item.id === comment.id)
            console.log(results.status)
            if (results.status === 'กำลังทำ') {
              that.PerformanceA++
            }
            if (results.status === 'ทำเสร็จแล้ว') {
              that.PerformanceB++
            }
            if (results.dash === 'On time') {
              that.PerformanceOnTime++
            }
            if (results.dash === 'Delay') {
              that.PerformanceDelay++
            }
            that.PerformanceSum = that.PerformanceA - that.PerformanceB

            if (results.status === 'กำลังทำ' && results.name === 'Apinan Singbut') {
              that.ApinanA++
            }
            if (results.status === 'ทำเสร็จแล้ว' && results.name === 'Apinan Singbut') {
              that.ApinanB++
            }
            if (results.dash === 'On time' && results.name === 'Apinan Singbut') {
              that.ApinanOnTime++
            }
            if (results.dash === 'Delay' && results.name === 'Apinan Singbut') {
              that.ApinanDelay++
            }
            that.ApinanSum = that.ApinanA - that.ApinanB

            if (results.status === 'กำลังทำ' && results.name === "P'Tang Ratabhoom Boongate") {
              that.TangA++
            }
            if (results.status === 'ทำเสร็จแล้ว' && results.name === "P'Tang Ratabhoom Boongate") {
              that.TangB++
            }
            if (results.dash === 'On time' && results.name === "P'Tang Ratabhoom Boongate") {
              that.TangOnTime++
            }
            if (results.dash === 'Delay' && results.name === "P'Tang Ratabhoom Boongate") {
              that.TangDelay++
            }
            that.TangSum = that.TangA - that.TangB
          })
          // console.log(that.progress)
        })
      })
      .catch(e => {
        this.errors.push(e)
      })
    }
  }
</script>
<style>
  .dashboardone{ /*บล๊อขาว*/
    margin: auto; /*บล๊อกอยู่กลาง*/
    width: 90%;
    height: 510px;
    border-radius: 2px; /*ความโค้งมนของขอบบล๊อก*/
    box-shadow: 0 0 15px #333 ; /*เงาของบล๊อก*/
    background: #FFF; /*สีบล๊อก*/
  }
</style>
