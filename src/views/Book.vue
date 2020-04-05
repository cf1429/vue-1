<template>
  <div>
    <table>
      <tr>
        <td>编号</td>
        <td>图书名称</td>
        <td>作者</td>
      </tr>
      <tr v-for="item in books" :key='item.id'>
        <td>{{item.id}}</td>
        <td>{{item.name}}</td>
        <td>{{item.author}}</td>
      </tr>
    </table>
  </div>

</template>

<script>
import axios from 'axios'

export default {
  name: 'Book',
  data () {
    return {
      msg: 'hello vue',
      books: [
        {
          id: 1,
          name: 'java基础',
          author: '张三'
        },
        {
          id: 2,
          name: 'veu基础',
          author: '里三'
        },
        {
          id: 3,
          name: 'css基础',
          author: '张柳'
        }
      ]
    }
  },
  created () {
    const _this = this
    axios.get('http://localhost:8070/api/book/findAll').then(function (res) {
      _this.books = res.data.data
      console.log(_this.books)
    })
  }
}
</script>

<style scoped>

</style>
