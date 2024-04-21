<script>
  let curp;
  let rfc;
  let fechaNacimiento;
  let nombre;
  let paterno;
  let materino;
  let sexo;
  let clave_Estado;
  let clave_Ciudad;
  let calle;
  let clave_Colonia;
  let cp;
  let telefono;
  let password;

  async function handleSubmit(event) {
    event.preventDefault();

    const userData = {
      curp,
      rfc,
      fechaNacimiento,
      nombre,
      paterno,
      materino,
      sexo,
      clave_Estado,
      clave_Ciudad,
      calle,
      clave_Colonia,
      cp,
      telefono,
      password
    };

    const url = 'https://tu-domino.com/api/register';
    try {
      const response = await fetch(url, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(userData)
      });

      const data = await response.json();

      if (response.ok) {
        console.log('Registro exitoso');
        window.location = '/'
      } else {
        console.error('Error en el registro: ', data.error);
      }
    } catch (error) {
      console.error('Error en la solicitud: ', error);
    }
  }
</script>

<div class="container">
  <h1>Registro</h1>
  <form on:submit={handleSubmit}>
    <div>
      <label for="curp">CURP:</label>
      <input type="text" id="curp" bind:value={curp} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="rfc">RFC:</label>
      <input type="text" id="rfc" bind:value={rfc} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="nombre">Nombre:</label>
      <input type="text" id="nombre" bind:value={nombre} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="paterno">Apellido Paterno:</label>
      <input type="text" id="paterno" bind:value={paterno} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="materino">Apellido Materno:</label>
      <input type="text" id="materino" bind:value={materino} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="sexo">Género:</label>
      <select name="sexo" id="sexo" bind:value={sexo} required>
        <option value="">Selecciona una opción</option>
        <option value="masculino">Masculino</option>
        <option value="femenino">Femenino</option>
        <option value="otro">Otro</option>
      </select>
    </div>
      <!-- Terminación de label y Select -->
      <!-- Terminación de label y input -->
    <div>
      <label for="clave_Estado">clave_Estado:</label>
      <input type="text" id="clave_Estado" bind:value={clave_Estado} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="clave_Ciudad">clave_Ciudad:</label>
      <input type="text" id="clave_Ciudad" bind:value={clave_Ciudad} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="calle">Dirección:</label>
      <input type="text" id="calle" bind:value={calle} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="clave_Colonia">clave_Colonia:</label>
      <input type="text" id="clave_Colonia" bind:value={clave_Colonia} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="cp">Código Postal:</label>
      <input type="text" id="cp" bind:value={cp} required />
    </div>
    <!-- Terminación de label y input -->
    <div>
      <label for="telefono">Teléfono:</label>
      <input type="text" id="telefono" bind:value={telefono} required />
    </div>
      <!-- Terminación de label y input -->
    <div>
      <label for="password">Contraseña:</label>
      <input type="text" id="password" bind:value={password} required />
    </div>
      <!-- Terminación de label y input -->
      <!-- Botón de submit -->
      <div class="button">
        <button type="submit">Registrarse</button>
      </div>
      <div class="links">
        <p>¿Ya tienes cuenta? <a href="/login">Inicia sesión</a></p>
        <p>¿Olvidaste tu contraseña? <a href="/reset-password">Recuperala</a><p>
      </div>
  </form>
</div>


<style>
  .container {
    max-width: 800px;
    margin: 0 auto;
    padding: 2rem;
    height: auto;
  }

  h1 {
    text-align: center;
    font-size: 3.5rem;
    /* color: var(--verde-700); */
    color: var(--dorado-900);
  }

  form {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
    place-items: center;
  }

  label {
    font-weight: bold;
    color: var(--verde-500);
  }

  input,
  select {
    padding: 0.5rem;
    border: 1px solid var(--verde-400);
    border-radius: 4px;
  }

  input:active {
    transform: scale(1.05);
    transition: transform 0.2s ease;
  }

  input:focus {
    outline: none;
    border-color: var(--dorado-700);
    box-shadow: 0 0 2px var(--verde-500);
    transition: border-color 0.2s ease, box-shadow 0.2s ease;
  }

  select:active {
    transform: scale(1.05);
    transition: transform 0.2s ease;
  }

  select:focus {
    outline: none;
    border-color: var(--dorado-700);
    box-shadow: 0 0 2px var(--verde-500);
    transition: border-color 0.2s ease, box-shadow 0.2s ease;
  }
  .button {
    margin-top: 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  button[type='submit'] {
    padding: 1rem 4rem;
    background-color: var(--verde-500);
    color: var(--blanco-50);
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  button[type='submit']:hover {
    background-color: var(--dorado-700);
  }

  .links {
    margin-top: 2rem;
  }
  .links p {
    text-align: center;
    font-size: 0.8rem;
  }
  .links a {
    text-align: center;
    margin-top: 0.5rem;
    color: var(--verde-500);
    transition: text-decoration 0.3s ease, color 0.3s ease;
  }

  .links a:hover {
    text-decoration: none;
    color: var(--dorado-700);
  }

  @media (max-width: 768px) {
    .container {
      max-width: 400px;
      margin: 0 auto;
      padding: 4rem;
    }

    h1 {
      font-size: 3rem;
      /* margin-bottom: 0.5rem; */
    }

    form {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }

    form > div {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    label {
      order: 2;
      width: 100%;
      /* margin-top: 4rem; */
    }

    input, select {
      order: 1;
      width: 100%;
    }

    .button {
      margin-top: 2rem;
    }

    button[type='submit'] {
      padding: 1rem 2rem;
    }
  }
</style>