<script>
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

import { onMounted, ref, computed, watch } from "vue";

export default {
  props: ["msg"],
  setup(props) {
    let count = ref(0);

    const getCount = async () => {
      count.value = await getData();
      // console.log(count.value);
    };
    onMounted(getCount);
    const onAddCount = () => {
      console.log("按钮点击了");
      count.value++;
    };
    watch(count, (newValue, oldValue) => {
      let result = "";
      for (let i = 0; i < count.value; i++) {
        result += name.value;
      }
      console.log(result);
      name.value = result;
    });

    let name = ref("胡雪");
    let helloText = computed(() => {
      return props.msg + " " + name.value;
    });

    return {
      count,
      onAddCount,
      name,
      helloText,
    };
  },
};
</script>

<template>
  {{ count }}
  <button @click="onAddCount">click</button>
  <h1>{{ name }}</h1>
  <h2>{{ helloText }}</h2>
</template>


<style scoped>
.h2 {
  color: red;
}
a {
  color: #42b983;
}
</style>
