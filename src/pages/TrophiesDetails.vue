<template>
	<v-ons-page>
		<v-ons-toolbar>
      <div class="left">
        <v-ons-back-button>Retour</v-ons-back-button>
      </div>
    </v-ons-toolbar>
	   <v-card>
		   <v-ons-card v-for="trophy in trophies">
		    <img v-if="trophy.obtenu" :src="'./trophees/' + trophy.path" style="width:100%">
		    <img v-else :src="'./trophees/' + trophy.path" style="opacity:0.2; width:100%">
		    <br>
		    <center v-if="trophy.obtenu">
		    	{{ trophy.name }}
		    </center>
		    <center v-else>
		    	<v-ons-icon icon="fa-lock"></v-ons-icon>
		    	{{ trophy.name }}
		    </center>
		   </v-ons-card>
		</v-card>
	</v-ons-page>

</template>

<script>

export default {
  data() {
    return {

    }
  },
  computed : {
    trophies() {
    	return this.$store.state.user.trophies
    },
    tropheesObtenus() {
    	var res = 0
    	for (let i = 0; i < this.trophies.length; i++) {
    		if (this.trophies[i].obtenu) res++
    	}
    return res
    }
  },
  methods : {
  	displayTrophy(index) {
  		console.log(JSON.stringify(this.trophies[index]))
  	}
  }
}

</script>