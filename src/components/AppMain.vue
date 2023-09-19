<script>
import CardsList from "./CardList.vue";

export default {
  components: { CardsList },
};
</script>

<template>
  <main class="container">
    <div class="box mt-4">
      <SelectedCount />
      <CardsList />
    </div>
  </main>
</template>

<style lang="scss" scoped>
@use "../../src/assets/general.scss" as *;
@use "../../src/assets/partials/variables" as *;

main {
  .box {
    background-color: $text-color;
    padding: 2rem 3rem;
  }
}
</style>
