<template>
  <div>
    <cRangeInput :min="min" :max="max" :step="step" />
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
    min: 0,
    max: 100,
    step: .1,
  }),
}
</script>
