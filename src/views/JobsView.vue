<template>
  <ol class="list"> <!-- 4) 사용한다. -->
    <li v-for="item in list" v-bind:key="item.id">
      <b>{{ item.time_ago}}</b>
      <span> by {{ item.user }}</span><br/>
      <a v-bind:href="item.url">{{ item.title }}<i>({{ item.comments_count }})</i></a>
    </li>
  </ol>
</template>

<script>
import ListItem from '../components/ListItem.vue';// 1) axios기능을 import해서 가져온다.

export default {
  components: { ListItem },

  computed: {
    list() {
        return this.$store.state.list;
    }
  },

  // created() {
  //   axios
  //     .get(`https://api.hnpwa.com/v0/jobs/1.json`) // 2) 데이터를 요청하고
  //     .then( res => {this.list = res.data}) // 3) 받아와서 list에 넣는다.
  // }

    created() {
    this.$store.dispatch('FETCH_LIST', 'jobs')
  },
}

</script>

<style> 
.list li {padding-left:10px; list-style-type: none}
.list li + li {margin-top:20px}
.list li > a {text-decoration: none; font-size:22px}
.list li > b {font-style: normal; font-size:12px; color:#999}
.list li span {font-style: normal; font-weight:700; font-size:12px; color:#999;}
.list li i {font-style: normal; font-size:12px; color:cornflowerblue}
</style>