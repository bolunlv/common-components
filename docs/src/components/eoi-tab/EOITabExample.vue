<template>
  <EOITab :active-tab="activeTab" :tabs-data="tabsData" @handle-click="handleClick">
    <template v-for="(screen, index) in screenData" :key="index" #[screen.name]>
        <component :is="screen.type" />
    </template>
  </EOITab>
</template>
<script setup lang="ts">
  import EOITab from '../../../../component/componentss/component/EoiPlus/index';
  import { ref, markRaw } from 'vue'
  import { ElInput, ElDatePicker } from 'element-plus';

  const screenData = ref([
   {
      name: 'Tab1',
      type: markRaw(ElInput),
   },
   {
      name: 'Tab2',
      type: markRaw(ElDatePicker),
   },
  ])

  const tabsData = ref([
    {
      label: 'Tab1', 
      name: 'Tab1', 
      disabled: false,
    },
    {
      label: 'Tab2', 
      name: 'Tab2', 
      disabled: false,
    },
  ])

  const activeTab = ref('Tab1')
  const handleClick = (val: any) => {
    console.log(val, '标签页')
  }
</script>


