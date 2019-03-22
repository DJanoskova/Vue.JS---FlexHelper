<template>
  <div id="app">
    <ElRow :gutter="40">
      <ElCol :sm="24" :lg="12" class="sm-mb-20">
        <ChildContainer :properties="properties" />
      </ElCol>
      <ElCol :sm="24" :lg="12">
        <div class="flex-picker">
          <p v-for="(option, key) in options" :key="option.name">
            <strong>{{ option.name }}:</strong>
            <br>
            <ElRadio v-model="properties[key]"
              :label="value"
              v-for="value in option.values"
              :key="value.name">
              {{ value }}
            </ElRadio>
          </p>
          <br>
          <a href="https://github.com/DJanoskova/Vue.JS---FlexHelper" target="_blank">
            https://github.com/DJanoskova/Vue.JS---FlexHelper
          </a>
        </div>
      </ElCol>
    </ElRow>
  </div>
</template>

<script>
import { Radio, Row, Col } from 'element-ui';

import ChildContainer from './components/ChildContainer';

export default {
  name: 'app',
  data() {
    return {
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
    ElRadio: Radio,
    ElRow: Row,
    ElCol: Col,
    ChildContainer
  }
}
</script>
