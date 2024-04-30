<script lang="ts">
	import WebDevSVG from '$lib/svg/webdev.svelte';
	import MoneySVG from '$lib/svg/money.svelte';
	import ServerSVG from '$lib/svg/server.svelte';
	import Support from '$lib/svg/support.svelte';
	import InformationSVG from '$lib/svg/information.svelte';

	export let nombre: string;
	export let trabajo: string;
	export let frase: string;
	export let imagenSrc: string;

	// Check SVG based on trabajo
	let SVGs: Record<string, any> = {
		Desarrollador: WebDevSVG,
		Finanzas: MoneySVG,
		Servidor: ServerSVG,
		Soporte: Support,
		Información: InformationSVG,
		// Add more SVGs as needed
	};
	let SVG = SVGs[trabajo] || WebDevSVG;
</script>

<div class="worker-card">
	<!-- Add an SVG container -->
	<div class="svg-container">
		<!-- Insert your SVG code here -->
		<SVG />
	</div>
	<div class="profile">
		<div class="image-container">
			<img src={imagenSrc} alt={nombre} />
		</div>
		<div class="info">
			<h2>{nombre}</h2>
			<p class="trabajo">{trabajo}</p>
			<br /><br />
			<p class="frase">"{frase}"</p>
		</div>
	</div>
</div>

<style>
	p {
		margin: 0;
	}

	.profile {
		display: flex;
		align-items: center;
		gap: 40px;
		z-index: 2;
	}

	.image-container {
		width: 150px;
		height: 150px;

		overflow: hidden;
		border: 2px solid black;
	}

	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.info {
		display: flex;
		flex-direction: column;
	}

	h2 {
		margin: 0;
	}

	.trabajo {
		font-style: italic;
		color: #8DECB4;
	}

	.frase {
		font-style: italic;
		color: #000000;
	}

	.worker-card {
		position: relative;
		border-radius: 8px;
		box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.9);
		background-color: #41b06e;
		padding: 20px;
		text-align: center;
		transition: 0.3s;
		max-width: 30rem;
		min-height: 8rem;
	}

	.worker-card:hover {
		transition: 0.3s;
		transform: scale(1.02);
	}

	/* Other style modifications as needed */
	h2 {
		font-family: 'Arial', sans-serif; /* Example font family */
	}

	:global(svg) {
		width: 5rem;
		height: 5rem;
		fill: #2e754b;
	}

	/* Style the SVG container */
	.svg-container {
		/* Adjust positioning as needed */
		position: absolute;
		bottom: 5px;
		right: 10px;
	}

	/* Media query for screens smaller than 600px (typical breakpoint for phones) */
@media (max-width: 600px) {
    .worker-card {
        max-width: 100%; /* Allow the card to take up the full width */
        padding: 10px; /* Reduce padding */
    }

    .profile {
        flex-direction: column; /* Stack the profile elements vertically */
        align-items: center; /* Center the profile elements */
        gap: 20px; /* Reduce gap */
    }

    .image-container {
        width: 100px; /* Reduce image size */
        height: 100px; /* Reduce image size */
    }

    :global(svg) {
        width: 3rem; /* Reduce SVG size */
        height: 3rem; /* Reduce SVG size */
    }

}
</style>
