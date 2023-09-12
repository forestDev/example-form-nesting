<script setup lang="ts">
import { ref } from 'vue'

import ThreeStateField from './ThreeStateField.vue'
import Collapse from './Collapse.vue'

const value = ref('')
const value1 = ref('')
const value2 = ref('')
const value3 = ref('')
const value4 = ref('')
const value5 = ref('')
const value6 = ref('')
const value7 = ref('')
const value8 = ref('')
const value9 = ref('')
</script>

<template>
    <div class="form">
        <div class="field">
            <ThreeStateField :values="['Yes', '', 'No']" label="example field" v-model="value" />
            <Collapse>
                <div class="sub-fields" v-if="value === 'Yes'">
                    <div class="field">
                        <ThreeStateField
                            :values="['Yes', '', 'No']"
                            label="sub field"
                            v-model="value1"
                        />
                        <Collapse>
                            <div class="sub-fields" v-if="value1 === 'Yes'">
                                <div class="field">
                                    <ThreeStateField
                                        :values="['Yes', '', 'No']"
                                        label="sub sub field"
                                        v-model="value2"
                                    />
                                    <Collapse>
                                        <div class="sub-fields" v-if="value2 === 'Yes'">
                                            <div class="field">
                                                <ThreeStateField
                                                    :values="['Yes', '', 'No']"
                                                    label="sub sub sub field"
                                                    v-model="value9"
                                                />
                                            </div>
                                        </div>
                                    </Collapse>
                                </div>
                                <div class="field">
                                    <ThreeStateField
                                        :values="['Yes', '', 'No']"
                                        label="sub field 2"
                                        v-model="value3"
                                    />
                                </div>
                                <div class="field">
                                    <ThreeStateField
                                        :values="['Yes', '', 'No']"
                                        label="sub field 3"
                                        v-model="value4"
                                    />
                                </div>
                            </div>
                        </Collapse>
                    </div>
                    <div class="field">
                        <ThreeStateField
                            :values="['Yes', '', 'No']"
                            label="sub field 2"
                            v-model="value5"
                        />
                    </div>
                    <div class="field">
                        <ThreeStateField
                            :values="['Yes', '', 'No']"
                            label="sub field 3"
                            v-model="value6"
                        />
                    </div>
                </div>
            </Collapse>
        </div>
        <div class="field">
            <ThreeStateField
                class="field"
                :values="['Yes', '', 'No']"
                label="example field 2"
                v-model="value7"
            />
        </div>
        <div class="field">
            <ThreeStateField
                class="field"
                :values="['Yes', '', 'No']"
                label="example field 3"
                v-model="value8"
            />
        </div>
    </div>
</template>
<style lang="scss" scoped>
.form {
    height: 80vh;
    width: 800px;

    .field {
        margin-bottom: 20px;
    }

    .sub-fields {
        padding-left: 16px;
        margin-left: 12px;
        margin-top: 12px;
        border-left: 1px solid black;

        &:deep(.heading::after) {
            content: '';
            position: absolute;
            height: 1px;
            width: 10px;
            background-color: black;
            left: -19px;
            top: 13px;
        }
    }
}
</style>
