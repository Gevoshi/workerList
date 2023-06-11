<!-- this component is List of worker  -->

<template>
    <div>
        <div v-if="workerList.length > 0">
            <h4>List of worker</h4>
            <worker-item 
            v-for="worker in workerList" 
            :key="worker.id"
            :worker="worker"
            @remove="$emit('remove', worker)"
            @showDialog="$emit('showDialog', worker)"
            />
        </div>

        <h3 v-else class="emptyText">Empty</h3>
    </div>

</template>

<script>
import WorkerItem from '@/components/WorkerItem.vue'
export default {
  components: { WorkerItem },
    props: {
        workerList: {
            type: Array,
            required: true
        }
    },
}
</script>

<style scoped>
.emptyText{
    color: brown;
}
</style>