<template>
 <div>
    <Layout class-prefix="layout">
       <NumberPad :value.sync="record.amount" @submit="saveRecord"/>
        <Tabs :data-source="recordTypeList" :value.sync="record.type"/>
      <div class="notes">
        <FormItem field-name="备注"
              placeholder="在这里输入备注"
              :value.sync="record.notes" />
      </div>
      <tags/>
    </Layout>
 </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import NumberPad from '@/components/Money/NumberPad.vue';
  import FormItem from '@/components/Money/FormItem.vue';
  import Tags from '@/components/Money/Tags.vue';
  import {Component} from 'vue-property-decorator';
  import Button from '@/components/Button.vue';
  import recordTypeList from '@/constants/recordTypeList';
  import Tabs from '@/components/Tabs.vue';


  @Component({
    components: {Tabs, Button, Tags, FormItem, NumberPad},
  })
  export default class Money extends Vue {
    get recordList() {
      return this.$store.state.recordList;
    }

    recordTypeList=recordTypeList;

    record: RecordItem = {
      tags: [],   /*初始值*/
      notes: '',
      type: '-',
      amount: 0
    };

    created() {
      this.$store.commit('fetchRecords');
    }

    saveRecord() {
            this.$store.commit('createRecord',this.record)
          }
   }
</script>

<style lang="scss" scoped>
   .layout-content {
      /*border: 3px solid red;*/
      display: flex;
      flex-direction: column-reverse; /*从下面开始布局*/
   }
  .notes {
    padding: 12px 0;
  }
</style>

<style scoped lang="scss">

</style>