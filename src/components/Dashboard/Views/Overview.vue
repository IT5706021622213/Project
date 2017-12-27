<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-3" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888;" align="center">
          <h4 class="card-title">All Job</h4>
          {{ count }}
          <p class="card-category">Job</p>
        </div>

        <div class="col-md-3" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888;" align="center">
          <h4 class="card-title">To Do</h4>
          {{ todocount }}
          <p class="card-category">Job</p>
        </div>

        <div class="col-md-3" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888;" align="center">
          <h4 class="card-title">In Progress</h4>
          {{ doneprogress }}
          <p class="card-category">Job</p>
        </div>

        <div class="col-md-3" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888;" align="center">
          <h4 class="card-title">Done</h4>
          {{ donecount }}
          <p class="card-category">Job</p>
        </div>
      </div>
    </div>

    <br>

    <div class="row">
      <div class="col-md-6">
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
      </div>

      <div class="col-md-6">
        <chart-card :chart-data="pieChart.data" chart-type="Pie">
          <template slot="header">
            <h4 class="card-title">Email Statistics</h4>
            <p class="card-category">Last Campaign Performance</p>
          </template>
          <template slot="footer">
            <div class="legend">
              <i class="fa fa-circle text-info"></i> To Do
              <i class="fa fa-circle text-danger"></i> In progress
              <i class="fa fa-circle text-warning"></i> Done
            </div>
            <hr>
            <div class="stats">
              <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalA">
                Launch demo modal A
              </button>
            </div>
          </template>
        </chart-card>
      </div>

      <!-- งานทั้งหมด : {{ count }} <br>
      To Do : {{ sumall - count }}<br>
      In Progress : {{ sumprogress }} <br>
      Done : {{ donecount }}<br><br> -->

      <!-- Performance<br>
      งานทั้งหมดที่มีคนทำ : {{ PerformanceA }}<br>
      งานทั้งหมดที่กำลังทำอยู่ : {{ PerformanceA - PerformanceB }}<br>
      งานทั้งหมดที่ทำเสร็จแล้ว : {{ PerformanceB }}<br>
      งานทั้งหมดที่ทำเสร็จตามเวลา : {{ PerformanceOnTime }}<br>
      งานทั้งหมดที่ทำเสร็จล่าช้า : {{ PerformanceDelay }}<br><br> -->

      <!-- Apinan Singbut<br>
      งานทั้งหมดที่ Apinan เป็นคนทำ : {{ ApinanA }}<br>
      งานทั้งหมดที่ Apinan กำลังทำอยู่ : {{ ApinanA - ApinanB }}<br>
      งานทั้งหมดที่ Apinan ทำเสร็จแล้ว : {{ ApinanB }}<br>
      งานทั้งหมดที่ Apinan ทำเสร็จตามเวลา : {{ ApinanOnTime }}<br>
      งานทั้งหมดที่ Apinan ทำเสร็จล่าช้า : {{ ApinanDelay }}<br><br> -->

      <!-- P'Tang Ratabhoom Boongate<br>
      งานทั้งหมดที่ P'Tang Ratabhoom Boongate เป็นคนทำ : {{ TangA }}<br>
      งานทั้งหมดที่ P'Tang Ratabhoom Boongate กำลังทำอยู่ : {{ TangA - TangB }}<br>
      งานทั้งหมดที่ P'Tang Ratabhoom Boongate ทำเสร็จแล้ว : {{ TangB }}<br>
      งานทั้งหมดที่ P'Tang Ratabhoom Boongate ทำเสร็จตามเวลา : {{ TangOnTime }}<br>
      งานทั้งหมดที่ P'Tang Ratabhoom Boongate ทำเสร็จล่าช้า : {{ TangDelay }}<br> -->

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
        progresscount: 0,
        doneprogress: 0,
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
        sumall: '',
        barChart: {
          data: {
            labels: ['User A'],
            series: [
              [30],
              [10],
              [50],
              [20],
              [40]
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
      todocount () {
        // this.$set(this.pieChart.data.series, 'labels', ['10%', '10%', '80%'])
        this.pieChart.data.series = [ this.todocount, this.doneprogress, this.donecount]
        this.pieChart.data.labels = [ `${this.todocount}`, `${this.doneprogress}`, `${this.donecount}`]
      },
      ApinanA () {
        // this.$set(this.pieChart.data.series, 'labels', ['10%', '10%', '80%'])
        this.barChart.data.series = [
          [this.PerformanceA],
          [this.PerformanceSum],
          [this.PerformanceB],
          [this.PerformanceOnTime],
          [this.PerformanceDelay]
        ]
      }
    },
    // Fetches posts when the component is created.
    created () {
      let that = this
      axios.get('https://graph.facebook.com/138501810233037?fields=feed&access_token=EAACEdEose0cBALcRP1StkZCQhPMfZAtKeFjTloneONNldfDLPxhKqqIW903pDPegzVW94ZAJJ4qiuUNO5X5a3yZAu7IftGWgvvOGI6IyvoD4jGqVr00IZABX00xUNaCrXZBXZCtBaK8h5lGUrZBnZApZBLvZAMESshOGugjmMYFo50jZB7rhJT8YZBf88Siq5Wr7FvGwZD')
      .then(response => {
        this.posts = response.data
        // console.log(this.posts.feed.data)s
        // let cut = posts => this.posts.filter(this.posts.feed.data.message.substr(0, 5) === '#ToDo')
        this.posts.feed.data.forEach(function (message) {
          // To Do
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
          // End To Do
        })
      })
      axios.get('https://graph.facebook.com/138501810233037?fields=feed{comments}&access_token=EAACEdEose0cBALcRP1StkZCQhPMfZAtKeFjTloneONNldfDLPxhKqqIW903pDPegzVW94ZAJJ4qiuUNO5X5a3yZAu7IftGWgvvOGI6IyvoD4jGqVr00IZABX00xUNaCrXZBXZCtBaK8h5lGUrZBnZApZBLvZAMESshOGugjmMYFo50jZB7rhJT8YZBf88Siq5Wr7FvGwZD')
      .then(response => {
        this.comments = response.data
        // console.log(this.comments.feed.data[0].comments.data[0].from.name)
        // console.log(this.comments.feed.data[0].comments.data[0].message)
        this.comments.feed.data.forEach(function (comment) {
          // let result = that.todo.find(item => item === comment.fields
          // console.log(result)
          // that.progress.push(result)
          // console.log(comment.id)
          comment.comments.data.forEach(function (progress) {
            // console.log(progress.message)
            // console.log(progress.from.name)
            // comment start

            // In Progress
            if (progress.message === '#start') {
              let result = that.todo.find(item => item.id === comment.id)
              result.status = 'กำลังทำ'
              result.date = progress.created_time.substr(8, 2)
              result.dmy = progress.created_time.substr(0, 10)
              result.name = progress.from.name
              that.progresscount++
              that.sumall = that.doneprogress + that.donecount
              that.doneprogress = that.progresscount - that.donecount
              // doneprogress : In Progress
              that.todocount = that.count - that.progresscount
              // todocount : To Do
              that.todo.push(result)

              console.log(that.todocount)
              console.log('scrum')
              // console.log(that.test.id)
            }
            // End In progress

            // Done
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
                that.donecount++
                // donecount : Done
                that.todo.push(result)

                // console.log(result.status)
                // console.log(that.test.id)
              }
            }
            // End Done

            let results = that.todo.find(item => item.id === comment.id)
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
    height: 150px;
    border-radius: 2px; /*ความโค้งมนของขอบบล๊อก*/
    box-shadow: 0 0 15px #333 ; /*เงาของบล๊อก*/
    background: #FFF; /*สีบล๊อก*/
  }
</style>
