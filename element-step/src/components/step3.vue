<template>
    <el-result type="success" title="操作成功" desc="预计两小时内到账">
        <div >
            <el-form ref="form" :label-width="labelWidth" :label-position="labelPosition">
                <el-form-item label="付款账户：">
                    {{ infoData.payAccount }}
                </el-form-item>
                <el-form-itemm label="收款账户：">
                    {{ infoData.gatheringAccount }}
                </el-form-itemm>
                <el-form-item label="收款人姓名：">
                    {{ infoData.gatheringName }}
                </el-form-item>
                <el-form-item label="转账金额：">
                    <strong>
                        <i class="el-icon-edit"></i>
                        {{ infoData.price }}
                    </strong>
                </el-form-item>
            </el-form>
        </div>
        <div class="ivu-text-center" >
            <el-button type="primary" @click="handleAgain">再转一笔</el-button>
            <el-button>查看账单</el-button>
        </div>
    </el-result>
</template>
<script>

    export default {
        props: {
            infoData: {
                type: Object
            }
        },
        methods: {
            handleAgain () {
                this.$emit('on-prev-step');
            }
        }
    }
</script>
