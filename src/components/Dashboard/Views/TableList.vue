<template>
  <div class="content">
    <div class="row">
      <!-- Table Header -->
      <div class="col-md-12">
        <table class="table">
          <thead class="thead-light">
            <tr>
              <th scope="col" style="padding-top:15px; padding-bottom:15px;"><center><font size="3">To Do</font></center></th>
              <th scope="col" style="padding-top:15px; padding-bottom:15px;"><center><font size="3">In Progress</font></center></th>
              <th scope="col" style="padding-top:15px; padding-bottom:15px;"><center><font size="3">Done</font></center></th>
            </tr>
          </thead>
        </table>
      </div>
      <!-- End Table Header -->

      <!-- To Do -->
      <div class="col-md-4">
        <table class="table">
          <tbody>
            <tr>
              <td>
                <div v-for = "message in todo">
                  <div v-if = "message.status == 'ยังไม่ได้ทำ'" class="alert alert-primary" role="alert">
                    <div class="message-header">
                      <font color="#000000" size="3">Status : </font><font color="#EEBA34" size="3"><b>Waiting</b></font>
                    </div>
                    <div class="message-body" style="padding-top: 10px;">
                      <font color="#000000" size="2">&nbsp;&nbsp;&nbsp;{{ message.msg }}</font>
                      <div style="padding-top:10px">
                        <font color="#000000" size="2">Date : {{ tododmy }}</font><br>
                        <font color="#000000" size="2">Time : {{ todotime }}</font>
                      </div>
                    </div>
                  </div>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <!-- End To Do -->

      <!-- In Progress -->
      <div class="col-md-4">
        <table class="table">
          <tbody>
            <tr>
              <td>
                <div v-for = "progress in progress">
                  <div class="">
                  </div>
                  <div v-if = "progress.status == 'กำลังทำ'" class="alert alert-warning" role="alert">
                    <div class="message-header">
                      <div v-show = "progress.dateendday >= datetime">
                        <font color="#000000" size="3">Status : </font><font color="green"><b>On time</b></font>
                      </div>
                      <div v-show = "progress.dateendday < datetime">
                        <font color="#000000" size="3">Status : </font><font color="red"><b>Delay</b></font>
                      </div>
                    </div>
                    <div class="message-body" style="padding-top: 10px;">
                      <font color="#000000" size="2">&nbsp;&nbsp;&nbsp;{{ progress.msg }}</font>
                      <div style="padding-top:10px">
                        <div v-show = "progress.date == datetime">
                          <font color="#000000" size="2">Job Start : {{ progress.dmy }}</font><br>
                          <font color="#000000" size="2">Deadline : {{ progress.dateend }}</font>
                        </div>
                        <div v-show = "progress.date != datetime">
                          <font color="#000000" size="2">Job Start : {{ progress.dmy }}</font><br>
                          <font color="#000000" size="2">Deadline : {{ progress.dateend }}</font>
                        </div>
                        <font color="#000000" size="2">{{ progress.name }}</font><br>
                        <div v-if = "progress.name == 'Apinan Singbut'">
                          <font color="#000000" size="2">Position : Programmer</font>
                        </div>
                        <div v-if = "progress.name == 'Nitigan Nakjuatong'">
                          <font color="#000000" size="2">Position : Testing</font>
                        </div>
                        <div v-if = "progress.name != 'Apinan Singbut' && progress.name != 'Nitigan Nakjuatong'">
                          <font color="#000000" size="2">Position : UI / UX</font>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <!-- End In Progress -->

      <!-- Done -->
      <div class="col-md-4">
        <table class="table">
          <tbody>
            <tr>
              <td>
                <div v-for = "dodone in done">
                  <div v-if = "dodone.status == 'ทำเสร็จแล้ว'" class="alert alert-success" role="alert">
                    <div class="message-header">
                      <div v-if = "dodone.dateendday >= dodone.ondelayday">
                        <font color="#000000" size="3">Status : </font><font color="green"><b>On time</b></font>
                      </div>
                      <div v-if = "dodone.dateendday < dodone.ondelayday">
                        <font color="#000000" size="3">Status : </font><font color="red"><b>Delay</b></font>
                      </div>
                    </div>
                    <div class="message-body" style="padding-top: 10px;">
                      <font color="#000000" size="2">&nbsp;&nbsp;&nbsp;{{ dodone.msg }}</font>
                      <br><br>
                      <div v-show = "dodone.date == datetime">
                        <font color="#000000" size="2">Job Start : {{ dodone.dmy }}</font><br>
                        <font color="#000000" size="2">Deadline : {{ dodone.dateend }}</font><br>
                        <font color="#000000" size="2">Job End : {{ dodone.ondelay }}</font>
                      </div>
                      <div v-show = "dodone.date != datetime">
                        <font color="#000000" size="2">Job Start : {{ dodone.dmy }}</font><br>
                        <font color="#000000" size="2">Deadline : {{ dodone.dateend }}</font><br>
                        <font color="#000000" size="2">Job End : {{ dodone.ondelay }}</font>
                      </div>
                      <div style="padding-top:10px">
                        <font color="#000000" size="2">{{ dodone.name }}</font>
                      </div>
                    </div>
                  </div>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <!-- End Done -->
    </div>
  </div>
</template>
<script>
import axios from 'axios';

export default {
  components: {

  },

  data() {
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
      number: 0
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
    if (that.datetime === '06') {
      that.datetime = 6
    }
    setInterval(() => {
      // https://github.com/vuejs/vue/issues/2873
      // Array.prototype.$set/$remove deprecated (use Vue.set or Array.prototype.splice instead)
      this.data.forEach((item, i) => {
        this.data.splice(i, 1, Math.ceil(Math.random() * 1000))
      })
    }, 1024)
  },
  // Fetches posts when the component is created.
  created () {
    let that = this
    axios.get('https://graph.facebook.com/138501810233037?fields=feed&access_token=EAACEdEose0cBAPQWdGbOKWC5Qzr4zpdQiQYoUMxYiqNxiSjou2ZAG6jqLlqY7LPUZB2rszlHSdJMDZCCpDT9JwQZBMh8odU6xq3NQhoYP2X88YnYxwb2mnWGk6htEEMOD0jqNQEWPjY1Oh7C9wr4fWkgGIlmS8ljCZBIqBENEEsD5Q23C85ZCVLjZCnCliowVEZD')
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
          // console.log(that.todo)
          // that.todo.push(message.message.substr(6))
          // that.todo.push(message.id)
          // that.feedid = message.id
          // console.log(that.feedid)
        }
      })
    })
    axios.get('https://graph.facebook.com/138501810233037?fields=feed{comments}&access_token=EAACEdEose0cBAPQWdGbOKWC5Qzr4zpdQiQYoUMxYiqNxiSjou2ZAG6jqLlqY7LPUZB2rszlHSdJMDZCCpDT9JwQZBMh8odU6xq3NQhoYP2X88YnYxwb2mnWGk6htEEMOD0jqNQEWPjY1Oh7C9wr4fWkgGIlmS8ljCZBIqBENEEsD5Q23C85ZCVLjZCnCliowVEZD')
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
          let result = that.todo.find(item => item.id === comment.id)
          // console.log(result)
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
            that.sumprogress = that.progresscount - that.donecount
            that.todo.push(result)
            // console.log(that.datetime)
            // console.log(that.test.id)
          }
          if (progress.message.substr(0, 5) === '#name') {
            if (progress.message.substr(6, 20) === '') {
              result.name = result.name + ''
            }
            else result.name = result.name + 'Name : ' + progress.message.substr(6, 20)
          }
          // console.log(progress.message)
          if (progress.message.substr(0, 5) === '#date') {
            if (progress.message.substr(6, 20) === '') {
              result.dateend = ''
            }
            else {
              result.dateend = progress.message.substr(6, 10)
              result.dateendday = progress.message.substr(14, 2)
              if (result.dateendday === '10') {
                result.dateendday = 10
              }
              console.log(result.dateendday)
              that.dateend = result.dateend
            }
          }
          // End comment start
          if (progress.message === '#end' && result.status === 'กำลังทำ') {
            // let result = that.todo.find(item => item.id === comment.id)
            result.status = 'ทำเสร็จแล้ว'
            result.ondelay = progress.created_time.substr(0, 10)
            result.ondelayday = progress.created_time.substr(8, 2)
            if (result.ondelayday === '06') {
              result.ondelayday = 6
            }
            // console.log(that.dateend)
            console.log(result.dmy);
            that.donecount++
            that.todo.push(result)

            // console.log(that.todo)s
            // console.log(that.test.id)sssหsss
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
  .tbl-content{
    height:435px;
    overflow-x:auto;
    margin-top: 0px;
    border: 1px solid rgba(255,255,255,0.3);
  }

  /* for custom scrollbar for webkit browser*/
  ::-webkit-scrollbar {
    width: 6px;
  }
  ::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
  }
  ::-webkit-scrollbar-thumb {
    -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
  }
</style>
