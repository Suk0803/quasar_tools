<template>
  <q-page class="column flex-center">
    <div>
      <q-btn
        label="스톱워치"
        color="green"
        icon="timer"
        @click="onClickTimer()"
      />
      <q-btn label="카운트다운" color="green" @click="onClickCountDown()" />
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
const count = ref(0);

const $router = useRouter();
const min = -5;
const max = 5;

const onClickTimer = () => {
  $router.push('/stopwatch');
};

const onClickCountDown = () => {
  $router.push('/countdown');
};
</script>
