<template>
   <nav>
      <router-link to="/money"   class="item">
         <Icon name="chart"/>
         记账
      </router-link>
      <router-link to="/labels" class="item">
         <Icon name="Label"/>
         标签
      </router-link>
      <router-link to="/statistics" class="item">
         <Icon name="Money"/>
         统计
      </router-link>
   </nav>
</template>

<script  lang="ts">

   export default {
      name: 'Nav',
   };
</script>

<style scoped lang="scss">
   nav {
    display: flex;
      box-shadow: 0 0 3px rgba(0,0,0,0.25);
      flex-direction: row;    /*flex-direction: row    水平排列*/
      >.item {
         width: 33.33333%;
         display: flex;
         justify-content: center;
         align-items: center;
         flex-direction: column;
         .icon {
            width: 32px;
            height: 32px;
         }
      }
   }


</style>