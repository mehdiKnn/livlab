<template>
  <div id="container">
    <input id="search" type="text" v-model="search" placeholder="Search">
    <div v-if="filteredList.length > 0" class="sports" v-for="item in filteredList">
      {{item}}
    </div>
    <img v-else id="travolta" src="https://www.hyperui.dev/photos/confused-travolta.gif" alt="John Travolta confused">
  </div>
</template>

<script>
export default {
  name: 'App',
  data: function () {
    return {
      search: "",
      list: [
        "Décathlon (H)",
        "110m haies (F)",
        "4x400m (F)",
        "Poids (H)",
        "France - Slovénie (Basket H)",
        "Boxe - moins de 60 kg (F)",
        "Canoë-kayak - K1 200m (H)",
        "Omnium (H)",
        "Keirin (F) Demi-finales",
        "Australie - États-Unis (Football F)",
      ]
    }
  },
  computed: {
    filteredList: function () {
      return this.list.filter(item => {
       return this.cleanString(item).includes(this.cleanString(this.search))
      })
    }
  },
  methods:{
    cleanString(str){
      return str.normalize('NFD')
          .replace(/([\u0300-\u036f]|[^\da-zA-Z])/g, '').toLowerCase()
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Roboto');

body{
  font-family: "Roboto Light",sans-serif;
  margin: 0;
}
#container{
  max-width: 1024px;
  margin: auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}
#search{
  font-family: inherit;
  margin-top: 40px;
  margin-bottom: 30px;
  width: 50%;
  padding: 1rem;
  border: 1px solid white;
  border-radius: 5px;
  font-size: 15px;
  box-shadow: rgba(0, 0, 0, 0.05) 0 6px 24px 0, rgba(0, 0, 0, 0.08) 0 0 0 1px;
  font-weight: lighter;
}

.sports{
  font-size: 14px;
  font-weight: lighter;
  width: 40%;
  padding: 0.8rem;
  border: 1px solid white;
  border-radius: 5px;
  box-shadow: rgba(0, 0, 0, 0.05) 0 6px 24px 0, rgba(0, 0, 0, 0.08) 0 0 0 1px;
  margin-bottom: 10px;
  text-align: center;
}
#travolta{
  border-radius: 10px;
}
</style>
