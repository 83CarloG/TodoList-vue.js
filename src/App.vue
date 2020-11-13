<template>
<div class="container p-5">
  <div class="row">
    <div class="col-md-6 text-center offset-md-3 ">
      <h1>DC Heroes #{{ herosCount }}</h1>
      <div>

      <ul class="list-group text-left p-3"> 
        <li class="list-group-item" :key="index" v-for="(hero, index)  in dcHeroes">{{ hero.name   }}</li>
      </ul>
      <form @submit.prevent="addHero">
        <input v-model="newHero" placeholder="Type hero name here">
        <button type="submit">Add Hero</button>
      </form>
      </div>
    </div>
  </div>
</div>  
</template>

<script>
export default {
  data () {
    return {
      newHero: "",
      dcHeroes: [
        { name: "Supergirl"},
        { name: "SuperMan"},
        { name: "Batman"},
        { name: "Flash"},
        { name: "Aquaman"},
      ],
    };
  },
  methods:{
    addHero() {
      !(this.newHero) ?  "" : this.dcHeroes.unshift({ name: this.newHero}); 
      this.newHero = ""; 
    },
    remove() {

    }
  },
  computed: {
    herosCount() {
      return this.dcHeroes.length
    }
  }

};
</script>

<style>

</style>