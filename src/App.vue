<template>
  <div class="allset">
  <h1 class="h1">おとなしめの色ランダムジェネレーター</h1>
  <v-container>
    <ColorContainer :colors="colors" @copied="showCopiedMessage" />
    <div>
    <v-btn class="mt-4 custom-btn" @click="generateColors" color="primary">更新</v-btn>
    </div>
  </v-container>
  </div>
</template>

<script>
import ColorContainer from "./components/ColorContainer.vue";

export default {
  components: {
    ColorContainer,
  },
  data() {
    return {
      colors: [],
    };
  },
  mounted() {
    this.generateColors();
  },
  methods: {
    generateRandomColor() {
      const letters = "0123456789ABCDEF";
      let color = "#";
      for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
    },
    generateColors() {
      const colors = Array.from({ length: 9 }, () => this.generateRandomColor());
      this.colors = colors;
    },
  },
};
</script>
<style scoped>
.custom-btn {
  background-color: #0c7588;
  color: #ffffff;
  border-radius: 8px;
  padding: 12px 24px;
  font-size: 16px;
  transition: background-color 0.3s ease;

  &:hover {
    background-color: #28afaa;
  }
}
.h1 {
  font-size: 32px;
  color: #a1cbc9;
  font-weight: bold;
  margin-bottom: 16px;
  font-family: "Arial Black";
}
.allset {
  background-color: #23232a;
  color: #cdcdde;
}
</style>