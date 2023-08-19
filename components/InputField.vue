<template>
  <input
    :name="name"
    :type="type"
    :class="[
      'w-full max-w-sm outline-none border-[1px] rounded-[4px] pl-4 py-2 placeholder:text-neutral-charcoal',
      bordered
        ? errorMessage
          ? 'border-danger focus:border-danger my-2'
          : 'border-neutral-divider focus:border-neutral-grey my-2'
        : 'border-none active:border-none focus:outline-none my-0',
    ]"
    :value="inputValue"
    @input="handleChange"
    @blur="handleBlur"
    :placeholder="placeholder"
  />
  <p v-show="errorMessage">{{ errorMessage }}</p>
</template>
<script setup lang="ts">
import { useField } from "vee-validate";

interface InputField {
  type: string;
  name: string;
  placeholder: string;
  defValue?: string;
  label?: string;
  bordered?: boolean;
}

const props = withDefaults(defineProps<InputField>(), {
  type: "text",
  value: "",
  placeholder: "Type your text here",
  bordered: true,
});

const name = toRef(props, "name");

const {
  value: inputValue,
  errorMessage,
  handleBlur,
  handleChange,
  meta,
} = useField<string>(name, undefined, {
  initialValue: props.defValue,
});
</script>
<style lang=""></style>
