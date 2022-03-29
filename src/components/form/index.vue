<template>
  <div class=''>
    <k-form :model="model" :rules="rules" ref="loginFrom">
      <k-form-item label="用户名" prop="username">
        <k-input v-model="model.username" type="text" />
      </k-form-item>
      <k-form-item label="密码" prop="password">
        <k-input v-model="model.password" type="password" />
      </k-form-item>
    </k-form>
    <button @click="onLogin">
      登陆
    </button>
    <br />
    {{model}}
  </div>
</template>

<script>
  import KInput from './k-input.vue'
  import KFormItem from './k-form-item.vue'
  import KForm from './k-form'
  export default {
    name: 'm-form',
    components: {
      'k-input': KInput,
      'k-form-item': KFormItem,
      'k-form': KForm
    },
    data() {
      return {
        model: {
          username: '',
          passeord: ''
        },
        rules: {
          username: [{required: true, message: '用户必填'}],
          password: [{required: true, message: '密码必填'}]
        }
      }
    },
    computed: {},
    watch: {},
    methods: {
      onLogin () {
        this.$refs.loginFrom.validate((isValid) => {
          if (isValid) {
            alert('登陆')
          } else {
            alert('失败');
          }
        })
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