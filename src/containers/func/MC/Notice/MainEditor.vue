<template>
  <el-dialog :title="title | t" :visible="showEditor"
    :close-on-click-modal="false" :close-on-press-escape="false" :show-close="false">
    <el-form :model="form" label-width="120px">
      <el-form-item :label="'noticeType' | t">
        <el-select v-model="form.noticeType">
          <el-option v-for="option in noticeTypeOptions" :key="'noticeType' + option.id" :label="option.text" :value="option.value"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item :label="'isWEB' | t">
        <el-switch :on-text="toMark(true)" :off-text="toMark(false)" v-model="form.isWEB"></el-switch>
      </el-form-item>
      <el-form-item :label="'isAPP' | t">
        <el-switch :on-text="toMark(true)" :off-text="toMark(false)" v-model="form.isAPP"></el-switch>
      </el-form-item>
      <el-form-item :label="'isEmail' | t">
        <el-switch :on-text="toMark(true)" :off-text="toMark(false)" v-model="form.isEmail"></el-switch>
      </el-form-item>
      <el-form-item :label="'isTextMessage' | t">
        <el-switch :on-text="toMark(true)" :off-text="toMark(false)" v-model="form.isTextMessage"></el-switch>
      </el-form-item>
      <el-form-item :label="'subject' | t">
        <el-input v-model="form.subject"></el-input>
      </el-form-item>
      <el-form-item :label="'content' | t">
        <el-input v-model="form.content"></el-input>
      </el-form-item>
      <el-form-item :label="'receiveList' | t">
        <el-input v-model="form.receiveList"></el-input>
      </el-form-item>
      <el-form-item :label="'remark' | t">
        <el-input v-model="form.remark"></el-input>
      </el-form-item>
    </el-form>
    <el-button @click="handleSubmit" :loading="waiting" type="primary">{{ 'btnConfirm' | t }}</el-button>
    <el-button @click="handleCancel">{{ 'btnCancel' | t }}</el-button>
  </el-dialog>
</template>

<script>
import { listEditorMixin } from 'containers/func/listHelper'
import { toMark } from 'utils/common'

export default {
  name: 'MainEditor',
  mixins: [listEditorMixin],
  computed: {
    noticeTypeOptions: function() {
      return this.caller.noticeTypeOptions
    },
  },
  methods: {
    toMark: toMark,
  },
}
</script>
