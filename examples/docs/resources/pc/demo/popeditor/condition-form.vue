<template>
  <div class="demo-form">
    <tiny-form ref="ruleForm" @submit.native.prevent :model="createData" :append-to-body="true" :rules="rules" label-width="100px">
      <tiny-form-item label="必填" prop="users">
        <tiny-input v-model="createData.users"></tiny-input>
      </tiny-form-item>
      <tiny-form-item label="日期" prop="datepicker">
        <tiny-date-picker type="daterange" v-model="createData.datepicker"></tiny-date-picker>
      </tiny-form-item>
      <tiny-form-item label="等级" prop="radio">
        <tiny-checkbox-group v-model="createData.radio" :options="options"></tiny-checkbox-group>
      </tiny-form-item>
      <tiny-form-item label="邮件" prop="email" class="my-form-item">
        <tiny-input v-model="createData.email"></tiny-input>
      </tiny-form-item>
      <tiny-form-item label="文本" prop="textarea">
        <tiny-popeditor
          v-model="createData.textarea"
          :append-to-body="false"
          :grid-op="gridOp"
          text-field="name"
          value-field="id"
          :conditions="conditions"
        ></tiny-popeditor>
      </tiny-form-item>
      <tiny-form-item>
        <tiny-button type="primary" @click="reset">重置</tiny-button>
        <tiny-button type="primary" @click="handleSubmit('ruleForm')">提交</tiny-button>
      </tiny-form-item>
    </tiny-form>
  </div>
</template>

<script lang="jsx">
import { Form, FormItem, Input, DatePicker, Button, Modal, CheckboxGroup, Popeditor } from '@opentiny/vue'

export default {
  components: {
    TinyForm: Form,
    TinyFormItem: FormItem,
    TinyInput: Input,
    TinyDatePicker: DatePicker,
    TinyButton: Button,
    TinyCheckboxGroup: CheckboxGroup,
    TinyPopeditor: Popeditor
  },
  data() {
    const dataset = [
      {
        id: '1',
        name: 'GFD科技YX公司',
        city: '福州',
        province: '福建'
      },
      {
        id: '2',
        name: 'WWW科技YX公司',
        city: '深圳',
        province: '广东'
      },
      {
        id: '3',
        name: 'RFV有限责任公司',
        city: '中山',
        province: '广东'
      },
      {
        id: '4',
        name: 'TGB科技YX公司',
        city: '龙岩',
        province: '福建'
      },
      {
        id: '5',
        name: 'YHN科技YX公司',
        city: '韶关',
        province: '广东'
      },
      {
        id: '6',
        name: 'WSX科技YX公司',
        city: '黄冈',
        province: '武汉'
      },
      {
        id: '7',
        name: 'KBG物业YX公司',
        city: '赤壁',
        province: '武汉'
      },
      {
        id: '8',
        name: '深圳市福德宝网络技术YX公司',
        province: '广东',
        city: '深圳'
      },
      {
        id: '9',
        name: 'KBG物业YX公司',
        city: '赤壁',
        province: '武汉'
      },
      {
        id: '10',
        name: '深圳市福德宝网络技术YX公司',
        province: '广东',
        city: '深圳'
      }
    ]
    return {
      options: [
        { label: '45', text: '很好', events: { click: this.handleClick } },
        { label: '46', text: '一般' }
      ],
      createData: {
        radio: [],
        users: '',
        email: '',
        datepicker: [],
        textarea: ''
      },
      gridOp: {
        columns: [
          {
            field: 'id',
            title: 'ID',
            width: 40
          },
          {
            field: 'name',
            title: '名称'
          },
          {
            field: 'province',
            title: '省份',
            width: 80
          },
          {
            field: 'city',
            title: '城市',
            width: 80
          }
        ],
        data: dataset
      },
      conditions: [
        { label: '公司名', labelWidth: '80px', field: 'name' },
        { label: '城市', labelWidth: '80px', field: 'city' }
      ],
      value: '',
      rules: {
        radio: [{ required: true, message: '必填', trigger: 'change' }],
        textarea: [{ required: true, message: '必填', trigger: 'change' }],
        users: [
          { required: true, message: '必填', trigger: 'blur' },
          { min: 2, max: 11, message: '长度必须不小于2', trigger: 'change' }
        ],
        datepicker: { type: 'date' },
        email: { type: 'email' }
      }
    }
  },
  methods: {
    reset() {
      this.$refs.ruleForm.resetFields()
    },
    handleSubmit(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          Modal.alert('提交成功')
        }
      })
    }
  }
}
</script>

<style>
.demo-form {
  width: 60%;
  position: relative;
}

.demo-form .tiny-date-editor--daterange.tiny-input {
  width: 100%;
}
</style>
