<template>
	<section class="container">
<footer class="container__footer">
<span class="container__footer-motto">{{ motto }}</span>

</footer>

	</section>
</template>

<script>
export default {
	data() {
		return {
			motto: '@CartaDesign'
		}
	}
}
</script>

<style scoped>
.container {
	display: grid;
	grid-template-columns: var(--grid-column-12);
	grid-auto-rows: minmax(100px, auto);
	gap: 1rem;
	
}

.container__footer {
	display: grid;
	grid-column: 1/ span 12;
	background-color: #80a08a;
	height: 100px;
}


.container__footer-motto {
	grid-column: 1/ span 3;
	font-size: 2.5rem;
	color: rgb(97, 18, 25);
	grid-row: 1;
	padding-top: 10px;
	padding-left: 10px;
}

@media screen and (max-width: 1024px) {
.container__footer {
	height: 150px;
	margin-top: 70px;
}
}


</style>