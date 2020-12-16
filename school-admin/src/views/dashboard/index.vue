<template>
  <div class="dashboard-container">
    <div class="dashboard-text">学校个数：{{schoolCount}}</div>
    <div class="dashboard-text">学生个数：{{studentCount}}</div>
    <div class="dashboard-text">班级个数：{{classsCount}}</div>
    <div class="dashboard-text">老师个数：{{teacherCount}}</div>
    <div class="dashboard-text">学院个数：{{academyCount}}</div>
  </div>
</template>

<script>
  import { mapGetters } from 'vuex'

  export default {
    name: 'Dashboard',
    computed: {
      ...mapGetters([
        'name'
      ])
    },

    data() {
      return {
        studentCount:'',
        schoolCount:'',
        teacherCount:'',
        academyCount:'',
        classsCount:''
      }
    },

    mounted(){
      this.$http.post('/api/school/find', this.user).then(res => {
        console.log('res:', res)
        console.log('res:'.length)
        this.schoolCount = res.length
      })
      this.$http.post('/api/student/find', this.user).then(res => {
        console.log('res:', res)
        console.log('res:'.length)
        this.studentCount = res.length
      })
      this.$http.post('/api/classs/find', this.user).then(res => {
        console.log('res:', res)
        console.log('res:'.length)
        this.classsCount = res.length
      })
      this.$http.post('/api/teacher/find', this.user).then(res => {
        console.log('res:', res)
        console.log('res:'.length)
        this.teacherCount = res.length
      })
      this.$http.post('/api/academy/find', this.user).then(res => {
        console.log('res:', res)
        console.log('res:'.length)
        this.academyCount = res.length
      })
    }



  }

</script>

<style lang="scss" scoped>
  .dashboard {
    &-container {
      margin: 30px;
    }
    &-text {
      font-size: 30px;
      line-height: 46px;
    }
  }
</style>
