<template>
  <div class="app">
    <MyDialog v-model:show="dialogVisible" class="inputChanger">
      <h3>Edit The Worker Parameters</h3>
      <my-input type="text" v-model="name"></my-input>
      <my-input type="text" v-model="surname"></my-input>
      <my-input type="number" v-model="experience"></my-input>
      <my-input type="number" v-model="age"></my-input>
      <my-input type="text" v-model="address"></my-input>
      <div class="changeSaver">
        <MyButton @click="saveChanged" > Save </MyButton>
      </div>
    </MyDialog>
    <create-worker-form
      @create="createWorker"/>
    <worker-list 
      :workerList="workerList"
      @remove="removeWorker"
      @showDialog="showDialog"
      @saveChanged="saveChanged"/>
  </div>
</template>

<script>
import CreateWorkerForm from '@/components/CreateWorkerForm.vue';
import WorkerList from '@/components/WorkerList.vue';
import MyInput from './components/Ui/MyInput.vue';

export default {

  components: {
    CreateWorkerForm,
    WorkerList,
    MyInput
  },
  data:() => ({
    // standard worker template
    workerList: [
      {id:1, name: 'John', surname: 'Smith', experience: 1, age: 25, address: 'England, London'},
      {id:2, name: 'Ali', surname: 'Yilmaz', experience: 3, age: 22, address: 'Turkey, Stambul'},
      {id:3, name: 'Anna', surname: 'Jackson', experience: 5, age: 30, address: 'Usa, Miami'}
    ],
    dialogVisible: false,
    name: '',
    surname: '',
    experience: '',
    age: '',
    address: '',
    id: '',

  }),

  methods: {
    createWorker(worker){
      this.workerList.push(worker)
    },

    removeWorker(worker){
      this.workerList = this.workerList.filter(w => w.id !== worker.id)
    },

    showDialog(worker){
            this.dialogVisible = true,
            this.name = worker.name,
            this.surname = worker.surname,
            this.experience = worker.experience,
            this.age = worker.age,
            this.address = worker.address,
            this.id = worker.id
        },
    
    saveChanged(){
      const editableWorker = this.workerList.find(worker => worker.id === this.id)
      editableWorker.name = this.name,
      editableWorker.surname = this.surname,
      editableWorker.experience = this.experience,
      editableWorker.age = this.age,
      editableWorker.address = this.address,
      this.dialogVisible = false

    }
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .app{
    width: 100%;
    padding: 15px;
  }

  .inputChanger {
    display: flex;
    justify-content: center;
    align-items: center;

  }

  .changeSaver{
    display: flex;
    justify-content: end;
  }
</style>