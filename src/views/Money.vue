<template>
 <div>
    <Layout class-prefix="layout">
       <NumberPad/>
       <Types :xxx="  3333   "/>
       <Notes/>
      <tags/>
    </Layout>
 </div>
</template>

<script lang="ts">

   import NumberPad from '@/components/Money/NumberPad.vue';
   import Types from '@/components/Money/Types.vue';
   import Notes from '@/components/Money/Notes.vue';
   import Tags from '@/components/Money/Tags.vue';

   export default {
      name: 'Money.vue',
      components: {Tags, Notes, Types, NumberPad},
   };
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