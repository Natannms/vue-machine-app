<template>
  <div class="flex flex-col justify-center justify-items-center">
    <h2 class="text-white">{{ textQuestion }}</h2>
    <div class="button flex justify-around p-2 mt-1 rounded">
      <span
        class="material-icons hover:text-orange-500 text-white"
        @click="playMusic"
      >
        play_circle_outline
      </span>
      <span
        class="material-icons hover:text-orange-500 text-white"
        @click="pauseMusic"
      >
        pause_circle_outline
      </span>
      <span
        class="material-icons hover:text-orange-500 text-white"
        @click="stopMusic"
      >
        stop_circle_outline
      </span>
      <span
        class="material-icons hover:text-orange-500 text-white"
        @click="changeMusic"
      >
        skip_next
      </span>
    </div>
    <button
      @click="stopMusic"
      class="button flex justify-around text-bold p-2 mt-1 rounded hover:bg-white hover:text-green-500 bg-green-500 text-white"
    >
      I'm satisfied
    </button>
    <!-- Reprodução simples de áudio -->
    <audio
      id="audio-console"
      src="https://fine.sunproxy.net/file/amFTNk5XaXpPU1o0VU5aMGRtZHdGQzludkVzbnU0UFNER2J0R0gyVG45NjZuQlZhUVVnR3JwdGR4Z21xQWtBeU4rUFFSbXV2ZkY3SkROMVhyMG0zeTg0RlZwRTZTWlBvbEN0REJZRE5Xb1E9/Marvin_Gaye_-_Let_s_Get_It_On_(BornMP3.com).mp3"
      controls
    >
      O seu navegador não suporta o elemento <code>audio</code>.
    </audio>
  </div>
</template>

<script>
export default {
  name: "Question2",
  data: function () {
    return {
      AudioConsole: document.getElementById("audio-console"),
      satisfiedWithTheMusic: false,
      currentMusic: 0,
      textButton: "Start our music",
      textQuestion: "Start the music for our moment",
      music: [
        {
          name: "01",
          url:
            "https://fine.sunproxy.net/file/amFTNk5XaXpPU1o0VU5aMGRtZHdGQzludkVzbnU0UFNER2J0R0gyVG45NjZuQlZhUVVnR3JwdGR4Z21xQWtBeU4rUFFSbXV2ZkY3SkROMVhyMG0zeTg0RlZwRTZTWlBvbEN0REJZRE5Xb1E9/Marvin_Gaye_-_Let_s_Get_It_On_(BornMP3.com).mp3",
        },
      ],
    };
  },
  methods: {
    changeMusic() {
      alert(this.music[this.currentMusic].url);
      this.AudioConsole.src = this.music[this.currentMusic].url;
    },
    playMusic() {
      let AudioConsole = document.getElementById("audio-console");
      this.textQuestion = "Do you like this music for our environment?";
      AudioConsole.play();
    },
    pauseMusic() {
      let AudioConsole = document.getElementById("audio-console");
      AudioConsole.pause();
    },
    stopMusic() {
      let AudioConsole = document.getElementById("audio-console");
      AudioConsole.pause();
      AudioConsole.currentTime = 0;
    },
    checkSatisfied() {
      if (!this.satisfiedWithTheMusic) {
        const newMusic = this.currentMusic + 1;
        let AudioConsole = document.getElementById("audio-console");
        this.currentMusic = newMusic;
        AudioConsole.src = newMusic;
        setTimeout(() => {
          this.stopMusic();
          this.playMusic();
        }, 2000);
      }
    },
  },
};
</script>

<style>
.button {
  width: 400px;
}
.InputName {
  width: 400px;
}
</style>