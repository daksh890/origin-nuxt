<template>
      <div class="card">
        <div class="img">
            <img :src="task.img"/>
        </div>
        <div class="tags" v-if = "flag">
            <div class="tag" v-for="(tag, index) in labels" :key="index">
                <div>{{tag}}</div>
            </div>
        </div>

        <div class="new" v-else>
            <div class="input">
                <input type="text" placeholder="Enter new tag" v-model="newtag"/>
                <button @click="changelabels">Add</button>
            </div>
            <div class="curr-tags">
                <div class="tag" v-for="(tag, index) in labels" :key="index">
                    <div @click="updatelabels(tag)">{{tag}}</div>
                </div>
            </div>
        </div>

        <div class="button">
            <button @click="$emit('update', task.id, labels), flag=!flag">Update</button>
        </div>
    </div>
</template>


<script setup lang="ts">
    const props = defineProps({
        task:Object as PropType<Card>|any
    })
    const task:Ref<Card> = toRef(props, "task");
        const labels = ref(task.value.labels);
        const flag = ref(true);
        const newtag = ref("");
        
        const changelabels = function(){
            if(newtag.value != ""){
                labels.value = [...labels.value, newtag.value];
            }
           
        };
        const updatelabels = function(tag:String){
            var newlabels = labels.value.filter((item:String)=> {
                    return item != tag;
                })
            labels.value = newlabels;
            
        };
</script>

<style scoped>
    .card{
    width:15vw;
    height:22rem;
    background-color: beige;
    border:2px solid black;
    margin:1rem;
    display: flex;
    flex-direction: column;
}
.img{
    height:60%;
    object-fit: cover;
}
img{
    height:100%;
    width:100%;
}
.tags, .new{
    margin:0.5rem;
    height:30%;
}
.new{
    display: flex;
    flex-direction: column;
}
.input input{
    width:60%;
    margin-right: 0.5rem;
}
.tag{
    display:inline-block;
    margin-right:0.5rem;
    background-color: cadetblue;
    border-radius: 20px 20px;
    padding:0.2rem 0.5rem;
}

.button{
    align-self: flex-end;
    display: flex;
    margin:1rem;
}

button{
    background: black;
    color:white;
    align-self:flex-end;
    padding:0.5rem;
    border-radius: 50px;
    cursor:pointer;

}
.curr-tags{
    cursor:pointer;
}


</style>