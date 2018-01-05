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
                        <font color="#000000" size="2">Date : {{ tododmy }}</font>
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
                  <div v-if = "progress.status == 'กำลังทำ'" class="alert alert-warning" role="alert">
                    <div class="message-header">
                      <div v-show = "progress.date == datetime">
                        <font color="#000000" size="3">Status : </font><font color="green"><b>On time</b></font>
                      </div>
                      <div v-show = "progress.date != datetime">
                        <font color="#000000" size="3">Status : </font><font color="red"><b>Delay</b></font>
                      </div>
                    </div>
                    <div class="message-body" style="padding-top: 10px;">
                      <font color="#000000" size="2">&nbsp;&nbsp;&nbsp;{{ progress.msg }}</font>
                      <div style="padding-top:10px">
                        <div v-show = "progress.date == datetime">
                          <font color="#000000" size="2">Date Start: {{ progress.dmy }}</font>
                        </div>
                        <div v-show = "progress.date != datetime">
                          <font color="#000000" size="2">Date Start: {{ progress.dmy }}</font>
                        </div>
                        <font color="#000000" size="2">Name : {{ progress.name }}</font><br>
                        <font color="#000000" size="2">Position : Personnel</font>
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
                      <div v-if = "dodone.dash == 'On time'">
                        <font color="#000000" size="3">Status : </font><font color="green"><b>{{ dodone.dash }}</b></font>
                      </div>
                      <div v-if = "dodone.dash == 'Delay'">
                        <font color="#000000" size="3">Status : </font><font color="red"><b>{{ dodone.dash }}</b></font>
                      </div>
                    </div>
                    <div class="message-body" style="padding-top: 10px;">
                      <font color="#000000" size="2">&nbsp;&nbsp;&nbsp;{{ dodone.msg }}</font>
                      <div style="padding-top:10px">
                        <font color="#000000" size="2">Name : {{ dodone.name }}</font>
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
      feedid: 0
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
  // Fetches posts when the component is created.
  created () {
    let that = this
    axios.get('https://graph.facebook.com/138501810233037?fields=feed&access_token=EAACEdEose0cBACi9L3PWdmdduOzZBezyipZCJMreF7s2Wld8SQc5cjjxFOX7dx8xrNy3HZAjyp6F96glZBEgQDjB74I4XhruPlxFoYv7iwD0qaqUC2z0ZBqvX5DY0pivrEXpEG4inHl0oB0w8afyZCeG1wj673lMNcFf3in3A9icKi1UHmV17gbk2HfYnIMfIZD')
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
            dash: '',
            tododmy: ''
          }
          // console.log(comment.id)
          that.todo.push(newmessage)
          that.progress.push(newmessage)
          that.done.push(newmessage)
          that.count++
          that.tododmy = message.updated_time.substr(0, 10)
          console.log(that.tododmy)
          // that.todo.push(message.message.substr(6))
          // that.todo.push(message.id)
          // that.feedid = message.id
          // console.log(that.feedid)
        }
      })
    })
    axios.get('https://graph.facebook.com/138501810233037?fields=feed{comments}&access_token=EAACEdEose0cBACi9L3PWdmdduOzZBezyipZCJMreF7s2Wld8SQc5cjjxFOX7dx8xrNy3HZAjyp6F96glZBEgQDjB74I4XhruPlxFoYv7iwD0qaqUC2z0ZBqvX5DY0pivrEXpEG4inHl0oB0w8afyZCeG1wj673lMNcFf3in3A9icKi1UHmV17gbk2HfYnIMfIZD')
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
            that.sumprogress = that.progresscount - that.donecount
            that.todo.push(result)
            // console.log(that.todo)
            // console.log(that.datetime)
            // console.log(that.test.id)
          }
          // End comment start
          if (progress.message === '#end') {
            let result = that.todo.find(item => item.id === comment.id)
            result.status = 'ทำเสร็จแล้ว'
            result.ondelay = progress.created_time.substr(8, 2)
            if (result.date === result.ondelay) {
              result.dash = 'On time'
            }
            else {
              result.dash = 'Delay'
            }
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
