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
          {{ progresscount }}
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
              <i class="fa fa-circle" style="color:#FB404B"></i> งานทั้งหมดที่กำลังทำอยู่ : {{ PerformanceB }} งาน<br>
              <i class="fa fa-circle" style="color:#FFA534"></i> งานทั้งหมดที่ทำเสร็จแล้ว : {{ PerformanceC }} งาน<br>
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
              <i class="fa fa-circle" style="color:#FB404B"></i> In progress : {{ progresscount }} Job<br>
              <i class="fa fa-circle" style="color:#FFA534"></i> Done : {{ donecount }} Job<br>
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
        <div class="col-md-12" style="background-color: #FFFFFF; box-shadow: 0 0 1px #888; padding-bottom: 80px;">
          <h4 style="font-weight: 300; padding-top:15px;">2014 Sales</h4>
          <p style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px;">All products including Taxes</p>
          <section>
            <h4 style="font-size: 16px; font-weight: 300;">Apinan Singbut : {{ progress1 }} Job</h4>
            <div style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px; padding-bottom: 10px;">Position : Programmer</div>
            <progress-bar v-model="progress1"/>
            <h4 style="font-size: 16px; font-weight: 300; padding-top: 10px;">P'Tang Ratabhoom Boongate : {{ progress2 }} Job</h4>
            <div style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px; padding-bottom: 10px;">Position : UI / UX</div>
            <progress-bar v-model="progress2"/>
            <h4 style="font-size: 16px; font-weight: 300; padding-top: 10px;">Nitigan Nakjuatong : {{ progress3 }} Job</h4>
            <div style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px; padding-bottom: 10px;">Position : Testing</div>
            <progress-bar v-model="progress3"/>
            <h4 style="font-size: 16px; font-weight: 300; padding-top: 10px;">ไข่ต้ม รมควัน : {{ progress4 }} Job</h4>
            <div style="font-size: 14px; font-weight: 400; color: #9A9A9A; margin-top: -6px; padding-bottom: 10px;">Position : Designer</div>
            <progress-bar v-model="progress4"/>
            <h4 style="font-size: 16px; font-weight: 300; padding-top: 10px;">Netiwit Keawthong : {{ progress5 }} Job</h4>
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
        number: 0,

        count: 0,
        todocount: 0,
        progresscount: 0,
        donecount: 0,
        doneprogress: 0,

        feedid: 0,

        PerformanceA: 0,
        PerformanceB: 0,
        PerformanceC: 0,
        PerformanceOnTime: 0,
        PerformanceDelay: 0,

        Apinan: 0,
        Ratabhoom: 0,
        Nitigan: 0,
        Nattapong: 0,
        Netiwit: 0,

        progress1: 0,
        progress2: 0,
        progress3: 0,
        progress4: 0,
        progress5: 0,

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
      if (that.datetime === '01') {
        that.datetime = 1
      }
      if (that.datetime === '02') {
        that.datetime = 2
      }
      if (that.datetime === '03') {
        that.datetime = 3
      }
      if (that.datetime === '04') {
        that.datetime = 4
      }
      if (that.datetime === '05') {
        that.datetime = 5
      }
      if (that.datetime === '06') {
        that.datetime = 6
      }
      if (that.datetime === '07') {
        that.datetime = 7
      }
      if (that.datetime === '08') {
        that.datetime = 8
      }
      if (that.datetime === '09') {
        that.datetime = 9
      }
      if (that.datetime === '10') {
        that.datetime = 10
      }
      if (that.datetime === '11') {
        that.datetime = 11
      }
      if (that.datetime === '12') {
        that.datetime = 12
      }
      if (that.datetime === '13') {
        that.datetime = 13
      }
      if (that.datetime === '14') {
        that.datetime = 14
      }
      if (that.datetime === '15') {
        that.datetime = 15
      }
      if (that.datetime === '16') {
        that.datetime = 16
      }
      if (that.datetime === '17') {
        that.datetime = 17
      }
      if (that.datetime === '18') {
        that.datetime = 18
      }
      if (that.datetime === '19') {
        that.datetime = 19
      }
      if (that.datetime === '20') {
        that.datetime = 20
      }
      if (that.datetime === '21') {
        that.datetime = 21
      }
      if (that.datetime === '22') {
        that.datetime = 22
      }
      if (that.datetime === '23') {
        that.datetime = 23
      }
      if (that.datetime === '24') {
        that.datetime = 24
      }
      if (that.datetime === '25') {
        that.datetime = 25
      }
      if (that.datetime === '26') {
        that.datetime = 26
      }
      if (that.datetime === '27') {
        that.datetime = 27
      }
      if (that.datetime === '28') {
        that.datetime = 28
      }
      if (that.datetime === '29') {
        that.datetime = 29
      }
      if (that.datetime === '30') {
        that.datetime = 30
      }
      if (that.datetime === '31') {
        that.datetime = 31
      }
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
        this.pieChart.data.series = [ this.todocount, this.progresscount, this.donecount]
        this.pieChart.data.labels = [ `${this.todocount}`, `${this.progresscount}`, `${this.donecount}`]
      },
      PerformanceA () {
        // this.$set(this.pieChart.data.series, 'labels', ['10%', '10%', '80%'])
        this.barChart.data.series = [
          [this.PerformanceA],
          [this.PerformanceB],
          [this.PerformanceC],
          [this.PerformanceOnTime],
          [this.PerformanceDelay]
        ]
      }
    },
    // Fetches posts when the component is created.
    created () {
      let that = this
      axios.get('https://graph.facebook.com/138501810233037?fields=feed&access_token=EAACEdEose0cBAMhHdhhZBafkFawjMVpZC9rFFNMj10RLfH0YimEAf2Kl41yRoNZBRHnoHRWnMTZAP3xttkV1tdOZBzB8LdwxmtRfZAkaycVWnl67IdZBMJxIO9JDdqWsMHTdlyWabkg4j6953LtnkkeTujvVfU6F55uDJrt8Mf1Ae7gvCFT3vNY48n3amt2m4sZD')
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
              ondelayday: '',
              dash: '',
              tododmy: '',
              todotime: '',
              day: '',
              my: '',
              dateend: '',
              dateendday: ''
            }
            // console.log(comment.id)
            that.todo.push(newmessage)
            that.progress.push(newmessage)
            that.done.push(newmessage)
            that.count++
            that.tododmy = message.updated_time.substr(0, 10)
            that.todotime = message.updated_time.substr(11, 5)
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
      axios.get('https://graph.facebook.com/138501810233037?fields=feed{comments}&access_token=EAACEdEose0cBAMhHdhhZBafkFawjMVpZC9rFFNMj10RLfH0YimEAf2Kl41yRoNZBRHnoHRWnMTZAP3xttkV1tdOZBzB8LdwxmtRfZAkaycVWnl67IdZBMJxIO9JDdqWsMHTdlyWabkg4j6953LtnkkeTujvVfU6F55uDJrt8Mf1Ae7gvCFT3vNY48n3amt2m4sZD')
      .then(response => {
        this.comments = response.data
        this.comments.feed.data.forEach(function (comment) {
          comment.comments.data.forEach(function (progress) {
            let result = that.todo.find(item => item.id === comment.id)

            // In Progress
            if (progress.message === '#start' && result.status === 'ยังไม่ได้ทำ') {
              // let result = that.todo.find(item => item.id === comment.id)
              result.status = 'กำลังทำ'
              result.date = progress.created_time.substr(8, 2)
              result.dmy = progress.created_time.substr(0, 10)
              that.number = progress.created_time.substr(9, 1)
              that.todo.push(result)
              if (result.status === 'กำลังทำ') {
                that.progresscount++
              }
              // console.log('scrum')
              // console.log(that.test.id)
            }
            // End In progress

            // Name
            if (progress.message.substr(0, 5) === '#name') {
              if (progress.message.substr(6, 20) === '') {
                result.name = result.name + ''
              }
              else result.name = result.name + 'Name : ' + progress.message.substr(6, 20)
            }
            // End name

            // Date
            if (progress.message.substr(0, 5) === '#date') {
              if (progress.message.substr(6, 20) === '') {
                result.dateend = ''
              }
              else {
                result.dateend = progress.message.substr(6, 10)
                result.dateendday = progress.message.substr(14, 2)
                if (result.dateendday === '01') {
                  result.dateendday = 1
                }
                if (result.dateendday === '02') {
                  result.dateendday = 2
                }
                if (result.dateendday === '03') {
                  result.dateendday = 3
                }
                if (result.dateendday === '04') {
                  result.dateendday = 4
                }
                if (result.dateendday === '05') {
                  result.dateendday = 5
                }
                if (result.dateendday === '06') {
                  result.dateendday = 6
                }
                if (result.dateendday === '07') {
                  result.dateendday = 7
                }
                if (result.dateendday === '08') {
                  result.dateendday = 8
                }
                if (result.dateendday === '09') {
                  result.dateendday = 9
                }
                if (result.dateendday === '10') {
                  result.dateendday = 10
                }
                if (result.dateendday === '11') {
                  result.dateendday = 11
                }
                if (result.dateendday === '12') {
                  result.dateendday = 12
                }
                if (result.dateendday === '13') {
                  result.dateendday = 13
                }
                if (result.dateendday === '14') {
                  result.dateendday = 14
                }
                if (result.dateendday === '15') {
                  result.dateendday = 15
                }
                if (result.dateendday === '16') {
                  result.dateendday = 16
                }
                if (result.dateendday === '17') {
                  result.dateendday = 17
                }
                if (result.dateendday === '18') {
                  result.dateendday = 18
                }
                if (result.dateendday === '19') {
                  result.dateendday = 19
                }
                if (result.dateendday === '20') {
                  result.dateendday = 20
                }
                if (result.dateendday === '21') {
                  result.dateendday = 21
                }
                if (result.dateendday === '22') {
                  result.dateendday = 22
                }
                if (result.dateendday === '23') {
                  result.dateendday = 23
                }
                if (result.dateendday === '24') {
                  result.dateendday = 24
                }
                if (result.dateendday === '25') {
                  result.dateendday = 25
                }
                if (result.dateendday === '26') {
                  result.dateendday = 26
                }
                if (result.dateendday === '27') {
                  result.dateendday = 27
                }
                if (result.dateendday === '28') {
                  result.dateendday = 28
                }
                if (result.dateendday === '29') {
                  result.dateendday = 29
                }
                if (result.dateendday === '30') {
                  result.dateendday = 30
                }
                if (result.dateendday === '31') {
                  result.dateendday = 31
                }
                that.dateend = result.dateend
              }
            }
            // End date

            // Done
            if (progress.message === '#end' && result.status === 'กำลังทำ') {
              // let result = that.todo.find(item => item.id === comment.id)
              result.status = 'ทำเสร็จแล้ว'
              result.ondelay = progress.created_time.substr(0, 10)
              result.ondelayday = progress.created_time.substr(8, 2)
              if (result.ondelayday === '01') {
                result.ondelayday = 1
              }
              if (result.ondelayday === '02') {
                result.ondelayday = 2
              }
              if (result.ondelayday === '03') {
                result.ondelayday = 3
              }
              if (result.ondelayday === '04') {
                result.ondelayday = 4
              }
              if (result.ondelayday === '05') {
                result.ondelayday = 5
              }
              if (result.ondelayday === '06') {
                result.ondelayday = 6
              }
              if (result.ondelayday === '07') {
                result.ondelayday = 7
              }
              if (result.ondelayday === '08') {
                result.ondelayday = 8
              }
              if (result.ondelayday === '09') {
                result.ondelayday = 9
              }
              if (result.ondelayday === '10') {
                result.ondelayday = 10
              }
              if (result.ondelayday === '11') {
                result.ondelayday = 11
              }
              if (result.ondelayday === '12') {
                result.ondelayday = 12
              }
              if (result.ondelayday === '13') {
                result.ondelayday = 13
              }
              if (result.ondelayday === '14') {
                result.ondelayday = 14
              }
              if (result.ondelayday === '15') {
                result.ondelayday = 15
              }
              if (result.ondelayday === '16') {
                result.ondelayday = 16
              }
              if (result.ondelayday === '17') {
                result.ondelayday = 17
              }
              if (result.ondelayday === '18') {
                result.ondelayday = 18
              }
              if (result.ondelayday === '19') {
                result.ondelayday = 19
              }
              if (result.ondelayday === '20') {
                result.ondelayday = 20
              }
              if (result.ondelayday === '21') {
                result.ondelayday = 21
              }
              if (result.ondelayday === '22') {
                result.ondelayday = 22
              }
              if (result.ondelayday === '23') {
                result.ondelayday = 23
              }
              if (result.ondelayday === '24') {
                result.ondelayday = 24
              }
              if (result.ondelayday === '25') {
                result.ondelayday = 25
              }
              if (result.ondelayday === '26') {
                result.ondelayday = 26
              }
              if (result.ondelayday === '27') {
                result.ondelayday = 27
              }
              if (result.ondelayday === '28') {
                result.ondelayday = 28
              }
              if (result.ondelayday === '29') {
                result.ondelayday = 29
              }
              if (result.ondelayday === '30') {
                result.ondelayday = 30
              }
              if (result.ondelayday === '31') {
                result.ondelayday = 31
              }
              // console.log(result.dateendday);
              // console.log(result.ondelayday);
              if (result.dateendday >= result.ondelayday) {
                that.PerformanceOnTime++
                // console.log('On');
              }
              if (result.dateendday < result.ondelayday)  {
                that.PerformanceDelay++
                // console.log('De');
              }
              that.progresscount--
              that.donecount++
              that.doneprogress = that.donecount + that.progresscount
              that.PerformanceA = that.donecount + that.progresscount
              that.PerformanceB = that.progresscount
              that.PerformanceC = that.donecount
              that.todocount = that.count - that.doneprogress
              that.todo.push(result)

              // console.log(result.status)
              // console.log(that.test.id)
              // console.log(result.dash);
            }
            // End Done
            if (progress.message.substr(6, 50) === 'Apinan Singbut') {
              that.Apinan++
              that.progress1 = that.Apinan
            }
            if (progress.message.substr(6, 50) === "P'Tang Ratabhoom Boongate") {
              that.Ratabhoom++
              that.progress2 = that.Ratabhoom
            }
            if (progress.message.substr(6, 50) === 'Nitigan Nakjuatong') {
              that.Nitigan++
              that.progress3 = that.Nitigan
            }
            if (progress.message.substr(6, 50) === 'ไข่ต้ม รมควัน') {
              that.Nattapong++
              that.progress4 = that.Nattapong
            }
            if (progress.message.substr(6, 50) === 'Netiwit Keawthong') {
              that.Netiwit++
              that.progress5 = that.Netiwit
            }
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
