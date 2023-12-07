<template>
  <q-card bordered flat class="q-pa-md">
    <div class="text-grey text-bold">Manage Jobs</div>
    <div class="text-cyan-3 q-mt-md text-bold">
      <q-icon size="22px" name="work" class="q-mr-sm" />
      All Jobs
    </div>
    <div class="text-grey q-mt-md">
      <q-img class="q-mr-sm" width="10%" src="applied.svg" />
      My Applied Jobs
    </div>
    <div class="q-mt-md text-grey">
      <q-img class="q-mr-sm" width="10%" src="suggested-jobs.svg" />
      Suggestes Jobs
    </div>
  </q-card>
  <q-card flat bordered class="q-pa-md q-mt-md">
    <div class="text-grey text-center q-mt-sm size">See who's viewed your profile</div>
    <div class="text-center q-mt-md">
      <q-avatar size="94px" text-color="white" color="cyan-13">A</q-avatar>
      <div class="q-mt-md  text-bold color-text">Abdullah Ashraf</div>
    </div>
    <q-item class="text-grey q-mx-lg q-mt-md height-text">
      <q-item-section>Connections</q-item-section>
      <q-item-section side>0 </q-item-section>
    </q-item>
    <q-item class="text-grey q-mx-lg  height-text">
      <q-item-section>Views</q-item-section>
      <q-item-section side>0 </q-item-section>
    </q-item>
    <q-item class="text-grey q-mx-lg height-text">
      <q-item-section>Jobs Applied</q-item-section>
      <q-item-section side>0 </q-item-section>
    </q-item>
    <q-item class="text-grey q-mx-lg height-text">
      <q-item-section>Following</q-item-section>
      <q-item-section side>0 </q-item-section>
    </q-item>
    <div class="text-center q-my-md">
      <q-btn no-caps unelevated rounded class="q-px-xl" color="cyan-13" label="All Posts" />
    </div>
  </q-card>
  <q-card flat bordered class="q-pa-md q-mt-md">
    <div class="row">
      <div class="text-bold color-text"> Network Top Employers</div>
      <div class="q-ml-auto">
        <q-icon size="22px" name="arrow_back_ios" />
        <q-icon size="22px" name="arrow_forward_ios" />
      </div>
    </div>
    <div class="row q-col-gutter-lg q-mt-md">
      <div class="col-6">
        <q-card flat bordered class="q-pa-md">
          <q-img src="logo.png" />
        </q-card>
      </div>
      <div class="col-6">
        <q-card flat bordered class="q-pa-md">
          <q-img src="logo.png" />
        </q-card>
      </div>
      <div class="col-6">
        <q-card flat bordered class="q-pa-md">
          <q-img src="logo.png" />
        </q-card>
      </div>
      <div class="col-6">
        <q-card flat bordered class="q-pa-md">
          <q-img src="logo.png" />
        </q-card>
      </div>
    </div>
  </q-card>
</template>

<script>
export default {
  // name: 'ComponentName',
  data() {
    return {
    }
  }
}
</script>
<style scoped>
.size {
  font-size: 12px;
}

.color-text {
  color: #595959;
  font-size: 16px;
}

.height-text {
  min-height: 0px;
  padding: 0px;
}
</style>
