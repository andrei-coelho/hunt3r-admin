<template>
    <div>
        <component v-bind:is="component" />
    </div>
</template>

<script>

import ListClients from './ListClients.vue'
import NewClient from './NewClient.vue'

export default {

    data() {
        return {
            component: ''
        }
    },

    props:{
        innerPage: String
    },

    methods: {
        changeInnerPage(){
            switch(this.innerPage){
                case "main":
                case "list":
                    this.component = ListClients;
                    break;
                case "new":
                    this.component = NewClient;
                    break;
            }
        }
    },

    mounted() {
        this.changeInnerPage()
    },

    watch: {
        'innerPage': function(){
            this.changeInnerPage()
        }
    }
}
</script>