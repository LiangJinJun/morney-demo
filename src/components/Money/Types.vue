<template>
   <div>
      <ul class="types">
         <li :class="type === '-' && 'selected'" @click="selectType('-')">支出</li>
         <li :class="type === '+' && 'selected'" @click="selectType('+')">收入</li>
      </ul>
   </div>
</template>

<script>
   export default {
      name: 'Types',
      props:['xxx'],
      data(){
         return {
            type:'-'  //'-'表示支出 '+' 表示收入
         }
      },
     mounted(){
        console.log(this.xxx)
     },
      methods:{
         selectType(type){ // 给我一个新的 type  这个type只能是'-'和'+' 中的一个
            if(type !== '-' && type !== '+'){   // 如果不是这个两个的其中一个那么就会报错
              throw new Error('type is unknown')
            }
            this.type=type  //  type 等于你给我的type
         }
      }
   };
</script>

<style scoped lang="scss">
 .types {
      background-color: #c3c4c4;
      display: flex;
      text-align: center;
      font-size: 23px;

      > li {
         width: 49%;
         height: 63px;
         display: flex;
         justify-content: center;
         align-items: center;
         position: relative;


         &.selected::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 99%;
            height: 3px;
            background: #332;
         }

      }

   }
</style>