<template>
    <button
        class="zb-button"
        :class="[
            `zb-button-${type}`,
            {
                'is-plain': plain,
                'is-round': round,
                'is-circle': circle,
                'is-disabled': disabled,
                'is-mimicry': mimicry,
            },
        ]"
        @click="handleClick"
        :disabled="disabled"
    >
        <i :class="icon" v-if="icon"></i>
        <span v-if="$slots.default"><slot></slot></span>
    </button>
</template>

<script>
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'ZbButton',
    emits: ['click'],
    props: {
        // 按钮类型
        type: {
            type: String,
            default: 'default',
            validator: function (value) {
                return (
                    ['default', 'success', 'primary', 'danger', 'warning', 'info', 'text'].indexOf(
                        value
                    ) !== -1
                );
            },
        },
        // 朴素按钮
        plain: {
            type: Boolean,
            default: false,
        },
        // 圆角按钮
        round: {
            type: Boolean,
            default: false,
        },
        // 圆按钮
        circle: {
            type: Boolean,
            default: false,
        },
        // icon图标
        icon: {
            type: String,
            default: '',
        },
        // 禁用属性
        disabled: {
            type: Boolean,
            default: false,
        },
        // 拟态
        mimicry: {
            type: Boolean,
            default: false,
        },
    },
    setup(_, { emit }) {
        const handleClick = e => {
            emit('click', e);
        };

        return { handleClick };
    },
});
</script>

<style lang="scss">
.zb-button {
    display: inline-block;
    line-height: 1;
    white-space: nowrap;
    cursor: pointer;
    background: #ffffff;
    border: 1px solid #dcdfe6;
    color: #606266;
    -webkit-appearance: none;
    text-align: center;
    box-sizing: border-box;
    outline: none;
    margin: 0;
    transition: 0.1s;
    font-weight: 500;
    //禁止元素的文字被选中
    -moz-user-select: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    padding: 12px 20px;
    font-size: 16px;
    border-radius: 4px;
    &:hover,
    &:focus {
        color: #409eff;
        border-color: #c6e2ff;
        background-color: #ecf5ff;
    }
    // 朴素按钮样式
    &.is-plain {
        &:hover,
        &:focus {
            background: #fff;
            border-color: #489eff;
            color: #409eff;
        }
    }
    // 圆角按钮样式
    &.is-round {
        border-radius: 20px;
        padding: 12px 23px;
    }
    // 圆按钮样式
    &.is-circle {
        border-radius: 50%;
        padding: 12px;
    }
    // disabled属性
    &.is-disabled {
        cursor: not-allowed;
    }
    // 拟态样式
    &.is-mimicry {
        box-shadow: inset 3px 6px 10px #ccc, inset -3px -7px 10px #fff;
    }
}

// 主要按钮
.zb-button-primary {
    color: #fff;
    background-color: #409eff;
    border-color: #409eff;
    &:hover,
    &:focus {
        background: #66b1ff;
        background-color: #66b1ff;
        color: #fff;
    }
    // 朴素按钮样式
    &.is-plain {
        color: #409eff;
        background: #ecf5ff;
        &:hover,
        &:focus {
            background: #409eff;
            border-color: #409eff;
            color: #fff;
        }
    }
    &.is-mimicry {
        box-shadow: inset 3px 6px 10px #337ecc, inset -3px -7px 10px #4dbeff;
    }
}

// 成功按钮
.zb-button-success {
    color: #fff;
    background-color: #67c23a;
    border-color: #67c23a;
    &:hover,
    &:focus {
        background: #85ce61;
        background-color: #85ce61;
        color: #fff;
    }
    &.is-plain {
        color: #67c23a;
        background: #c2e7b0;
        &:hover,
        &:focus {
            background: #67c23a;
            border-color: #67c23a;
            color: #fff;
        }
    }
    &.is-mimicry {
        box-shadow: inset 3px 6px 10px #6aa54e, inset -3px -7px 10px #a0f774;
    }
}

// 信息按钮
.zb-button-info {
    color: #fff;
    background-color: #909399;
    border-color: #909399;
    &:hover,
    &:focus {
        background: #a6a9ad;
        background-color: #a6a9ad;
        color: #fff;
    }
    &.is-plain {
        color: #909399;
        background: #d3d4d6;
        &:hover,
        &:focus {
            background: #909399;
            border-color: #909399;
            color: #fff;
        }
    }
    &.is-mimicry {
        box-shadow: inset 3px 6px 10px #73767a, inset -3px -7px 10px #adb0b8;
    }
}

// 警告按钮
.zb-button-warning {
    color: #fff;
    background-color: #e6a23c;
    border-color: #e6a23c;
    &:hover,
    &:focus {
        background: #ebb563;
        background-color: #ebb563;
        color: #fff;
    }
    &.is-plain {
        color: #e6a23c;
        background: #f5dab1;
        &:hover,
        &:focus {
            background: #e6a23c;
            border-color: #e6a23c;
            color: #fff;
        }
    }
    &.is-mimicry {
        box-shadow: inset 3px 6px 10px #bc914f, inset -3px -7px 10px #ffd977;
    }
}

// 危险按钮
.zb-button-danger {
    color: #fff;
    background-color: #f56c6c;
    border-color: #f56c6c;
    &:hover,
    &:focus {
        background: #f78989;
        background-color: #f78989;
        color: #fff;
    }
    &.is-plain {
        color: #f56c6c;
        background: #fbc4c4;
        &:hover,
        &:focus {
            background: #f56c6c;
            border-color: #f56c6c;
            color: #fff;
        }
    }
    &.is-mimicry {
        box-shadow: inset 3px 6px 10px #c45656, inset -3px -7px 10px #ff8282;
    }
}

// 文本按钮
.zb-button-text {
    color: #606266;
    border-color: transparent;
    background: transparent;
    padding: 0;
    &:hover,
    &:focus {
        color: #409eff;
        border-color: transparent;
        background: transparent;
        padding: 0;
    }

    &.is-disabled {
        cursor: not-allowed;
        color: #c0c4cc;
    }
}

// icon样式
.zb-button [class*='zb-icon-'] + span {
    margin-left: 5px;
}
</style>
