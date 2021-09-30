<template>
  <VueForm
      v-model="formData"
      :schema="schema"
      :uiSchema="uiSchema"
      :formProps="formProps"
      :formFooter="formFooter"
      @submit="handlerSubmit"
      @form-mounted="handleFormMounted"
  />

</template>

<script>
//  使用
import VueForm from '@lljj/vue3-form-ant';
import {ref} from "vue";

export default {
  name: 'Demo',
  components: {
    VueForm
  },
  setup() {
    const formData = {};
    const schema = ref({});
    const uiSchema = ref({});
    const formProps = ref({});
    const formFooter = ref({});
    schema.value = {
      "title": "标题",
      "type": "object",
      "properties": {
        "id": {
          "title": "Id",
          "type": "string"
        },
        "version": {
          "title": "Version",
          "default": 1,
          "type": "integer"
        },
        "content": {
          "title": "内容",
          "type": "string"
        }
      },
      "required": [
        "content"
      ]
    };
    uiSchema.value = {
      'ui:layout': 'horizontal',
      id: {
        'ui:widget': 'hidden',
      },
      version: {
        'ui:widget': 'hidden',
      },
      content: {
        'ui:widget': 'a-textarea',
      },
    }
    formProps.value = {
      labelCol: {
        span: 4,
      },
      wrapperCol: {
        span: 14,
      },
      layout: 'horizontal',
    };
    formFooter.value = {
      show: true, // 是否显示默认底部
      okBtn: 'Submit', // 确认按钮文字
      okBtnProps: {type: 'primary'}, // 传递确认按钮的 props，例如配置按钮 loading 状态 okBtnProps: { loading: true }
      cancelBtn: 'Cancel', // 取消按钮文字
      formItemAttrs: {
        wrapperCol: {span: 10, offset: 8},
      },
    }

    return {
      formData,
      schema,
      uiSchema,
      formProps,
      formFooter
    }
  },
  methods: {
    handlerSubmit(formData) {
      console.log("submit")
    },
    handleFormMounted() {
      console.log("FormMounted")
    }
  }
}
;

</script>

<style scoped>

</style>