<!--
* Button组件的描述部分，描述补充，介绍部分
* @title 组件Title
* @design 统一button的表现
* @expect
  1. 测试
  2. 看看
-->
<template>
  <div class="na">
    这是一个btn
    <header class="header">
      <!--
      * 这是一个title slot
      * @bind `{ size, type }`大小和类型
      -->
      <slot name="title" v-bind="{ size, type }"></slot>
    </header>

    <!-- 这是默认的slot -->
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'button',
  model: {
    prop: 'value',
    event: 'change',
  },
  props: {
    /**
     * 尺寸
     * @optional mini|small|medium|large
     */
    size: {
      type: String,
      default: 'medium',
    },
    /**
     * 禁用状态
     */
    disabled: Boolean
  },
  methods: {
    /**
     * 点击事件
     * @param {Event} event - description event.
     */
    click(event) {
      let obj = { key: 'k', value: 'v' }
      /**
       * 变化事件
       * @arg {string} value - The input value
       * @arg {object} obj - `{ key: 'k', value: 'v'}`
       */
      this.$emit('onChange', this.value, obj)
    },
    /**
     * @private
     * 这是一个私有方法
     */
    demo() {
      /**
       * @ignore
       * 在文档中忽略当前事件
       */
      this.$emit('change', '111')
    },
  },
}
</script>
