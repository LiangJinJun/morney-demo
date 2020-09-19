<template>
   <nav>
      <router-link to="/money"   class="item" active-class="selected">
         <Icon name="chart"/>
         记账
      </router-link>
      <router-link to="/labels" class="item" active-class="selected">
         <Icon name="Label"/>
         标签
      </router-link>
      <router-link to="/statistics" class="item" active-class="selected">
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
   @import "~@/assets/style/helper.scss";

   nav {
      @extend %outerShadow;
    display: flex;
      font-size: 12px;
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
      >.item.selected {
         color: $color-highlight;
      }
   }


</style>