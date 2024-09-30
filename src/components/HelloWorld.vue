<template>
  <n-space vertical>
    <n-h1 strong>NginxWebUi转换工具</n-h1>
    <n-steps :current="current" :status="currentStatus">
      <n-step title="粘贴配置文件">
        <div class="n-step-description">
          <p>请在NginxWebUi中复制此内容</p>
          
        </div>
      </n-step>
      <n-step title="选择站点">
        <div class="n-step-description">
          <p>此处可以选择站点</p>
          <!-- <n-button
            v-if="current === 2"
            :type="buttonType"
            size="small"
            @click="handleButtonClick"
          >
            Next
          </n-button> -->
        </div>
      </n-step>
      <n-step title="导入">
        <div class="n-step-description">
          <p>导入数据</p>
          <!-- <n-button
            v-if="current === 3"
            :type="buttonType"
            size="small"
            @click="handleButtonClick"
          >
            Next
          </n-button> -->
        </div>
      </n-step>
    </n-steps>
    <div><n-button
      v-if="current > 1"
      size="small"
      @click="handleButtonClick"
    >
      上一步
    </n-button>
    <n-button
      type="success"
      size="small"
      @click="handleButtonClick"
    >
      下一步
    </n-button></div>
  </n-space>
</template>

<script>
import { computed, defineComponent, ref } from "vue";
import {
  NButton,
  NSteps,
  NSpace,
  NStep,
  NRadioButton,
  NRadioGroup,
  NH1,
} from "naive-ui";

export default defineComponent({
  components: {
    NButton,
    NSteps,
    NStep,
    NSpace,
    NRadioButton,
    NRadioGroup,
    NH1,
  },
  setup() {
    const currentRef = ref(1);
    const currentStatusRef = ref("process");

    return {
      current: currentRef,
      currentStatus: currentStatusRef,
      handleButtonClick() {
        currentRef.value = (currentRef.value % 4) + 1;
      }
    };
  },
});
</script>
