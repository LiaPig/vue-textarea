<template>
    <div class="my-textarea">
      <textarea ref="textarea" :style="{'height': height}" v-model="value" class="textarea" ></textarea>
    </div>
</template>

<script>
  import calcTextareaHeight from '@/assets/calcTextareaHeight';

  export default {
    name: 'my-textarea',
    data() {
      return {
        // textarea内容
        value: '',
        // 动态高度
        height: '30px'
      }
    },
    watch: {
      value() {
        this.getHeight();
      }
    },
    methods: {
      getHeight() {
        this.height = calcTextareaHeight(this.$refs.textarea, 1, null).height;
      }
    }
  }
</script>

<style scoped>
  .my-textarea .textarea {
    display: inline-block;
    width: 400px;
    /*height: 30px;*/
    line-height: 30px;
    font-size: 30px;
    resize: none;
  }
</style>
