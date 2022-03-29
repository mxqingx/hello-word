<template>
<div class=''>
  <input @input="onInput($event)" :value="value" v-bind="$attrs">
</div>
</template>

<script>

export default {
  name: 'k-input',
  inheritAttrs: false, // 避免顶层容器继承
  components: {},
  props: {
    value: {
      type: String,
      default: ''
    }
  },
  data() {
    return {

    }
  },
  computed: {},
  watch: {},
  methods: {
    onInput (e) {
      this.$emit('input', e.target.value)
      // 通知formItem校验
      this.$parent.$emit('validate')
    }
  },
  created() {

  },
  mounted() {

  },
}
</script>
<style scoped lang='scss'>

</style>