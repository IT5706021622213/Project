<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-3" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888;" align="center">
          <h4 style="font-weight: 300; padding-top:15px;">All Job</h4>
          {{ count }}
          <p style="font-weight: 300;">Job</p>
        </div>

        <div class="col-md-3" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888;" align="center">
          <h4 style="font-weight: 300; padding-top:15px;">To Do</h4>
          {{ todocount }}
          <p style="font-weight: 300;">Job</p>
        </div>

        <div class="col-md-3" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888;" align="center">
          <h4 style="font-weight: 300; padding-top:15px;">In Progress</h4>
          {{ PerformanceInProgress }}
          <p style="font-weight: 300;">Job</p>
        </div>

        <div class="col-md-3" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888;" align="center">
          <h4 style="font-weight: 300; padding-top:15px;">Done</h4>
          {{ donecount }}
          <p style="font-weight: 300;">Job</p>
        </div>
      </div>
    </div>

    <br>

    <div class="row">
      <div class="col-md-4">
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
            <div class="legend" style="margin-top: -25px;">
              <i class="fa fa-circle" style="color:#1DC7EA"></i> งานทั้งหมดที่มีคนทำ : {{ PerformanceA }} งาน<br>
              <i class="fa fa-circle" style="color:#FB404B"></i> งานทั้งหมดที่กำลังทำอยู่ : {{ PerformanceInProgress }} งาน<br>
              <i class="fa fa-circle" style="color:#FFA534"></i> งานทั้งหมดที่ทำเสร็จแล้ว : {{ PerformanceDone }} งาน<br>
              <i class="fa fa-circle" style="color:#9368E9"></i> งานทั้งหมดที่ทำเสร็จตามเวลา : {{ PerformanceOnTime }} งาน<br>
              <i class="fa fa-circle" style="color:#87CB16"></i> งานทั้งหมดที่ทำเสร็จล่าช้า : {{ PerformanceDelay }} งาน<br>
            </div>
            <div class="stats">
              <!-- <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalB">
                Launch demo modal B
              </button> -->
            </div>
          </template>
        </chart-card>
      </div>

      <div class="col-md-4">
        <chart-card :chart-data="pieChart.data" chart-type="Pie">
          <template slot="header">
            <h4 class="card-title">Email Statistics</h4>
            <p class="card-category">Last Campaign Performance</p>
          </template>
          <template slot="footer">
            <div class="legend" style="margin-top: -25px; padding-bottom: 65px;">
              <i class="fa fa-circle" style="color:#1DC7EA"></i> To Do : {{ todocount }} Job<br>
              <i class="fa fa-circle" style="color:#FB404B"></i> In progress : {{ PerformanceInProgress }} Job<br>
              <i class="fa fa-circle" style="color:#FFA534"></i> Done : {{ PerformanceDone }} Job<br>
            </div>
            <div class="stats">
              <!-- <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalA">
                Launch demo modal A
              </button> -->
            </div>
          </template>
        </chart-card>
      </div>

      <div class="col-md-4">
        <div class="col-md-12" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888; padding-bottom: 35px;">
          <h4 style="font-weight: 300; padding-top:15px;">2014 Sales</h4>
          <p style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px;">All products including Taxes</p>
          <section>
            <h4 style="font-weight: 300;">Apinan Singbut : {{ progress1 }} Job</h4>
            <div style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px; padding-bottom: 10px;">Position : Programmer</div>
            <progress-bar v-model="progress1"/>
            <h4 style="font-weight: 300; padding-top: 10px;">Nitigan Nakjuatong : {{ progress2 }} Job</h4>
            <div style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px; padding-bottom: 10px;">Position : Testing</div>
            <progress-bar v-model="progress2"/>
            <h4 style="font-weight: 300; padding-top: 10px;">Personnel C : {{ progress3 }} Job</h4>
            <div style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px; padding-bottom: 10px;">Position : Personnel</div>
            <progress-bar v-model="progress3"/>
            <h4 style="font-weight: 300; padding-top: 10px;">Personnel D : {{ progress4 }} Job</h4>
            <div style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px; padding-bottom: 10px;">Position : Personnel</div>
            <progress-bar v-model="progress4"/>
            <h4 style="font-weight: 300; padding-top: 10px;">Personnel E : {{ progress5 }} Job</h4>
            <div style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px; padding-bottom: 10px;">Position : Personnel</div>
            <progress-bar v-model="progress5"/>
          </section>
        </div>
      </div>
    </div>

      <!-- <chart-card :chart-data="pieChart.data" chart-type="Pie">
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
      </chart-card> -->

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
</template>
<script>
  import ChartCard from 'src/components/UIComponents/Cards/ChartCard.vue'
  import StatsCard from 'src/components/UIComponents/Cards/StatsCard.vue'
  import Card from 'src/components/UIComponents/Cards/Card.vue'
  import LTable from 'src/components/UIComponents/Table.vue'
  import Checkbox from 'src/components/UIComponents/Inputs/Checkbox.vue'
  import axios from 'axios'

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
        donecount: 0,

        feedid: 0,

        PerformanceA: 0,
        PerformanceDone: 0,
        PerformanceInProgress: 0,
        PerformanceOnTime: 0,
        PerformanceDelay: 0,

        progress1: 40,
        progress2: 20,
        progress3: 60,
        progress4: 80,
        progress5: 65,

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
        this.pieChart.data.series = [ this.todocount, this.PerformanceInProgress, this.PerformanceDone]
        this.pieChart.data.labels = [ `${this.todocount}`, `${this.PerformanceInProgress}`, `${this.PerformanceDone}`]
      },
      ApinanA () {
        // this.$set(this.pieChart.data.series, 'labels', ['10%', '10%', '80%'])
        this.barChart.data.series = [
          [this.PerformanceA],
          [this.PerformanceInProgress],
          [this.PerformanceDone],
          [this.PerformanceOnTime],
          [this.PerformanceDelay]
        ]
      }
    },
    // Fetches posts when the component is created.
    created () {
      let that = this
      axios.get('https://graph.facebook.com/138501810233037?fields=feed&access_token=EAACEdEose0cBAA5UF6U8bJHkyjJO87zj2MFMYeDgxZCuycRUZBggZAcuFWo5Op3t6nTu7LC1pUw3qQqxCUoklvyhPJKOBzW1NTvBmmA5ZBKikBFBKLZAgP3xCubKAYVQK3XBoTTKk98UZA0iwCcOPiZBYgkG9nS7MxXI1OV06xcuMOWjqcrXXYsOm53FmT7ZC7sZD')
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
      axios.get('https://graph.facebook.com/138501810233037?fields=feed{comments}&access_token=EAACEdEose0cBAA5UF6U8bJHkyjJO87zj2MFMYeDgxZCuycRUZBggZAcuFWo5Op3t6nTu7LC1pUw3qQqxCUoklvyhPJKOBzW1NTvBmmA5ZBKikBFBKLZAgP3xCubKAYVQK3XBoTTKk98UZA0iwCcOPiZBYgkG9nS7MxXI1OV06xcuMOWjqcrXXYsOm53FmT7ZC7sZD')
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
            // if (progress.message === '#start') {
            //   let result = that.todo.find(item => item.id === comment.id)
            //   result.status = 'กำลังทำ'
            //   result.date = progress.created_time.substr(8, 2)
            //   result.dmy = progress.created_time.substr(0, 10)
            //   result.name = progress.from.name
            //   that.progresscount++
            //   console.log(that.progresscount);
            //   // doneprogress : In Progress
            //   that.todocount = that.count - that.progresscount
            //   // todocount : To Do
            //   that.todo.push(result)
            //
            //   // console.log(that.todocount)
            //   // console.log('scrum')
            //   // console.log(that.test.id)
            // }
            if (progress.message === '#start' && result.status === 'ยังไม่ได้ทำ') {
              // let result = that.todo.find(item => item.id === comment.id)
              result.status = 'กำลังทำ'
              result.date = progress.created_time.substr(8, 2)
              result.dmy = progress.created_time.substr(0, 10)
              // if (progress.message.substr(0, 5) === '#name') {
              //   result.name = result.name + progress.message.substr(6, 20)
              // }
              that.progresscount++
              that.number = progress.created_time.substr(9, 1)
              that.todo.push(result)
              // console.log(that.datetime)
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
              that.PerformanceDone++
            }
            if (results.dash === 'On time') {
              that.PerformanceOnTime++
            }
            if (results.dash === 'Delay') {
              that.PerformanceDelay++
            }
            that.PerformanceInProgress = that.PerformanceA - that.PerformanceDone

            // -------------------------------------------------------
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
  .progress-bar{
    display: -ms-flexbox;
    display: flex;
    -ms-flex-align: center;
    align-items: center;
    -ms-flex-pack: center;
    justify-content: center;
    color: #fff;
    background-color: #87CB16;
  }
</style>
