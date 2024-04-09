<script lang="ts">
  import { Ferias } from "@data";
  // import Modal from "@components/Modal.astro";

  type Feria = {
    id: number;
    title: string;
    descripcion: string;
    location: string;
    date: string;
    type: string;
    requirements: string[];
  };

  let query: string = "";
  let filteredFerias: Feria[] = Ferias;

  $: filteredFerias = Ferias.filter((feria: Feria) => feria.title.toLowerCase().includes(query.toLowerCase()));

  let selectedFeria: Feria | null = null;

  const handleRegister = (feria: Feria) => {
    selectedFeria = feria;
  };
</script>

<div class="search">
  <span><i class="ri-search-line"></i></span>
  <input type="search" placeholder="Buscar ferias..." bind:value={query} />
</div>

{#if filteredFerias.length === 0}
  <p>No se encontraron ferias de empleo</p>
{:else}
  <div class="job-fairs">
    {#each filteredFerias as feria}
      <div class="job-fair">
        <h2>{feria.title}</h2>
        <p>{feria.descripcion}</p>
        <p><strong>Lugar:</strong> {feria.location}</p>
        <p><strong>Fecha:</strong> {feria.date}</p>
        <p><strong>Tipo:</strong> {feria.type}</p>
        <strong>Requisitos:</strong>
        <ul>
          {#each feria.requirements as req}
            <li>{req}</li>
          {/each}
        </ul>
        <button class="register-btn">Registrarse</button>
      </div>
    {/each}
  </div>
{/if}

<style>
  .search {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 2.5rem;
  }

  .search span {
    margin-right: 0.4rem;
  }

  .search span i {
    font-size: 1rem;
    color: var(--dorado-900);
  }

  .search input {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid var(--verde-400);
    border-radius: 4px;
  }

  .search input:active {
    transform: scale(1.01);
    transition: transform 0.2s ease;
  }

  .search input:focus {
    outline: none;
    border-color: var(--dorado-700);
    box-shadow: 0 0 2px var(--verde-500);
    transition:
      border-color 0.2s ease,
      box-shadow 0.2s ease;
  }

  .job-fairs {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .job-fair {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: space-between;
    border: 1px solid var(--rojo-200);
    border-radius: 4px;
    padding: 1rem;
    transition:
      box-shadow 0.3s ease,
      transform 0.3s ease;
    overflow: hidden;
  }

  .job-fair h2 {
    text-align: center;
    font-size: 2rem;
    font-weight: bold;
    color: var(--dorado-900);
  }

  .job-fair ul {
    list-style-type: square;
    margin-left: 1rem;
  }

  .job-fair:hover {
    transform: translateY(-5px) scale(1.05);
    box-shadow: 0 8px 16px var(--dorado-700);
  }

  .register-btn {
    margin-top: 0.5rem;
    display: block;
    width: 100%;
    padding: 1rem;
    background-color: var(--verde-500);
    color: var(--blanco-50);
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .register-btn:hover {
    background-color: var(--dorado-700);
  }
</style>
