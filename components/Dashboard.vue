<template>
      <div class="dashboard-wrapper">
        <div class="dashboard">
            <h3>Dashboard</h3>
        </div>
        <div class="filter">
            <Filter @filter="filteredCards"/>
        </div>
        <div class="cards">
            <div :key="task.id" v-for="task in filteredTasks">
                <Card :task="task" @update="update"/>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
    
    import  getData  from "./../data/data";
    import { useArrayFilter } from '@vueuse/core';
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

    function filteredCards(category:string){
        var filterTag:string="";
        if (category =="" || category == "all"){
            filteredTasks.value = data;
        }else{
            filterTag=category;
            filteredTasks.value = useArrayFilter(data, (item)=>{
                let tags = item.labels.some((label) => {
                        return label === filterTag;
                })
                // console.log(tags);
                return tags;
            }).value;
        }
    }
    
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