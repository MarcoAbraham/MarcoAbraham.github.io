<script>
	import Worker from '$lib/components/Worker.svelte';
	import persona1 from '$lib/images/p1.jpg';
	import EmmaFoto from '$lib/images/emma.png';
	import IvanFoto from '$lib/images/ivan.jpg';
	import MarcosFoto from '$lib/images/marcos.jpg';
	import GabrielFoto from '$lib/images/gabriel.jpg';

	const teamData = [
		{
			image: GabrielFoto,
			name: 'Gabriel Gayón Bello',
			job: 'Desarrollador',
			phrase: 'Dueño de 10 carros.'
		},
		{
			image: persona1,
			name: 'Victor Manuel López',
			job: 'Finanzas',
			phrase: 'Doy dinero y ya'
		},
		{
			image: MarcosFoto,
			name: 'Marco Abraham Gallardo Hernández',
			job: 'Servidor',
			phrase: 'no se que poner'
		},
		{
			image: IvanFoto,
			name: 'Ivan Fierro Molina',
			job: 'Soporte',
			phrase: 'A veces, me gusta cocinar'
		},
		{
			image: EmmaFoto,
			name: 'Emmanuel Garnica Solano',
			job: 'Información',
			phrase: 'La información.'
		}
	];
</script>

<h1 class="title">¿Quiénes Somos?</h1>

<div class="team-grid">
	{#each teamData as member}
		<Worker
			imagenSrc={member.image}
			nombre={member.name}
			trabajo={member.job}
			frase={member.phrase}
		/>
	{/each}
</div>

<style>
	.title {
		text-align: center;
		font-size: 3em;
		margin-bottom: 20px;
	}

	.team-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 20px;
		justify-content: center;
		align-items: center;
		margin: 10rem;
	}

	/* Media query for screens smaller than 600px (typical breakpoint for phones) */
	@media (max-width: 600px) {
		.team-grid {
			grid-template-columns: 1fr; /* Change to a single column layout */
			margin: 2rem; /* Reduce margin */
		}
	}
</style>
