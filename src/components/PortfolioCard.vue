<script>
import { store } from "../store";

export default {
  data() {
    return {
      store,
    };
  },
  props: {
    objPortfolio: {
      type: Object,
      required: true,
    },
  },
  methods: {
    getImageUrl(image) {
      return image
        ? this.store.baseUrl + "storage/" + image
        : this.store.baseUrl + "storage/default.png";
    },
  },
};
</script>
<template>
  <div class="card h-100">
    <img
      :src="getImageUrl(objPortfolio.image)"
      class="card-img-top h-100"
      :alt="objPortfolio.name"
    />
    <div class="card-body d-flex flex-column">
      <h5 class="card-title">Titolo: {{ objPortfolio.name }}</h5>
      <p class="card-text">Data di Consegna: {{ objPortfolio.deploy_date }}</p>
      <router-link
        :to="{ name: 'portfolios.show', params: { id: objPortfolio.id } }"
        class="btn btn-primary mt-auto"
        >View</router-link
      >
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
