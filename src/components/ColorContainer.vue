<template>
  <v-container class="color-container">
    <div class="color-row">
      <div v-for="(color, index) in colors" :key="index" class="color-col" @click="copyColorCode(color)">
        <v-card :style="{ background: color }" class="color-card">
          <v-card-text>{{ color }}</v-card-text>
        </v-card>
      </div>
    </div>
  </v-container>
</template>

<script>
export default {
  props: {
    colors: Array,
  },
  methods: {
    copyColorCode(color) {
      navigator.clipboard.writeText(color);
      this.$emit('copied', color);
      window.alert(`カラーコード ${color} がコピーされました`);
    },
  },
};
</script>

<style scoped>
.color-container {
}

.color-row {
  display: flex;
  flex-wrap: wrap;
  margin: 0 -10px;
}

.color-col {
  flex-basis: calc(33.33% - 20px);
}

.color-card {
  cursor: pointer;
  color: #ffffff;
  font-family: "Arial Black";
  height: 200px;
  aspect-ratio: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

@media screen and (max-width: 768px) {
  .color-col {
    flex-basis: calc(50% - 20px);
  }
}

@media screen and (max-width: 480px) {
  .color-col {
    flex-basis: calc(100% - 20px);
  }
}
</style>
