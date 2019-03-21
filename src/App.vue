<template>
  <div id="app">
    <div>
      <div class="flex-container" :style="properties" ref="container">
        <div v-for="i in count" class="flex-element" :key="i"></div>
      </div>
    </div>
    <div class="flex-picker">
      <p v-for="(option, key) in options" :key="option.name">
        <strong>{{ option.name }}:</strong>
        <br>
        <ElRadio v-model="properties[key]" :label="value" v-for="value in option.values" :key="value.name">
          {{ value }}
        </ElRadio>
      </p>
    </div>
  </div>
</template>

<script>
import { Radio } from 'element-ui';

export default {
  name: 'app',
  data() {
    return {
      count: 4,
      properties: {
        display: 'flex',
        flexDirection: 'row',
        justifyContent: 'flex-start',
        alignItems: 'flex-start'
      },
      options: {
        flexDirection: {
          name: 'flex-direction',
          values: ['row', 'column']
        },
        justifyContent: {
          name: 'justify-content',
          values: ['flex-start', 'flex-end', 'center', 'space-between', 'space-around', 'space-evenly']
        },
        alignItems: {
          name: 'align-items',
          values: ['flex-start', 'flex-end', 'center', 'baseline', 'stretch']
        }
      }
    }
  },
  components: {
    ElRadio: Radio
  }
}
</script>
