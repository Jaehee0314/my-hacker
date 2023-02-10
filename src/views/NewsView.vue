<template>
   
    <list-item :listData="list"></list-item>

</template>


<script>

import ListItem from '../components/ListItem.vue';

// 1) axios기능을 import해서 가져온다.

export default {
  components: { ListItem },

  computed: {
    list() {
        return this.$store.state.list;
    }
  },
  created() {
    this.$store.dispatch('FETCH_LIST', 'news')
  },
}
</script>

<style> 

</style>