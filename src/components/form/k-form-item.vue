<template>
  <div class=''>
    <label v-if="label" for="">
      {{label}}
    </label>
    <slot></slot>
    <p v-if="errorMessage">
      {{errorMessage}}
    </p>
  </div>
</template>

<script>
import Schema from 'async-validator'
export default {
  name: 'k-form-item',
  components: {},
  props: {
    label: {
      type: String,
      default: ''
    },
    prop: {
      type: String
    }
  },
  inject: ['form'],
  data() {
    return {
      errorMessage: ''
    }
  },
  computed: {},
  watch: {},
  methods: {
    validate () {
      // 执行组件的校验
      // 1.获取校验规则
      const rules =  this.form.rules[this.prop]
      // 2.获取数据
      const value =  this.form.model[this.prop]
      // 执行校验
      const desc = {
        [this.prop]: rules
      }
      const schema = new Schema(desc)
      // 参数2是校验错误对象数组
      // 返回Promise<boolean>
      return schema.validate({[this.prop]: value}, errors => {
        if (errors) {
          this.errorMessage = errors[0].message
        } else {
          // 没错就清除错误信息
          this.errorMessage = ''
        }
      })
    }
  },
  created() {

  },
  mounted() {
    // 监听检验事件并执行校验
    this.$on('validate', () => {
      this.validate()
    })
  },
}
</script>
<style scoped lang='scss'>

</style>