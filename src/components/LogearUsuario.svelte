<script>
  let curp;
  let password;

  async function handleSubmit(event) {
    event.preventDefault();

    const UserData = { curp, password };

    try {
      const url = 'https://tu-dominio.com/api/login';
      const response = await fetch(url, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(UserData)
      });

      const data = await response.json();

      if (response.ok) {
        console.log('Inicio de sesión exitoso');
        const token = data.token; // Obtener el token de autenticacion
        window.localStorage.setItem('token', token);
        window.location.href = '/';
      } else {
        console.error('Error en el inicio de sesión: ', data.error);
      }
    } catch (error) {
      console.error('Error en la solicitud: ', error);
    }
  }
</script>


<div class="container">
  <h1>Iniciar Sesión</h1>
  <form on:submit={handleSubmit}>
    <div>
      <label for="curp">CURP:</label>
      <input type="text" id="curp" bind:value={curp} required />
    </div>
    <div>
      <label for="password">Contraseña:</label>
      <input type="password" id="password" bind:value={password} required />
    </div>
    <div class="btn">
      <button type="submit">Inicia sesión</button>
    </div>
    <div class="links">
      <p>¿Olvidaste tu contraseña? <a href="/reset-password">Recuperala</a><p>
      <p>¿No tienes cuenta? <a href="/register">Registrate</a></p>
    </div>
  </form>
</div>


<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    max-width: 800px;
    margin: 0 auto;
    padding: 2rem;
    height: 45rem;

  }

  h1 {
    text-align: center;
    font-size: 3.5rem;
    color: var(--dorado-900);
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
    font-weight: bold;
    color: var(--verde-500);
  }

  input{
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

  .btn {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 2rem;
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
      padding: 3rem;
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
    }

    input {
      order: 1;
      width: 100%;
    }

    button[type='submit'] {
      padding: 1rem 2rem;
    }
  }
</style>
