<template>
<div class="container p-5">
  <div class="row">
    <div class="col-md-6 text-center offset-md-3 hero__title rounded">
      <h1 class="hero__count">DC Heroes #{{ herosCount }}</h1>
      <div>

      <ul class="list-group text-left p-3"> 
        <li class="list-group-item d-flex align-items-center justify-content-between " :key="index" v-for="(hero, index)  in dcHeroes">
          <div class="align-self-center">
          {{ hero.name }}
          </div>
          <div class="d-flex align-items-center justify-content-between">
          <span class="m-1 badge badge-pill badge-success"><i class="fas fa-info"></i></span>
          <span class="m-1 badge badge-pill badge-warning"><i class="far fa-edit"></i></span>
          <span class="m-1 badge badge-pill badge-danger" @click="remove(index)"><i class="far fa-trash-alt"></i></span>
          </div>
        </li>
      </ul>
      <form @submit.prevent="addHero" class="flex-column ">
        <div>
        <input v-model="newHero" placeholder="Type hero name here">
        </div>
        <div>
        <button type="submit" class="btn btn-outline-light m-2">Add Hero</button>
        </div>
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
    remove(index) {
      
      this.dcHeroes = this.dcHeroes.filter((hero,i) => i != index);
    }
  },
  computed: {
    herosCount() {
      return this.dcHeroes.length
    }
  }

};
</script>

<style lang="scss">
.hero {
  &__title {
    background-color: rebeccapurple;
    padding: 10px;
  }
  &__count {
    color: #339966 !important;
  }
}
.fas, .far {
  color: #fff ;
  font-size: 14px;
} 
</style>