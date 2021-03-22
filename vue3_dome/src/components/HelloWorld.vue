<template>
  <div>{{ readersNumber }} {{ book.title }}</div>
</template>

<script>
import { ref, reactive,readonly ,watchEffect,isReactive } from "vue";

export default {
  setup() {
    // ref 接受一个内部值并返回一个响应式且可变的 ref 对象。ref 对象具有指向内部值的单个 property.value
    const readersNumber = ref("ssdsa"); //  怎么指定数据类型

   
    readersNumber.value = "wzy";
    // console.log(readersNumber);
    ///////
    const book = reactive({ title: "wzy" });
    // console.log(book);
    // isReactiven 用于判断改变量是否是通过reactive 创建的响应式数据
    const kobe = 'bryant'
    console.log(isReactive(kobe))

    // 利用reactive 穿件响应式数据
    const original = reactive({ count: 0 });
    // 将相应式数据利用readonly 设置为只读数据
    const copy = readonly(original);
    // 原来的监听函数  研究的不是很透彻
    watchEffect(() => {
      // 适用于响应性追踪
      console.log(copy.count);
    });

    // 变更original 会触发侦听器依赖副本
    original.count++;

    // 变更副本将失败并导致警告
    copy.count++; // 警告!
    return {
      readersNumber,
      book,
    };
  },
};
</script>

<style scoped>
a {
  color: #42b983;
}
</style>