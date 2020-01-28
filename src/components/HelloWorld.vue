<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>GEO APP</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-item>
      <ion-input type="search" v-model="research" @keyup.enter="startSearch"></ion-input>
    </ion-item>
    <ul>
      <li v-for="departement in departements" :key="departement.id">
        <p>{{departement.nom}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      research: "your departement",
      departements: []
    };
  },
  methods: {
    startSearch() {
      console.log(research);
    }
  },
  created: function() {
    axios
      .get("https://geo.api.gouv.fr/departements")
      .then(response => (this.departements = response.data));
  }
};
</script>