<template>
    <div>
        <div class="i-layout-page-header">
          <!-- heafer -->
            <el-page-header content="員工 / 訪客預約">
            </el-page-header>
        </div>
         <!-- card -->
        <el-card class="box-card">
            <!-- row -->
            <el-row>
              <!-- col -->
                <el-col :xl="{span: 12, offset: 6}" :lg="{span: 12, offset: 6}" :md="{span: 16, offset: 4}" :sm="{span: 20, offset: 2}" :xs="24">
                    <div class="ivu-p ivu-mb">
                        <el-steps  :active="currentStep" finish-status="success">
                            <el-step title="step01" description="預約資料"></el-step>
                            <el-step title="step02" description="訪客資料"></el-step>
                            <el-step title="step03" description="預約確認"></el-step>
                        </el-steps>
                    </div>
                    <step1 v-if="currentStep === 0" @on-next-step="(data) => handleSetStep(1, data)" />
                    <step2 v-if="currentStep === 1" :info-data="data" @on-next-step="(data) => handleSetStep(2)" @on-prev-step="handleSetStep(0)" />
                </el-col>
            </el-row>
            <step3 v-if="currentStep === 2" :info-data="data" @on-prev-step="handleSetStep(0)" />
            <div v-if="currentStep === 0">
            </div>
        </el-card>
    </div>
</template>
<script>
    import step1 from './components/step1';
    import step2 from './components/step2';
    import step3 from './components/step3';

    export default {
        name: 'App',
        components: { step1,step2,step3 },
        data () {
            return {
                currentStep: 0,
                data: {}
            }
        },
        methods: {
            handleSetStep (current, data) {
                this.currentStep = current;
                if (data) this.data = Object.assign(this.data, data);
            }
        }
    }
</script>
<style>
  .text {
    font-size: 14px;
  }

  .item {
    padding: 18px 0;
  }

  .box-card {
    width: 480px;
  }
</style>