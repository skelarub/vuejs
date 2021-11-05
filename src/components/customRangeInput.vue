<template>
  <div>
    <input type="number" v-model="value" :min="min" :max="max" :step="step">
    <div class="slider-component">
      <div class="slidecontainer">
        <input
          ref="input"
          v-model="value"
          type="range"
          :min="min"
          :max="max"
          :step="step"
          class="slider"
          @input="onInput"
        >
        <div class="slider-preset-value">
          <div class="slider-preset-value-item" @click="setValue(25)">25%</div>
          <div class="slider-preset-value-item" @click="setValue(50)">50%</div>
          <div class="slider-preset-value-item" @click="setValue(75)">75%</div>
          <div class="slider-preset-value-item" @click="setValue(100)">100%</div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: "customRangeInput",
  props: {
    min: {
      type: Number,
      required: true
    },
    max: {
      type: Number,
      required: true
    },
    step: {
      type: Number,
      required: true
    }
  },
  data(){
    return {
      value: 0,
      currentValue: this.value,
    };
  },
  methods: {
    onInput() {
      this.$emit('input', parseInt(this.currentValue));
    },
    setValue(val) {
      this.value = val
    }
  }
};
</script>

<style  scoped lang="less">
@widthRangeSlider: 45%;
@heightRangeSlider: 3rem;
 
.slider-component .slidecontainer {
	width: @widthRangeSlider;
}

.slider-component .slidecontainer .slider {
	-webkit-appearance: none;
	appearance: none;
	width: 100%;
	height: @heightRangeSlider;
	border-radius: 25px;
	background: linear-gradient(to right, green, red);
	outline: none;
	opacity: 0.7;
	-webkit-transition: .2s;
	transition: opacity .2s;
}

.slider-component .slidecontainer .slider:hover {
	opacity: 1;
}

.slider-component .slidecontainer .slider::-webkit-slider-thumb {
	-webkit-appearance: none;
	appearance: none;
	width: 25px;
	height: 25px;
	background: #FFFFFF;
	cursor: pointer;
	border-radius: 50%;
}

.slider-component .slidecontainer .slider::-moz-range-thumb {
	width: 25px;
	height: 25px;
	background: #FFFFFF;
	cursor: pointer;
	border-radius: 50%;
}

.slider-preset-value {
  display: flex;
  justify-content: center;
}

.slider-preset-value-item {
  padding: 1rem;
  border-radius: 50%;
  cursor: pointer;
}

</style>