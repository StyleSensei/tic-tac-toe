<script setup lang="ts">
import Button from './Button.vue';
import { ref } from 'vue';

const emit = defineEmits<{
  (e: 'onSubmit', model: string): void;
}>();
const model = ref("")

const handleOnSubmit = () => {
emit('onSubmit', model.value.slice(0,1).toUpperCase() + model.value.slice(1))
model.value = ''
}
</script>

<template>
  <div class="start-screen-container">
    <div class="start-screen">
      <h1>Tic Tac Toe</h1>
      <form @submit.prevent = handleOnSubmit>
        <label for="user"> Username
          <input id="user" v-model="model"/>
        </label>
        <Button
        id="submit-user-name"
        title="submit"
        text="Add player"
        :disabled="model === '' || model.startsWith(' ')"
        ></Button>
      </form>
    </div>
  </div>

</template>

<style scoped lang="scss">
.start-screen-container{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.start-screen {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}
form{
  padding: 1.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #373737;
  border-radius: 20px;
}
input#user{
  padding: .5rem 1rem;
  border-radius: 20px;
  background-color: #1a1a1a;
  border: solid 1px rgb(124, 123, 123);
  &:focus, &:focus-visible{
    outline: 4px auto #646cff;;
  }
}
label {
  line-height: 1.1;
}
button{
border-radius: 20px;
}

</style>
