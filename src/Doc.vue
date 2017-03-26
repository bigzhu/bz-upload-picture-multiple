<template>
  <div>
    <doc :name="name"
      :desc="desc"
      :parm_desc="parm_desc"
      :parms="parms"
      :code="code"
      >
      <bz v-model="imgs"></bz>
    </doc>
  </div>
</template>
<script>
  // import toastr from 'toastr'

  import Bz from './Bz'
  import Doc from 'bz-doc'
  export default {
    components: {
      Bz,
      Doc
    },
    data: function () {
      return {
        imgs: [],
        loading: false,
        name: 'bz-upload-picture-multiple',
        desc: '登录页面',
        parms: [
          {parm: 'check_done', desc: 'v-on 绑定 check_done 事件，完成了用户名密码必填的check'},
          {parm: 'user_name_placeholder', desc: '可选'},
          {parm: 'password_placeholder', desc: '可选'},
          {parm: 'loading', desc: '控制按钮loading效果(可选)'}
        ],
        parm_desc: ``,
        code: `<bz v-on:check_done="call_back"></bz>`
      }
    },
    methods: {
    }
  }
</script>
