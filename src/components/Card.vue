<script>
export default {
  props: {
    name: String,
    archetype: String,
    image: String,
  },
};
</script>

<template>
  <div class="cols">
    <img :src="image" alt="" class="card-img" />
    <div class="caption">
      <h3 class="caption-name">{{ name }}</h3>
      <p class="c-type">{{ archetype || "Undefined" }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "../assets/general.scss" as *;
@use "../assets/partials/variables" as *;
.card-img {
  max-width: 100%;
}
.caption {
  padding: 0.7rem;
  height: 100px;
  background-color: $bg-color;
  text-align: center;
  .caption-name {
    color: $text-color;
    font-size: 1rem;
    font-weight: 800;
  }
}
</style>
