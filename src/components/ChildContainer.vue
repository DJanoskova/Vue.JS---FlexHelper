<template>
  <div>
    <div class="flex-container" :style="properties">
      <ChildRectangle v-for="i in count"
        :key="i"
        :i="i"
        :customStyle="childStyle"
        :customText="childText" />
    </div>

    <ElCheckbox v-model="style.used" v-for="(style,key) in childStyle" :key="key">
      {{ key }}: {{ style.value }}
    </ElCheckbox>
    <hr />
    <ElCheckbox v-model="childText">
      Display random text
    </ElCheckbox>
  </div>
</template>

<script>
import { Checkbox } from 'element-ui';

import ChildRectangle from './ChildRectangle'

export default {
  props: {
    properties: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      count: 4,
      childStyle: {
        width: {
          value: '50px',
          used: true
        },
        height: {
          value: '50px',
          used: true
        },
        flex: {
          value: 1,
          used: false
        }
      },
      childText: false
    }
  },
  components: {
    ChildRectangle,
    ElCheckbox: Checkbox
  }
}
</script>