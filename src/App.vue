<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import BaseSelect from "./components/BaseSelect.vue";
import axios from "axios";
import { store } from "./store";

export default {
  data() {
    return {
      store,
      apiUri: "https://db.ygoprodeck.com/api/v7/cardinfo.php",
      archetypeUri: "https://db.ygoprodeck.com/api/v7/archetypes.php",
    };
  },

  components: { AppHeader, AppMain, BaseSelect },

  methods: {
    fetchCards(endpoint) {
      axios.get(endpoint).then((response) => {
        store.cards = response.data.data;
      });
    },

    fetchArchetype(termination) {
      axios.get(termination).then((response) => {
        store.archetypes = response.data;
      });
    },

    handleSelect(selected) {
      const archPoint = `${this.apiUri}?archetype=${selected}`;
      this.fetchCards(archPoint);
    },
  },

  created() {
    this.fetchCards(this.apiUri);
    this.fetchArchetype(this.archetypeUri);
  },
};
</script>

<template>
  <AppHeader />

  <div class="container">
    <BaseSelect
      :options="store.archetypes"
      :placeHolder="'Choose an ArcheType'"
      @change-select="handleSelect"
    />
  </div>
  <AppMain />
</template>

<style lang="scss">
@use "./assets/general.scss";
</style>
