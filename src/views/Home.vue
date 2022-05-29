<template>
  <div>
    <q-header bordered  class="bg-white">
      <div class="row">
        <div class="col-lg-1 col-md-1 col-sm-1 col-xs-1"></div>
        <div class="col-lg-10 col-md-10 col-sm-10 col-xs-10">
          <q-toolbar>
            <div class="q-pa-md">
              <img src="../assets/miko-logo.svg">
            </div>
            <div style="color:black;">
              Trello dashboard
            </div>
            <q-space />
            <div class="q-pa-md">
              <q-btn
                color="red"
                label="Byu Now"
                rounded
                no-caps
              />
            </div>
          </q-toolbar>
        </div>
        <div class="col-lg-1 col-md-1 col-sm-1 col-xs-1"></div>
      </div>
    </q-header>
    <q-page-container>
     <router-view />
    </q-page-container>
  </div>
</template>

<script>
export default {
 
  data() {
    return {
    };
  },
  methods:{
  },
};
</script>

<style lang="scss" scoped>
$blue-color:#ee6b6b;
$black-color:#f1e8ec;
</style>