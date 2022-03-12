<template>
<section class="container">
 <header class="container__header">
 <img class="container__header-logo" src="/images/logo.png" alt="">

 <span class="container__header-title">{{ title }}</span>
  
	</header>	
</section>

</template>


<script>
export default {
	data() {
		return {
       title: 'DrInk App'
		  
		}
	},
}
</script>

<style scoped>
.container {
	display: grid;
	grid-template-columns: var(--grid-column-12);
	grid-auto-rows: minmax(100px, auto);
	gap: 1rem;
	
}

.container__header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  background-color: #80a08a;
  grid-column: 1/ span 12;
  display: grid;
  height: 210px;
  /* padding-top: 10px; */
  /* margin-bottom: 5px; */
}

.container__header-title {
	grid-column: 2/ span 3;
	font-size: 3rem;
	color: rgb(97, 18, 25);
	box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
	grid-row: 1;
	padding-top: 40px;
	font-family:cursive;
	background: rgb(199, 116, 68);
	width: 385px;
	height: 114px;
	border-radius: 50%;
	line-height: 1.6rem;
	margin: 45px 5px;
	text-align: center;
	
}
.container__header-logo {
	transition: transform 1s ease-in-out;
	grid-column: 1/ span 2;
	grid-row: 1;
	width: 50%;
}

.container__header-logo:hover {
		transform: rotateZ(360deg);
	}




</style>