<template>
  <div class="w-full h-full flex justify-center items-center">
    <div>
      <img class="mx-auto mb-10" src="~/assets/Logo.svg" alt="Logo" />
      <h1 class="font-bold text-xl">Sign In to WisdomCircle</h1>
      <div class="text-sm">
        <span class="font-normal"> Don't have an account? </span>
        <span class="font-semibold text-royal-blue">Sign up</span>
      </div>
      <Form :validation-schema="loginSchema">
        <InputField
          name="emailOrPhone"
          type="text"
          def-value=""
          placeholder="Email Id or Mobile Number "
        />
        <PasswordField name="password" placeholder="Password" />
      </Form>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { Form } from "vee-validate";
import * as yup from "yup";

const loginSchema = yup.object({
  emailOrPhone: yup
    .string()
    .required("Please enter a email or phone number")
    .test(
      "emailOrPhone",
      "Please enter a valid email address",
      (value, context) => {
        console.log(value, context);
        return false;
      }
    )
    .test("emailOrPhone", "Please enter a valid mobile number", (value) => {
      console.log(value);
      return false;
    }),
  password: yup.string().required("Please enter a password."),
});
</script>
<style lang=""></style>
