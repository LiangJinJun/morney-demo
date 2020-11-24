<template>
 <div>
    <Layout class-prefix="layout">
       <NumberPad :value.sync="record.amount" @submit="saveRecord"/>
       <Types :value.sync="record.type"/>
       <Notes :value.sync="record.notes" />
      <tags :data-source.sync="tags" @update:value="onUpdateTags"/>
    </Layout>
 </div>
</template>

<script lang="ts">
    import Vue from 'vue';
   import NumberPad from '@/components/Money/NumberPad.vue';
   import Types from '@/components/Money/Types.vue';
   import Notes from '@/components/Money/Notes.vue';
   import Tags from '@/components/Money/Tags.vue';
    import {Component, Watch} from 'vue-property-decorator';
    import recordListModel from '@/models/recordListModel';
    import tagListModel from '@/models/tagListModel';


    const recordList= recordListModel.fetch();
    const tagList = tagListModel.fetch();



    @Component({
      components: {Tags, Notes, Types, NumberPad},
    })
   export default class Money extends Vue{
          tags=tagList;
          recordList: RecordItem[]=recordList;
          record: RecordItem={
            tags:[],   /*初始值*/
            notes:'',
            type:'-',
            amount:0
          }
          onUpdateTags(value: string[]){
            this.record.tags=value;
          }

          saveRecord(){
            const record2: RecordItem=recordListModel.clone(this.record);
            record2.createdAt= new Date()  /*当前时间*/
            this.recordList.push(record2)
            console.log(this.recordList);
          }
          @Watch('recordList')
          onRecordListChanged(){
            recordListModel.save(this.recordList);
          }
   }
</script>

<style lang="scss">
   .layout-content {
      /*border: 3px solid red;*/
      display: flex;
      flex-direction: column-reverse; /*从下面开始布局*/
   }
</style>

<style scoped lang="scss">

</style>