<template>
  <div>
    <div
      v-for="instrumento in instrumentosData"
      :key="instrumento.id"
      style="margin-top:15px"
      class="d-flex justify-content-center"
    >
      <instrumento-item :instrumentoParam="instrumento"></instrumento-item>
    </div>
  </div>
</template>

<script>
import Instrumento from "@/components/Instrumento.vue";

export default {
  name: "Productos",
  components: {
    "instrumento-item": Instrumento,
  },
  mounted() {
    this.getInstrumentos();
  },
  data() {
    return {
      instrumentosData: [],
    };
  },
  methods: {
    async getInstrumentos() {
      const res = await fetch("../fakeAPI/instrumentos.json");
      const resJson = await res.json();
      console.log(resJson.instrumentos);
      this.instrumentosData = resJson.instrumentos;
    },
  },
};
</script>
