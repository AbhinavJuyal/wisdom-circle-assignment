<template>
  <div
    class="flex items-center rounded-[4px] border-[1px] border-neutral-divider active:outline-neutral-grey focus:outline-neutral-grey"
  >
    <InputField
      :placeholder="placeholder"
      :name="name"
      :type="showPassword ? 'text' : 'password'"
      :bordered="false"
    />
    <button class="pr-4 py-2" @click="toggle" type="button">
      <img v-show="showPassword" src="~/assets/Hide.svg" alt="hide" />
      <img v-show="!showPassword" src="~/assets/Show.svg" alt="show" />
    </button>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";

interface PasswordField {
  name: string;
  placeholder: string;
}

const { name, placeholder } = withDefaults(defineProps<PasswordField>(), {
  name: "",
  placeholder: "Type your text here",
});

const showPassword = ref(false);
const toggle = () => (showPassword.value = !showPassword.value);
</script>
<style lang=""></style>
