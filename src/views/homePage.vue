<template>
  <div>
    <cRangeInput :startValue="startValue" :min="min" :max="max" :step="step" />
  </div>
</template>

<script>
import cRangeInput from '../components/customRangeInput.vue'

export default {
  name: 'homePage',
  components: {
    cRangeInput,
  },
  data: () => ({
    startValue: 15.5,
    min: 0,
    max: 100,
    step: .1,
  }),
}
</script>
