<template>
  <div class="container">
    <h1>Countdown Timer</h1>
    <h2>Created by Seth Davila</h2>
    <input type="number" v-model="timeInput" placeholder="Enter seconds (1-60)" min="1" max="60" />
    <button @click="startTimer">Start Timer</button>
    <div id="timerDisplay">{{ timerDisplay }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timeInput: '',
      seconds: 0,
      timerDisplay: '00:00',
      countdown: null,
    };
  },
  methods: {
    startTimer() {
      this.seconds = parseInt(this.timeInput);
      if (isNaN(this.seconds) || this.seconds < 1 || this.seconds > 60) {
        alert('Please enter a number between 1 and 60.');
        return;
      }

      if (this.countdown) {
        clearInterval(this.countdown); 
      }

      this.countdown = setInterval(() => {
        this.timerDisplay = `00:${this.seconds < 10 ? '0' : ''}${this.seconds}`;
        if (this.seconds <= 0) {
          clearInterval(this.countdown);
          alert("Time's up!");
          this.timerDisplay = '00:00';
        } else {
          this.seconds--;
        }
      }, 1000);
    },
  },
};
</script>



