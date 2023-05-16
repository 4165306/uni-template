<template>
    <u--form
            labelPosition="left"
            :model="data.model1"
            :rules="data.rules"
            ref="form1"
    >
        <u-form-item
                label="姓名"
                prop="userInfo.name"
                borderBottom
                ref="item1"
        >
            <u--input
                    v-model="data.model1.userInfo.name"
                    border="none"
            ></u--input>
        </u-form-item>
        <u-form-item
                label="性别"
                prop="userInfo.sex"
                borderBottom
                @click="data.showSex = true; hideKeyboard()"
                ref="item1"
        >
            <u--input
                    v-model="data.model1.userInfo.sex"
                    disabled
                    disabledColor="#ffffff"
                    placeholder="请选择性别"
                    border="none"
            ></u--input>
            <template #right>
                <u-icon
                        name="arrow-right"
                ></u-icon>
            </template>
        </u-form-item>
    </u--form>
    <u-action-sheet
            :show="data.showSex"
            :actions="data.actions"
            title="请选择性别"
            description="如果选择保密会报错"
            @close="data.showSex = false"
            @select="data.sexSelect"
    >
    </u-action-sheet>
</template>

<script setup>

import {reactive} from "vue";

const data = reactive({
    showSex: false,
    model1: {
        userInfo: {
            name: 'uview-plus UI',
            sex: '',
        },
    },
    actions: [{
        name: '男',
    },
        {
            name: '女',
        },
        {
            name: '保密',
        },
    ],
    rules: {
        'userInfo.name': {
            type: 'string',
            required: true,
            message: '请填写姓名',
            trigger: ['blur', 'change']
        },
        'userInfo.sex': {
            type: 'string',
            max: 1,
            required: true,
            message: '请选择男或女',
            trigger: ['blur', 'change']
        },
    },
    radio: '',
    switchVal: false
})

const hideKeyboard = () => {
    // todo 隐藏键盘
}

</script>

<style>

</style>
