<template>
    <div>
        <zb-button type="default" @click="click">按钮</zb-button>

        <zb-dialog title="温馨提示" v-model="show" appendToBody>
            <template v-slot:title> 自定义标题 </template>
            <template> 内容 </template>
            <template v-slot:footer>
                <zb-button type="primary" plain>主要</zb-button>
                <zb-button type="success" plain>成功</zb-button>
            </template>
        </zb-dialog>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const show = ref(false);
const click = e => {
    show.value = true;
};
</script>

<style lang="scss"></style>
