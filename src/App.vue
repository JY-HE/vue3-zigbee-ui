<template>
    <div>
        <!-- <zb-button type="default" @click="click">按钮</zb-button>

        <zb-dialog title="温馨提示" v-model="show" appendToBody>
            <template v-slot:title> 自定义标题 </template>
            <template> 内容 </template>
            <template v-slot:footer>
                <zb-button type="primary" plain>主要</zb-button>
                <zb-button type="success" plain>成功</zb-button>
            </template>
        </zb-dialog> -->
        <zb-input v-model="inputValue" placeholder="请输入信息" @change="change"></zb-input>
    </div>
</template>

<script setup>
import { ref, watch } from 'vue';

const show = ref(false);
const inputValue = ref('');
const click = e => {
    show.value = true;
};
watch(inputValue, newValue => {
    // console.log('Rd ~ file: App.vue ~ line 26 ~ newValue', newValue);
});
const change = val => {
    console.log('Rd ~ file: App.vue ~ line 29 ~ onblur ~ val', val);
};
</script>

<style lang="scss"></style>
