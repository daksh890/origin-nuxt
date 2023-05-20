<template>
    <div class="signin">
        <div class="head">
            Sign In
        </div>
        <div class="form">
            <form @submit="handleSubmit">
                <div>
                    <p>Email</p>
                    <input type="email" required placeholder="abc@daksh.com" v-model="email"/>
                </div>
                <div>
                    <p>Password</p>
                    <input type="password" required placeholder="password" v-model="password"/>
                </div>
                <div>
                    <button type="submit">Submit</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import { NavigateToItem } from 'typescript';

export default defineComponent({
    name:"SignIn",
    setup () {
        const email = ref("");
        const password = ref("");

        const handleSubmit = (e:Event) => {
            e.preventDefault();
            console.log(email.value, password.value);
            navigateTo("/dashboard");
        }

        return {
            email, password, handleSubmit
        }
    }
})
</script>

<style scoped>
.signin{
    width:20%;
    display:flex;
    flex-direction: column;
    align-items: center;
    text-align: left;
    /* background-color: aliceblue; */
    margin:0 auto;
    background-color: rgb(221, 223, 224);
    box-sizing: border-box;
}
.head{
    font-size: 1.2rem;
    font-weight: 700;
}
form div{
    margin-bottom: 1rem;
    display: flex;
    flex-direction: column;
    width:100%;
    align-items: center;
    text-align: left;
}
form div p{
    font-size: 1rem;
    margin-bottom: 0.5rem;
    align-self: flex-start;
}
form div input{
    border:0.5px solid black;
    border-radius: 20px;
    padding:0.5rem 1rem;
    background: transparent;
    width:100%;
}
button{
    padding:0.5rem 1rem;
    width:15vw;
    background-color: black;
    color:white;
    border-radius: 20px;
}

</style>