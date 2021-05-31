<template>
    
    <el-form ref="form" :model="data" :rules="rules" :label-width="labelWidth" :label-position="labelPosition">
         <br>
         <br>

        <el-form-item label="起始日期" required>
        <div class="block">
            <span class="demonstration"></span>
            <el-date-picker
             v-model="value1"
             type="week"
            format="gggg 第 ww 周"
             placeholder="請選擇日期">
            </el-date-picker>
            </div>
        </el-form-item>

        <el-form-item label="結束日期" required>
            <span class="demonstration"></span>
            <el-date-picker
             v-model="value1"
             type="week"
            format="gggg 第 ww 周"
             placeholder="請選擇日期">
            </el-date-picker>
        </el-form-item>

        <el-form-item label="申請者身分證：" prop="gatheringName">
            <el-input v-model="data.gatheringName" />
        </el-form-item>

        <el-form-item label="申請者姓名：" prop="gatheringName">
            <el-input v-model="data.gatheringName" />
        </el-form-item>

        <el-form-item label="申請者電話：" prop="gatheringName">
            <el-input v-model="data.gatheringName" />
        </el-form-item>

        <el-form-item label="申請者信箱：" prop="gatheringName">
            <el-input v-model="data.gatheringName" />
        </el-form-item>

        <el-form-item>
            <el-button  size="medium" type="info" round @click="handleSubmit">下一步</el-button>
        </el-form-item>

    </el-form>
</template>
<script>
    export default {
        data () {
            return {
                data: {
                    payAccount: 'admin@iview.design',
                    gatheringAccount: 'aresn@iview.design',
                    gatheringType: 'wechat',
                    gatheringName: 'Aresn',
                    price: '100'
                },
                rules: {
                    payAccount: [
                        { required: true, message: '请选择付款账户', trigger: 'change' }
                    ],
                    gatheringAccount: [
                        { required: true, message: '请输入收款账户', trigger: 'blur' },
                        { type: 'email', message: '账户名应为邮箱格式', trigger: 'blur' }
                    ],
                    gatheringName: [
                        { required: true, message: '请输入收款人姓名', trigger: 'blur' }
                    ],
                    price: [
                        { required: true, message: '请输入转账金额', trigger: 'blur' },
                        { pattern: /^(\d+)((?:\.\d+)?)$/, message: '请输入合法金额数字' }
                    ]
                }
            }
        },
        methods: {
            handleSubmit () {
                this.$refs.form.validate((valid) => {
                    if (valid) {
                        this.$emit('on-next-step', this.data);
                    }
                });
            }
        }
    }
</script>
