<template>
  <div>
    <bz-upload-picture :blank_img="blank_img" v-for="v in value" v-model="v.src" :alt="v.alt"></bz-upload-picture>
    <bz-upload-picture :blank_img="blank_img" v-model="new_img" @upload_done="addNew"></bz-upload-picture>
  </div>
</template>

<script>
  import BzUploadPicture from 'bz-upload-picture'
  export default {
    watch: {
      value: {
        handler: function (val, oldVal) {
          let imgs = val.filter(item => item.src !== '')
          if (val.length !== imgs.length) {
            this.$emit('input', val.filter(item => item.src !== ''))
          }
        },
        deep: true
      }
    },
    props: {
      value: {
        default: function () { return [] }
      },
      blank_img: {
        type: String,
        default: ''
      }
    },
    components: {
      BzUploadPicture
    },
    data: function () {
      return {
        new_img: ''
      }
    },
    methods: {
      addNew: function (src, alt) {
        this.value.push({src: src, alt: alt})
        this.new_img = ''
      }
    }
  }
</script>
