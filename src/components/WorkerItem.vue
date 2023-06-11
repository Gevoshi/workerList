<template>
  <div>
        <div class="workerList">
            <div>
                <div><strong>Name : </strong>{{ worker.name }}</div>
                <div><strong>Surname : </strong>{{ worker.surname }}</div>
                <div><strong>Experience : </strong>{{ worker.experience + ' year' }}</div>
                <div><strong>Age : </strong>{{ worker.age }}</div>
                <div><strong>Address : </strong>{{ worker.address }}</div>
            </div>
            <div class="buttonBox">
                <MyButton 
                    class="btn edit" 
                    @click="$emit('showDialog', worker)">
                        <i class="fa-solid fa-pen-to-square"></i>
                </MyButton>
                <MyButton 
                    class="btn delete" 
                    @click="$emit('remove', worker)">
                        <i class="fa-solid fa-trash"></i>
                </MyButton>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    props: {
        worker: {
            type: Object,
            required: true
        }
    },
}
</script>

<style scoped>
     .workerList{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 15px;
        border: 2px solid teal;
        margin-top: 15px;
        border-radius: 12px;

    }

    .buttonBox{
        display: flex;
        flex-direction: column;
        gap: 10px;
    }

    .btn {
        font-size: 15px !important;
        margin-top: 0 !important;
        padding: 0 !important;
        width: 30px !important;
        height: 30px !important;
    }

    .edit:hover{
        color: blue !important;
        border-color: blue !important;
    }

    .delete:hover{
        color: brown !important;
        border-color: brown !important;
    }

</style>