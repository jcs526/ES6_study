<template>
    <div>
        <table-component :table-data="tableData"></table-component>
        <div>{{turn}}님의 턴입니다.</div>
        <div v-if="winner">{{winner}}님의 승리!</div>
    </div>
</template>

<script>
import { mapState } from 'vuex';
import store from './store';
import TableComponent from './TableComponent';

    export default{
        store,
        components:{
                TableComponent,
        },

        data() {
            return {
                
            };
        },
        computed: {
          ...mapState(['tableData','winner','turn']),
          ...mapState({
            //   winner:state => state.winner,
            winner(state){
                return state.winner; // 이 안에 화살표함수는 this. 못쓰고 일반함수는 가능함
            },
              turnState:'turn'
          })
        },
        methods: {
            onChangeData(){
                this.$set(this.tableData[1],0,'X');
            },
           

        },
        
       
    }
</script>

<style>
  table {
    border-collapse: collapse;
  }
  td {
    border: 1px solid black;
    width: 40px;
    height: 40px;
    text-align: center;
  }
</style>