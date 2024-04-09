<script lang="ts">
  import { Empresas } from "@data";

  type Empresa = {
    id: number;
    RFC: string;
    nombre_empresa: string;
    encargado_RH: string;
  };

  let busqueda: string = "";
  let filteredEmpresas: Empresa[] = Empresas;

  $: filteredEmpresas = Empresas.filter((empresa: Empresa) =>
    empresa.nombre_empresa.toLowerCase().includes(busqueda.toLowerCase())
  );

  let selectedEmpresa: Empresa | null = null;

  function handleEmpresaSelection(empresa: Empresa) {
    selectedEmpresa = empresa;
  }
</script>

<div class="container">
  <h1>Empresas</h1>

  <div class="search">
    <span><i class="ri-search-line"></i></span>
    <input type="search" bind:value={busqueda} placeholder="Buscar empresa..." />
  </div>

  <table>
    <thead>
      <tr>
        <th>Nombre</th>
        <th>RFC</th>
        <th>Encargado de RRHH</th>
        <th>Acciones</th>
      </tr>
    </thead>
    <tbody>
      {#each filteredEmpresas as empresa}
        <tr>
          <td>{empresa.nombre_empresa}</td>
          <td>{empresa.RFC}</td>
          <td>{empresa.encargado_RH}</td>
          <td
            ><button type="button" class="btn primary-btn" on:click={() => handleEmpresaSelection(empresa)}
              >Más información</button
            ></td
          >
        </tr>
      {/each}
    </tbody>
  </table>
  <!-- Si le dan click al boton -->
</div>

<style>
  .container {
    max-width: 1024px;
    margin: 0 auto;
    padding: 2rem;
    height: auto;
  }

  h1 {
    text-align: center;
    font-size: 3.5rem;
    color: var(--dorado-900);
    margin-bottom: 2rem;
  }

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

  table {
    width: 100%;
    border-spacing: 0;
    border-collapse: collapse;
    border: 1px solid var(--dorado-300);
  }

  th,
  td {
    padding: 0.5rem;
    border: 1px solid var(--verde-700);
    color: var(--verde-600);
  }

  th {
    text-align: left;
    font-weight: bold;
    color: var(--dorado-800);
    font-size: 1.1rem;
  }

  .btn {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.2rem 0.6rem;
    border-radius: 0.5rem;
    border: none;
    cursor: pointer;
  }

  .primary-btn {
    background-color: var(--verde-500);
    color: var(--blanco-100);
    transition: background-color 0.3s ease;
  }
  .primary-btn:hover {
    background-color: var(--dorado-300);
    color: var(--blanco-100);
  }

  @media (max-width: 768px) {
    .container {
      padding: 0.3rem;
      height: auto;
      margin: 0 auto;
    }

    h1 {
      font-size: 2.5rem;
    }

    th {
      font-size: 0.95rem;
    }
  }
</style>
