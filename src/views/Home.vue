<template>
  <Header />
	  <main>
	   <div class="container__main" v-for="drink in cocktails" :key="drink.id">
		  <div class="container__main-title">{{ drink.strDrink}}</div>
		  <div class="container__version">VErsion:<br>{{ drink.strAlcoholic }}</div>
		  <div class="container__category">CatEgory:<br>{{ drink.strGlass }}</div>
		  <img class="container__main-image" :src=image>
		 <div class="container__main-description">DESCRIPTION:<br>
	    {{ drink.strInstructions}}</div>
		<ul class="container__list">
		  <li class="container__list-title">Ingredients:</li>
		  <li class="container__main-list">{{ drink.strMeasure1 }}, {{ drink.strIngredient1 }}</li>
		  <li class="container__main-list">{{ drink.strMeasure2 }}, {{ drink.strIngredient2 }} </li>
		  <li class="container__main-list">{{ drink.strMeasure3 }}, {{ drink.strIngredient3 }}</li>
		  <li class="container__main-list">{{ drink.strMeasure4 }} {{ drink.strIngredient4 }} </li>
		  <li class="container__main-list">{{ drink.strMeasure5 }} {{ drink.strIngredient5 }} </li>
		  <li class="container__main-list">{{ drink.strMeasure6 }} {{ drink.strIngredient6 }} </li>
		  <li class="container__main-list">{{ drink.strMeasure7 }} {{ drink.strIngredient7 }}</li>
	   </ul>
      <button class="container__main-button" @click="fetchDrinks">Try a new drink</button>
     </div>
	</main>
  <Footer />
	
</template>

<script>
	import Header from '../components/Header.vue';
	import Footer from '../components/Footer.vue';
	export default {
		components: {
			Header,
			Footer
		},
	data() {
		return {
		  error: '',
		  image: '',
		  cocktails: [],
		}
	},
	created() {
		this.fetchDrinks();

	},
	methods: {
		async fetchDrinks() {
      const url = 'https://www.thecocktaildb.com/api/json/v1/1/random.php';
		const response = await fetch(url); 
		try {
			await this.handleResponse(response)
		} catch(error) {
			console.log(error)
			this.error = error;
		}
	},
	async handleResponse(response) {
			if(response.status >= 200 && response.status < 300)  {
				console.log('it works');
		const { drinks }  = await response.json();
		this.cocktails = drinks;
		this.image = drinks[0].strDrinkThumb	
		return true; 
		} else {
				if(response.status === 404) {
					throw new Error('Url is not right');
				}
				if(response.status === 500) {
					throw new Error('server not working!');
				}
				} 
				throw new Error ('oh, no! something went wrong')
	}
		}
	}
</script>

<style scoped>

	.container__main-title {
		text-align: center;
		font-size: 2rem;
		font-weight: 300;
		margin: 1rem;
		color: rgb(90, 21, 30);
		position: absolute;
		right: 210px; 
		
	}

	.container__category {
		background: rgb(199, 116, 68);
		box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
		width: 320px;
		height: 130px;
		border-radius: 50%;
		text-align: center;
		position: absolute;
		line-height: 2rem;
		font-size: 1.5rem;
		font-weight: 300;
		top: 440px;
		right: 190px;
		padding-top: 15px;
	}

	.container__version {
		background: rgb(199, 116, 68);
		box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
		width: 320px;
		height: 130px;
		border-radius: 50%;
		text-align: center;
		line-height: 2rem;
		font-size: 1.5rem;
		font-weight: 300;
		position: absolute;
		top: 290px;
		right: 170px;
		padding-top: 20px;
	}

	.container__main-image {
		margin: 25px 5px 0px 390px; 
		width: 400px;
		height: 400px;
	}

	.container__main-description {
		font-family: cursive;
		line-height: 1.6;
		font-size: 1.3rem;
		margin: 15px 15px 15px 390px;
		
	}
	.container__list-title {
		font-weight: bold;
		margin-bottom: 5px;
	}


	.container__list {
		background: rgb(199, 116, 68); 
		width: 220px;
		height: 300px;
		list-style: none;
		margin: 30px 0px 30px 100px;
		font-size: 1.2rem;;
		line-height: 1.5rem; 
		position: absolute;
		top: 450px;  
		left: 50px; 
		padding: 10px;
	} 

	.container__main-button {
		padding: 20px;
		border: 1px solid #80a08a;
		background-color: #80a08a;
	   border-radius: 30px;
		width: 350px;
		margin: 10px 10px 25px 420px;
		font-size: 1.6rem;
		box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
		color: rgb(70, 16, 24);
	}

	.container__main-button:hover {
		color: rgb(53, 8, 15);
		background-color: rgb(199, 116, 68);
	}
    /* small and medium devices */
	@media screen and (max-width: 1024px) {
		.container__title-list {
			margin-left: 0px;
		}
		.container__main-image {
			margin: 180px 0px 20px 15px;
		}
		.container__main-description {
			font-size: 1.4rem;
			margin-left: 20px;
		}
		.container__list {
			line-height: 2rem;
			font-size: 1.6rem;
			height: 440px;
			width: 250px;
			margin: 950px 20px 20px 600px;
		} 
		.container__main-title {
			right: 350px;
			margin-top: 100px;
			font-size: 3rem;
		}
		.container__main-image {
			width: 100%;
			height: 700px;
			margin: 200px 10px 20px 10px;
		}
		.container__main-button {
			width: 500px;
			padding: 25px;
			margin: 700px 100px 10px 250px;
			font-size: 2rem;

		} 
		.container__category {
			top: 1700px;
			left: 120px;
			width: 350px;
			height: 200px;
			padding-top: 45px;
			font-size: 2rem;
			line-height: 2.6rem;
		}
		.container__version {
			top: 1450px;
			left: 120px;
			width: 350px;
			height: 200px;
			padding-top: 45px;
			font-size: 2rem;
			line-height: 2.6rem;
		}
	}
</style>

