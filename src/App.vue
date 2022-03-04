<template>
    <div class="container-fuid">
      <div class="row ">
          <div class="col-1 m-2 position-fixed" style="z-index: 999999;">
            <MainMenu @changePage="changePageEvent"/>
          </div>
          <div class="col-1"></div>
          <div class="col-11">
            <PageController :page="page"/>
          </div>
      </div>
    </div>
</template>

<script>

import MainMenu from './components/MainMenu.vue'
import PageController from './components/PageController.vue'  

export default {
  
  name: 'App',
  
  data() {
    return {
      page:"clients"
    }
  },
  
  components: {
    MainMenu, PageController
  },
  
  methods: {
    changePageEvent(page){
      this.page = page;
    }
  }

}
</script>
