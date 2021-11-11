<template>
  <h1>{{ msg }}</h1>
  <h2 class="h2">{{ helloText }}</h2>

  <button type="button" @click="count++">count is: {{ count }}</button>

  <br />
  <input type="text" v-model="msg" />
</template>

<script>
// import { ref } from "vue";

// defineProps({
//   msg: String,
// });

// const count = ref(0);

function getData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(Math.floor(Math.random() * 100));
    }, 2000);
  });
}

export default {
  props: ["msg"],
  data() {
    return {
      count: 0,
      name: "胡雪",
    };
  },
  methods: {
    //发请求获取数据
    async getCount() {
      this.count = await getData();
    },
    onAddCount() {
      this.count++;
    },
  },
  computed: {
    helloText() {
      return this.msg + " " + this.name;
    },
  },
  mounted() {
    this.getCount();
  },
};
</script>


<style scoped>
.h2{
  color:red;
}
a {
  color: #42b983;
}
</style>
