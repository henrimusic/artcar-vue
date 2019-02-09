<template>
    <b-list-group-item href="#" v-on:click="counter += 1" class="d-flex justify-content-between align-items-center">
        {{ marca }}
        <b-badge variant="primary" pill>{{ quantidade }}</b-badge>
    </b-list-group-item>
</template>


<script>
export default {

    data(){
        return {counter : 0};
    },

    props:['marca', 'quantidade']

}
</script>