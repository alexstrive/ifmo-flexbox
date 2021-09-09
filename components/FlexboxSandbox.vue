<script setup lang="ts">
import { ref, defineProps, reactive } from 'vue';

let props = defineProps({
  flexboxPropName: String,
  wrap: {
    type: Boolean,
    default: false,
  },
  elementsNumber: {
    type: Number,
    default: 5,
  },
});

const { flexboxPropName, wrap, elementsNumber } = props;

const middleElementIndex = Math.ceil(elementsNumber / 2);

const flexboxProps = {
  'align-self': [
    {
      value: 'flex-start',
      styleElement: { alignSelf: 'flex-start' },
      allElementsStyle: { height: 'auto' },
      styleContainer: {},
    },
    {
      value: 'center',
      styleElement: { alignSelf: 'center' },
      allElementsStyle: { height: 'auto' },
      styleContainer: {},
    },
    {
      value: 'flex-end',
      styleElement: { alignSelf: 'flex-end' },
      allElementsStyle: { height: 'auto' },
      styleContainer: {},
    },
    {
      value: 'stretch',
      styleElement: { alignSelf: 'stretch' },
      allElementsStyle: { height: 'auto' },
      styleContainer: {},
    },
  ],
  'align-content': [
    {
      value: 'start',
      styleContainer: { alignContent: 'start' },
    },
    {
      value: 'center',
      styleContainer: { alignContent: 'center' },
    },
    {
      value: 'space-between',
      allElementsStyle: { flexBasis: '200px' },
      styleContainer: { alignContent: 'space-between' },
    },
    {
      value: 'space-around',
      allElementsStyle: { flexBasis: '200px' },
      styleContainer: { alignContent: 'space-around' },
    },
  ],
  'flex-shrink': [
    {
      value: 'flex-shrink: 0',
      styleElement: { flexShrink: 0 },
      allElementsStyle: { flexBasis: '400px' },
    },
    {
      value: 'flex-shrink: 1',
      styleElement: { flexShrink: 1 },
      allElementsStyle: { flexBasis: '400px' },
    },
    {
      value: 'flex-shrink: 2',
      styleElement: { flexShrink: 2 },
      allElementsStyle: { flexBasis: '400px' },
    },
  ],
  'flex-basis': [
    { value: 'flex-basis: auto', styleElement: { flexBasis: 'auto' } },
    { value: 'flex-basis: 0', styleElement: { flexBasis: 0 } },
    { value: 'flex-basis: 200px', styleElement: { flexBasis: '200px' } },
  ],
};

const selectedFlexboxProp = flexboxProps[flexboxPropName];
let currentPropertyValue = ref(selectedFlexboxProp[0]);
</script>

<style>
.interactive-content {
  padding: 15px;
  background-color: rgb(245, 245, 245);
  border-radius: 10px;
}

.parent {
  display: flex;
  height: 200px;
}

.child {
  flex-grow: 1;
  padding: 10px 20px;
  margin-right: 10px;
  color: #f83da4;
  height: 50px;

  border: 1px solid black;
  border-style: solid;
  border-color: #f83da4;
  border-radius: 4px;
}

.styleElement {
  background-color: #f83da4;
  color: white;
}

.control {
  font-family: monospace;
  display: flex;
  margin-bottom: 20px;
}

.control button {
  border-width: 4px;
  border-style: dashed;
  padding: 10px;
  border-radius: 2px;
  margin-right: 20px;
}

.control button:hover {
  background: #f83da470;
}

.buttonActive {
  border-color: #f83da4;
}
</style>

<template>
  <div class="wrapper">
    <div class="interactive-content">
      <div class="control">
        <button
          v-for="flexboxProp in selectedFlexboxProp"
          @click="currentPropertyValue = flexboxProp"
          :class="{
            buttonActive: flexboxProp.value === currentPropertyValue.value,
          }"
        >
          {{ flexboxProp.value }}
        </button>
      </div>
      <div
        class="parent"
        :style="[
          { flexWrap: wrap ? 'wrap' : 'nowrap' },
          currentPropertyValue.styleContainer,
        ]"
      >
        <div
          v-for="index in elementsNumber"
          :class="[
            'child',
            {
              styleElement:
                index === middleElementIndex &&
                currentPropertyValue.styleElement,
            },
          ]"
          :style="[
            currentPropertyValue.allElementsStyle,
            index === middleElementIndex && currentPropertyValue.styleElement,
          ]"
        >
          Item {{ index }}
        </div>
      </div>
    </div>
    <div :style="{ padding: '15px' }">
      {{ currentPropertyValue.description }}
    </div>
  </div>
</template>
