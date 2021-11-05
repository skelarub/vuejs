<template>
  <div>
    <span class="slider-value">{{ value }} %</span>
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
    startValue: {
      type: Number,
      default: 0,
      required: true
    },
    min: {
      type: Number,
      default: 0,
      required: true
    },
    max: {
      type: Number,
      default: 100,
      required: true
    },
    step: {
      type: Number,
      default: .1,
      required: true
    }
  },
  data: function () {
    return {
      value: this.startValue
    }
  },
  methods: {
    onInput() {
      this.$emit('input', parseInt(this.value));
    },
    setValue(val) {
      this.value = val
    }
  }
};
</script>

<style  scoped lang="less">
@widthRangeSlider: 100%;
@heightRangeSlider: 3rem;
@mainColor: #FFFFFF;

div {
  background: #21273F;
}

.slider-value {
  display: block;
  padding: 1rem 1.5rem;
  color: #79819C;
}

.slider-component .slidecontainer {
	width: @widthRangeSlider;
}

.slider-component .slidecontainer .slider {
	-webkit-appearance: none;
	appearance: none;
	width: 100%;
	height: @heightRangeSlider;
	border-radius: 25px;
	background: linear-gradient(to right, #03DFC9, #FF6960);
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
	background: @mainColor;
	cursor: pointer;
	border-radius: 50%;
}

.slider-component .slidecontainer .slider::-moz-range-thumb {
	width: 25px;
	height: 25px;
	background: @mainColor;
	cursor: pointer;
	border-radius: 50%;
}

.slider-preset-value {
  display: flex;
  justify-content: center;
  padding: 1rem;
}

.slider-preset-value-item {
  padding: 1rem;
  border-radius: 25%;
  cursor: pointer;
  background: #4F608F;
  color: @mainColor;
  margin-right: 1rem;
}

</style>