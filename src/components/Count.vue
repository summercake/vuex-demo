<template>
  <div>
    <h1>{{msg}}</h1>
    <hr>
    <!--<h2>{{$store.state.count}} - {{count}}</h2>-->
    <!--<h2>{{count}}</h2>-->
    // 使用Module
    <h2>{{$store.state.a.count}} - {{count}}</h2>
    <p>
      <b>同步</b>
      <button @click="$store.commit('add', 10)">+</button>
      <button @click="reduce">-</button>
    </p>
    <p>
      <b>异步</b>
      <button @click="addAction">+</button>
      <button @click="reduceAction">-</button>
    </p>
  </div>
</template>
<script>
  import store from '@/vuex/store'
  import { mapState, mapMutations, mapGetters, mapActions } from 'vuex'

  export default {
    data () {
      return {
        msg: 'Hello Vuex'
      }
    },
    // method 1
    //computed:{
    //  count(){
    //    return this.$store.state.count
    //  }
    //},
    // method 2
    //computed: mapState({
    //  count: state => state.count
    //}),
    // method 3
    //count(){
    //  return this.$state.getters.count;
    //}
    //computed:mapState(['count']),
    //methods:mapMutations(['add', 'reduce']),
    computed: {
      //...mapState(['count']),
      //...mapGetters(['count'])
      count(){
        return this.$store.state.a.count;
      }
    },
    methods: {
      ...mapMutations(['add', 'reduce']),
      ...mapActions(['addAction', 'reduceAction'])
    },
    store
  }
</script>
<style scoped>
</style>
