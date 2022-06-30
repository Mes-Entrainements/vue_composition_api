<template>
  <div>
    <h1>{{ title }}</h1>

    <form @submit.prevent="send">
      <!-- <input type="text" v-model="model" /> -->
      <input type="text" v-model="essai" />
      <button>Envoyer</button>
    </form>

    <input :ref="test" type="text" />
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  props: ["essai"],
  setup(props) {
    let title = "Test";

    let model = ref("title");

    let essai = ref(null);

    model.value = "Hello world";

    const test = ref(null);

    function send() {
      console.log(essai.value);
    }

    return {
      title,
      model,
      send,
      test,
      essai
    };
  },
};
</script>

<style  scoped>
h1 {
  text-align: center;
  margin-top: 10px;
}
</style>