<template>
  <div id="app">
    <ElRow :gutter="40">
      <ElCol :sm="24" :lg="12" class="sm-mb-20">
        <ChildContainer :properties="properties" />
      </ElCol>
      <ElCol :sm="24" :lg="12">
        <div class="flex-picker">
          <p v-for="(optionValues, name) in options" :key="name">
            <strong>{{ name }}:</strong>
            <br>
            <ElRadio v-model="properties[name]"
              v-for="value in optionValues"
              :label="value"
              :key="value">
              {{ value }}
            </ElRadio>
          </p>
          <br>
        </div>
        <pre>{{ properties }}</pre>
      </ElCol>
    </ElRow>

    <div class="footer">
      <a href="https://github.com/DJanoskova/Vue.JS---FlexHelper" target="_blank">
        https://github.com/DJanoskova/Vue.JS---FlexHelper
      </a>
    </div>
  </div>
</template>

<script>
import { Radio, Row, Col } from 'element-ui';

import { containerOptions } from './const';

import ChildContainer from './components/ChildContainer';

export default {
  name: 'app',
  data() {
    return {
      properties: {
        display: 'flex',
        'flex-direction': 'row',
        'justify-content': 'flex-start',
        'align-items': 'flex-start'
      },
      options: containerOptions
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
