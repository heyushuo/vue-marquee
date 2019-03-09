<template>
  <div>
    <PaoMaDeng :delay="0.5" :speed="100" :content="arr">
      <span v-for="(item, index) in arr" :key="index">{{item}}</span>
    </PaoMaDeng>
  </div>
</template>

<script>
  import PaoMaDeng from 'heyushuo-marquee';
  export default {
    components: {
      PaoMaDeng
    },
    name: 'HelloWorld',
    mounted() {
      this.arr = ['手机用户:151****013获得二等奖', "科比:获得一个篮球", "网友:获得现金5元"]
    },
    data() {
      return {
        arr: []
      }
    },
    computed: {},
  }
</script>
<style scoped>
  span {
    font-size: 12px;
    margin-right: 20px;
  }
</style>