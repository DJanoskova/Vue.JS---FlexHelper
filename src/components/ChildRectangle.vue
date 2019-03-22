<template>
  <div class="flex-element text-center" :key="i" :style="style">
    <span>{{ displayedText }}</span>
  </div>
</template>

<script>
export default {
  props: {
    i: {
      type: Number,
      required: true
    },
    customStyle: {
      type: Object,
      required: true
    },
    customText: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    style() {
      const style = {};
      for (const key in this.customStyle) {
        if (this.customStyle.hasOwnProperty(key)) {
          const styleProperty = this.customStyle[key];
          if (styleProperty.used) style[key] = styleProperty.value
        }
      }
      return style
    },
    displayedText() {
      const i = this.i;
      if (!this.customText) return i;
      switch (i) {
        case 1:
          return 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus pretium neque non tristique tincidunt. Nulla et vestibulum urna. Nam finibus ex eu gravida tempus.';
        case 2:
          return 'Orci varius natoque penatibus.'
        case 3:
          return 'Morbi velit nunc, suscipit sed tincidunt sit amet, tincidunt non odio. Nullam suscipit vitae augue non vestibulum. Maecenas non faucibus dolor. Duis hendrerit libero nec mauris maximus aliquet eu vitae libero. Vestibulum nec felis et orci condimentum tempor sit amet vel enim.'
        case 4:
          return 'Donec tincidunt rhoncus erat, non ultricies diam varius quis. '
        default:
          return i
      }
    }
  }
}
</script>
