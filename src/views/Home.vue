<template>
  <div class="w-1/2 mx-auto ">
    <Wizard v-model="state.step" :headerItems="state.headerItems" />
  </div>
</template>

<script setup>
import Wizard from "@/components/Wizard.vue"
import { reactive } from "vue"

////////

const state = reactive({
  headerItems: [
    "username",
    "email",
    "review"
  ],
  step: 1
})

</script>