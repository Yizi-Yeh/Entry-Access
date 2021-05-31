<template>
    <el-form ref="form" :model="data" :rules="rules" :label-width="labelWidth" :label-position="labelPosition">
         <el-form-item label="接洽員工姓名：" prop="gatheringName" required>
            <el-input v-model="data.gatheringName" />
        </el-form-item>
        <el-form-item label="接洽員工電話：" prop="gatheringName">
            <el-input v-model="data.gatheringName" />
        </el-form-item>
        <el-form-item label="預約目的：" prop="gatheringName">
            <el-input v-model="data.gatheringName" />
        </el-form-item>
        <el-form-item label="備註：" prop="gatheringName">
            <el-input v-model="data.gatheringName" />
        </el-form-item>

        <el-form-item>
            <el-button type="primary" :loading="loading" @click="handleSubmit">提交</el-button>
            <el-button @click="handlePrev" class="ivu-ml">上一步</el-button>
        </el-form-item>
    </el-form>
</template>
<script>

    export default {
        props: {
            infoData: {
                type: Object
            }
        },
        data () {
            return {
                data: {
                    password: '123456'
                },
                rules: {
                    password: [
                        { required: true, message: '请输入支付密码', trigger: 'blur' }
                    ]
                },
                loading: false
            }
        },
        methods: {
            handleSubmit () {
                this.$refs.form.validate((valid) => {
                    this.loading = true;
                    if (valid) {
                        setTimeout(() => {
                            this.$emit('on-next-step', this.data);
                            this.loading = false;
                        }, 2000);
                    } else {
                        this.loading = false;
                    }
                });
            },
            handlePrev () {
                this.$emit('on-prev-step');
            }
        }
    }
</script>
