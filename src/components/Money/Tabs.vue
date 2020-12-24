<template>
  <ul class="tabs" :class="{[classPrefix+'-tabs']:classPrefix}">
    <li v-for="item in dataSource" :key="item.value"
        class="tabs-item"
        :class="liClass(item)"
        @click="select(item)">{{item.text}}
    </li>
  </ul>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component, Prop} from 'vue-property-decorator';

  type DataSourceItem = { text: string; value: string }

  @Component
  export default class Tabs extends Vue {
    @Prop({required: true, type: Array}) dataSource!: DataSourceItem[];
    /*dataSource! --- 在后面加叹号说明让TypeScript不用管这句话*/
    /*required: true 是否必需，true为必须*/
    /*readonly --- 只读，不能更改*/
    @Prop(String) readonly value!: string;
    @Prop(String) classPrefix?: string;
    /*后面加个问号，说明这个属性有可能不存在*/
    @Prop({type:String,default:'64px'})
    height!: string

   liClass(item: DataSourceItem){
    return {
       [this.classPrefix+'-tabs-item']:this.classPrefix,
     selected: item.value===this.value,
    }
   }

    select(item: DataSourceItem) {
      this.$emit('update:value', item.value);
    }
  }
</script>

<style scoped lang="scss">
  .tabs {
    background-color: #5F9EA0;
    display: flex;
    text-align: center;
    font-size: 24px;
    &-item {
      width: 50%;
      height: 64px;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      &.selected {
        color: white;
      }

      &.selected::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 4px;
        background: #333;
      }

    }

  }

</style>