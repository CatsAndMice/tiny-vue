<template>
  <div>
    <tiny-radio disabled v-model="radio" label="禁用">选中禁用</tiny-radio>
    <tiny-radio disabled v-model="radio" label="不选中禁用">不选中禁用</tiny-radio>
    <div style="margin-top: 20px">
      <tiny-radio-group disabled v-model="radio1">
        <tiny-radio :label="3">备选项1</tiny-radio>
        <tiny-radio :label="6">备选项2</tiny-radio>
        <tiny-radio :label="9">备选项3</tiny-radio>
      </tiny-radio-group>
    </div>

    <div style="margin-top: 20px">
      <tiny-radio-group v-model="radio2">
        <tiny-radio-button label="1">日度</tiny-radio-button>
        <tiny-radio-button disabled label="2">月度</tiny-radio-button>
        <tiny-radio-button label="3">年度</tiny-radio-button>
      </tiny-radio-group>
    </div>
  </div>
</template>

<script lang="jsx">
import { Radio, RadioButton, RadioGroup } from '@opentiny/vue'

export default {
  components: {
    TinyRadio: Radio,
    TinyRadioButton: RadioButton,
    TinyRadioGroup: RadioGroup
  },
  data() {
    return {
      radio: '禁用',
      radio1: '3',
      radio2: '1'
    }
  }
}
</script>
