<template>
      <div class="dashboard-wrapper">
        <div class="dashboard">
            <h3>Dashboard</h3>
        </div>
        <!-- <div class="filter">
            <Filter :tasks="tasks" @filter="filteredCards"/>
        </div> -->
        <div class="cards">
            <div :key="task.id" v-for="task in data">
                <Card :task="task" @update="update"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import  getData  from "../../data/data";
import Card from '../utils/card.vue';

export default defineComponent({
    props:['task'],
    components:{Card},
    setup () {
        const data = getData();
        const filteredTasks = ref(data);
        function update(id:string, labels:Array<string>){
            // console.log(id, labels);
            for (var i=0; i<data.length; i++){
                if(data[i].id === id){
                    data[i].labels = labels;
                    // console.log(data[i].labels);
                    filteredTasks.value = data;
                }
            }
        }
    
        return {data, update, filteredTasks}
    }
})
</script>

<style scoped>
.dashboard-wrapper{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.filter{
    width:60%;
    margin-top:2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 2rem;
}
.cards{
    width:75%;
    display: grid;
    gap: 4rem 30px ;
    grid-template-columns: repeat(3, 25vw);
    box-sizing: border-box;
    margin:0 auto;
    margin-bottom:7rem;
    align-items: center;
}
</style>