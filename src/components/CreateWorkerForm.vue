<!-- this component is form for creation worker  -->

<template>
  <form @submit.prevent>
    <h4>Create worker</h4>
    <MyInput
        type="text" 
        v-model="worker.name"
        placeholder="Name"
        :errorMessage="errorMessage"
        :error="showErrorMessageAboutName"
        :class="{'errorInput' : showErrorMessageAboutName}"/>
    <MyInput 
        type="text" 
        v-model="worker.surname"
        placeholder="Surname"
        :errorMessage="errorMessage"
        :error="showErrorMessageAboutSurname"
        :class="{'errorInput' : showErrorMessageAboutSurname}"/>
    <MyInput 
        type="number" 
        v-model="worker.experience"
        placeholder="Experience"
        :errorMessage="errorMessage"
        :error="showErrorMessageAboutExperience"
        :class="{'errorInput' : showErrorMessageAboutExperience}"/>
    <MyInput 
        type="number" 
        v-model="worker.age"
        placeholder="Age"
        :errorMessage="errorMessage"
        :error="showErrorMessageAboutAge"
        :class="{'errorInput' : showErrorMessageAboutAge}"/>
    <MyInput 
        type="text" 
        v-model="worker.address"
        placeholder="Address"
        :errorMessage="errorMessage"
        :error="showErrorMessageAboutAddress"
        :class="{'errorInput' : showErrorMessageAboutAddress}"/>
    <MyButton 
        type="submit"
        @click="checkInputValid"> Create
    </MyButton>
  </form>
</template>

<script>

export default {
    data: () => ({
        isValid: false,
        showErrorMessageAboutName: false,
        showErrorMessageAboutSurname: false,
        showErrorMessageAboutExperience: false,
        showErrorMessageAboutAge: false,
        showErrorMessageAboutAddress: false,
        errorMessage: '',
        worker: {
            name: "",
            surname: "",
            experience: "",
            age: "",
            address: "",
        },
    }),

    methods: {
        createWorker() {
            if (this.isValid){
                this.worker.id = Date.now();
                this.$emit("create", this.worker);
                this.worker = {
                    name: "",
                    surname: "",
                    experience: "",
                    age: "",
                    address: ""
                };
                this.isValid = false
            };
        },

        checkInputValid() {
            this.toDefault();
            this.$emit('checkInputValid');
            console.log('kanchvela');
            const { worker } = this;
            
            if(worker.name.trim() === '') {
                console.log('chi exel');
                this.errorMessage = 'name must contain at least one letter'
                this.showErrorMessageAboutName = true
            }
            else if(worker.surname.trim()  === ''){
                console.log('chi exel');
                this.errorMessage = 'surname must contain at least one letter'
                this.showErrorMessageAboutSurname = true
            }
            else if(worker.experience < 0 || worker.experience === ''){
                console.log('chi exel');
                this.errorMessage = 'enter valid value'
                this.showErrorMessageAboutExperience = true
            }
            else if(worker.age < 0 || worker.age === ''){
                console.log('chi exel');
                this.errorMessage = 'enter valid value'
                this.showErrorMessageAboutAge = true
            }
            else if(worker.address.trim() === ''){
                console.log('chi exel');
                this.errorMessage = 'The address should contain more information'
                this.showErrorMessageAboutAddress = true
            }

            else{
                console.log('stacvec');
                this.isValid = !this.isValid
                this.createWorker()
            }
        },

        toDefault(){
            this.showErrorMessageAboutName = false,
            this.showErrorMessageAboutSurname = false,
            this.showErrorMessageAboutExperience = false,
            this.showErrorMessageAboutAge = false,
            this.showErrorMessageAboutAddress = false,
            this.errorMessage = ''
        }

    },
}
</script>

<style>
    form{
        display: flex;
        flex-direction: column;
    }

    .errorInput{
        border-color: brown !important;
        
    }
    
</style>