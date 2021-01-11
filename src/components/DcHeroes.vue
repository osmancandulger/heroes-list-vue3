<template>
  <div class="m-auto">
    <h1 class="text-2xl text-center" v-if="heroesCount > 1">
      DC Heroes List with {{ heroesCount }} heroes
    </h1>
    <h1 class="text-2xl text-center" v-else-if="!heroesCount">
      There is no Hero yet.
    </h1>

    <h1 class="text-2xl text-center" v-else>
      DC Heroes List with {{ heroesCount }} hero
    </h1>

    <ul>
      <li
        class="flex justify-between"
        v-for="(hero, index) in dcHeroes"
        :key="index"
      >
        <div>
          {{ hero.name }} <button v-on:click="removeHero(index)">Delete</button>
        </div>
      </li>
    </ul>
    <input class="border-2" type="text" v-model="newHero" placeholder="Type" />

    <button class="border-2" type="submit" v-on:click.prevent="addHero">
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
