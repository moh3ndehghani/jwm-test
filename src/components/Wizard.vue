<template>

  <div class="wizard">
    <div class="wizard-header">
      <span v-for="(item, index) in props.headerItems" :key="index"
        :class="{ 'opacity-30': props.modelValue != index + 1 }">{{
        item }}</span>
    </div>
    <div class="wizard-body">

    </div>
    <div class="wizard-footer">
      <button class="btn" :class="{ 'btn-disable': disablePrevBtn }" id="btn-prev" @click="prev"
        :disabled="disablePrevBtn">Previous</button>
      <button class="btn" :class="{ 'btn-disable': disableNextBtn }" id="btn-next" @click="next"
        :disabled="disableNextBtn">Next</button>
    </div>
  </div>

</template>

<script setup>
import { computed } from "vue"


////////

const props = defineProps(["modelValue", "headerItems"])
const emit = defineEmits(["update:modelValue"])

////////

const disableNextBtn = computed(() => {
  return props.modelValue >= props.headerItems.length ? true : false
})

const disablePrevBtn = computed(() => {
  return props.modelValue <= 1 ? true : false
})

////////

function next() {
  if (props.modelValue < props.headerItems.length)
    emit("update:modelValue", props.modelValue + 1)
}

function prev() {
  if (props.modelValue > 1)
    emit("update:modelValue", props.modelValue - 1)
}

</script>
