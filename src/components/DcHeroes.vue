<template>
  <div class="container">
    <h1 class="title-counter" v-if="heroesCount > 1">
      DC Heroes List with {{ heroesCount }} heroes
    </h1>
    <h1 v-else-if="!heroesCount">There is no Hero yet.</h1>

    <h1 v-else>DC Heroes List with {{ heroesCount }} hero</h1>

    <ul class="ul-list">
      <li class="list-items" v-for="(hero, index) in dcHeroes" :key="index">
        <div>
          {{ hero.name }}
        </div>
        <button class="delete-button" v-on:click="removeHero(index)">
          Delete
        </button>
      </li>
    </ul>
  </div>
  <div class="submit-section">
    <input
      class="hero-input"
      type="text"
      v-model="newHero"
      placeholder="Type your hero name"
      onfocus='this.placeholder=" "'
      onblur='this.placeholder="Type your hero name"'
    />

    <button class="submit-button" type="submit" v-on:click.prevent="addHero">
      Add a Hero
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isDisabled: true,
      newHero: "",
      dcHeroes: [
        { name: "SuperGirls" },
        { name: "Flash" },
        { name: "Batman" },
        { name: "Arrow" },
        { name: "Superman" },
      ],
    };
  },
  methods: {
    addHero() {
      if (this.newHero !== "") {
        this.dcHeroes.push({ name: this.newHero });
      }
    },
    removeHero(index) {
      this.dcHeroes = this.dcHeroes.filter((hero, i) => i !== index);
    },
  },
  computed: {
    heroesCount() {
      return this.dcHeroes.length;
    },
  },
};
</script>

<style></style>
