<template>
  <q-page padding>
    <q-list bordered separator>
      <q-item>
        <q-tiem-section class="text-bold">스톱워치</q-tiem-section>
      </q-item>
      <q-item v-for="(time, time_index) in lap_times" :key="time_index">
        <q-tiem-section avatar>
          <q-chip color="red-5">{{ time_index + 1 }}</q-chip>
        </q-tiem-section>
        <q-tiem-section> {{ time }} </q-tiem-section>
      </q-item>

      <q-item>
        <q-tiem-section
          ><div class="text-h6">elapsed : {{ elapsed }}</div></q-tiem-section
        >
      </q-item>

      <q-item>
        <q-tiem-section
          ><q-btn label="시작" color="blue" @Click="startStopWatch()" />
          <q-btn label="멈춤" color="orange" @Click="stopStopWatch()" />
          <q-btn label="랩타임" color="green" @Click="recordLapTime()"
        /></q-tiem-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const abc = 0;
const elapsed = ref(0);
const isRun = ref(false);
let interval;
let started;

const lap_times = ref([]);

onMounted(() => {
  console.log('StopWatch onMounted');
});

onUnmounted(() => {
  stopStopWatch();
});

const startStopWatch = () => {
  if (isRun.value) {
  } else {
    isRun.value = true;
    elapsed.value = 0;
    started = new Date().getTime();
    interval = setInterval(() => {
      elapsed.value = (new Date().getTime() - started) / 1000;
    }, 10);
  }
};
const stopStopWatch = () => {
  if (interval != null)
    if (isRun.value) {
      clearInterval(interval);
      isRun.value = false;
    }
};

const recordLapTime = () => {
  lap_times.value.push(elapsed.value);
};
</script>
