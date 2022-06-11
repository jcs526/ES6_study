<template>
    <td @click="onClickTd">{{ cellData }}</td>
</template>

<script>
import EventBus from './EventBus';
export default {
    props: {
        cellData: String,
        rowIndex: Number,
        cellIndex: Number,
    },
    data() {
        return {

        }
    },
    methods: {
        onClickTd() {
            if (this.cellData) return;
            console.log("됨?")
            EventBus.$emit('clickTd',this.rowIndex,this.cellIndex)
        }
    },
}

</script>


<style>
td {
    width: 20px;
    height: 20px;
}
</style>