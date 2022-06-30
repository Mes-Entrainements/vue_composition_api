<template>
  <div class="home">
    <form @submit.prevent="send">
      <div>
        <h2>Reactive from setup in api composition</h2>

        <input v-model="state.title" required type="text" />

        <input v-model="state.step" required type="text" />
      </div>

      <button>Envoyer</button>
    </form>
  </div>
</template>

<script>
import { reactive, watch } from "vue";
import { useRouter, useRoute} from 'vue-router';
export default {
  setup() {
    const state = reactive({
      title: null,
      step: null,
    });

    const route = useRoute();
    
    console.log(route.path);


    watch(
      () => state.title,
      (newValue, oldValue) => {
        console.log(oldValue, newValue);
      }
    );

    function send() {
      console.log(state);
    }

    return {
      state,
      send,
    };
  },
};
</script>

<style scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.home div {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 200px;
}

.home div input {
  margin-top: 20px;
  border-radius: 10px;
  padding: 10px;
}

button {
  margin-top: 10px;
  outline: none;
  border: none;
  padding: 10px;
  border-radius: 10px;
}
</style>
