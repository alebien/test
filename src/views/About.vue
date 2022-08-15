<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>{{ "name: " + people.name }}</p>
    <p>{{ "age: " + people.age }}</p>
    <p>{{ "hobby: " + people.hobby }}</p>
    <p>{{ "height: " + people.height }}</p>
    <p>{{ "weight: " + people.weight }}</p>
    <h2>{{ "响应式：" + name }}</h2>
    <h2>{{ "响应式：" + age }}</h2>
    <h2>{{ "非响应：" + height }}</h2>
    <h2>{{ "非响应：" + weight }}</h2>
  </div>
</template>

<script>
import { reactive, ref, toRefs, readonly } from "vue";

export default {
  name: "About",
  setup() {
    let count = ref(0);
    // console.log(count);
    // console.log(count.value);
    // const aa = reactive({
    //     count,
    //     cc: 10,
    // })
    // count = ref(1);
    // console.log(aa.count);
    // console.log(count);
    // aa.cc = 20;

    const people = reactive({
      name: "人类",
      age: 500,
      hobby: "eatPeople",
      height: 700,
      weight: 750,
    });
    let { name, age } = toRefs(people);
    let { height, weight } = people;

    const original = reactive({ count: 0 });
    console.log("original", original);
    const copy = readonly(original);
    console.log("copy", copy);
    // original.count++;
    console.log(original);
    copy.count++;
    console.log(copy);

    return {
      count,
      // bb:{count},
      // aa,
      people,
      name,
      age,
      height,
      weight,
    };
  },
  mounted() {
    // console.log(this.bb.count.value);
    // console.log(this.aa.cc);
  },
};
</script>
