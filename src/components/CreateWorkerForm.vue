<!-- this component is form for creation worker  -->

<template>
  <form @submit.prevent>
    <h4>Create worker</h4>
    <MyInput
        type="text" 
        v-model="worker.name"
        placeholder="Name"/>
    <MyInput 
        type="text" 
        v-model="worker.surname"
        placeholder="Surname"/>
    <MyInput 
        type="number" 
        v-model="worker.experience"
        placeholder="Experience"/>
    <MyInput 
        type="number" 
        v-model="worker.age"
        placeholder="Age"/>
    <MyInput 
        type="text" 
        v-model="worker.address"
        placeholder="Address"/>
    <MyButton 
        @click="createWorker"> Create
    </MyButton>
  </form>
</template>

<script>

export default {
    data: () => ({
        worker: {
            name: "",
            surname: "",
            experience: "",
            age: "",
            address: ""
        }
    }),
    methods: {
        createWorker() {
            this.worker.id = Date.now();
            this.$emit("create", this.worker);
            this.worker = {
                name: "",
                surname: "",
                experience: "",
                age: "",
                address: ""
            };
        }
    },
}
</script>

<style scoped>
    form{
        display: flex;
        flex-direction: column;
    }


</style>