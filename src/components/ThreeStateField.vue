<script setup lang="ts">
const props = defineProps({
    label: String,
    values: Array<String>,
    modelValue: String
})

const isChecked = (value: String) => value === props.modelValue
</script>
<template>
    <h4 class="heading">{{ label }}</h4>
    <div class="wrapper">
        <template v-for="(value, idx) in values" :key="idx">
            <label @click="$emit('update:modelValue', value)" class="label">{{ value }}</label>
            <input class="input" type="radio" :value="value" :checked="isChecked(value)" />
        </template>
        <div class="pointer"></div>
    </div>
</template>
<style lang="scss" scoped>
.heading {
    margin-bottom: 12px;
    margin-left: 4px;
    position: relative;
}
.wrapper {
    width: 160px;
    background: #dee2e6;
    border-radius: 16px;
    display: flex;
    flex-direction: row;
    position: relative;

    .label {
        width: 33.33%;
        padding: 3px;
        color: black;
        text-align: center;
        z-index: 5;
        font-weight: bold;
    }

    .input:nth-of-type(1):checked ~ .pointer {
        background-color: #29cac4;
        left: 0;
    }

    .input:nth-of-type(2):checked ~ .pointer {
        left: 33.33%;
    }

    .input:nth-of-type(3):checked ~ .pointer {
        left: 66.66%;
        background-color: rgb(246, 61, 61);
    }

    .input {
        left: 0;
        opacity: 0;
        position: absolute;
    }

    .pointer {
        height: 100%;
        position: absolute;
        z-index: 2;
        width: 33.33%;
        left: 33.33%;
        top: 0;
        background-color: white;
        border-radius: 16px;
        transition: 0.2s;
        transition-property: left;
    }
}
</style>
