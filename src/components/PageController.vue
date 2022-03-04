<template>
    <div>
        <div class="container-fluid position-fixed border-bottom py-2">
            <div class="row">
                <div class="col-10">
                    <!-- menu -->
                    <component v-bind:is="menuComponent" @changeInnerPage="changeInnerPageEvent"/>
                </div>
                <div class="col-2">
                    <!-- user -->
                    user
                </div>
            </div>
        </div>
        <div style="height: 80px;"></div>
        <component v-bind:is="mainComponent" :innerPage="innerPage"/>
    </div>
</template>

<script>

import MenuClient   from './pages/clients/MenuComp.vue';
import MainClient   from './pages/clients/MainComp.vue';
import MenuProfiles from './pages/profiles/MenuComp.vue';
import MainProfiles from './pages/profiles/MainComp.vue';
import MenuStats    from './pages/stats/MenuComp.vue';
import MainStats    from './pages/stats/MainComp.vue';
import MenuConfig   from './pages/config/MenuComp.vue';
import MainConfig   from './pages/config/MainComp.vue';

export default {

    components: {
        MenuClient, MainClient,
        MenuProfiles, MainProfiles,
        MenuStats, MainStats,
        MenuConfig, MainConfig
    },

    data() {
        return {
            mainComponent : "",
            menuComponent : "",
            innerPage: "main"
        }
    },

    props: {
        page: String
    },

    methods: {

        changeInnerPageEvent(inner){
            console.log(inner)
            
            this.innerPage = inner;
        },

        changePage(){

            switch(this.page) {
                case 'clients':
                    this.mainComponent = MainClient;
                    this.menuComponent = MenuClient;
                break;
                case 'profiles':
                    this.mainComponent = MainProfiles;
                    this.menuComponent = MenuProfiles;
                break;
                case 'stats':
                    this.mainComponent = MainStats;
                    this.menuComponent = MenuStats;
                break;
                case 'config':
                    this.mainComponent = MainConfig;
                    this.menuComponent = MenuConfig;
                break;
            }
        }

    },

    mounted() {
        this.changePage()
    },

    watch: {
        'page': function(){
            this.changePage()
        }
    }

}
</script>