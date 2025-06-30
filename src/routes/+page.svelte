<script>
  import { goto } from '$app/navigation';
  import { onDestroy } from 'svelte';

  export let data;

  let nameInput = data.name || '';
  let timeout;

  function handleInput(e) {
    clearTimeout(timeout);
    const value = e.target.value.trim();

    timeout = setTimeout(() => {
      if (value) {
        // Atualiza a URL com o novo nome
        goto(`/?name=${encodeURIComponent(value)}`, { replaceState: true });
      } else {
        // Limpa se input estiver vazio
        goto(`/`, { replaceState: true });
      }
    }, 1000);
  }

  onDestroy(() => clearTimeout(timeout));
</script>

<style>
  .container{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }

  .container .card{
    background-color: #343a40;
    padding: 1rem;
    border-radius: 1rem;
    width: 380px;
    box-sizing: border-box;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.6);
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }

  .container .card:hover{
    transform: translateY(-4px);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.7);
  }

  .container .card .input-wrapper{
    position: relative;
    width: 300px;
    margin: 2rem auto;
  }

  .container .card .input-wrapper label{
    position: absolute;
    top: -10px;
    left: 10px;
    color: #adb5bd;
    background: #343a40;
    padding: 0 6px;
    font-size: 0.875rem;
    pointer-events: none;
    transition: 0.2s ease;
    z-index: 2;
  }

  .container .card .input-wrapper .border-animation {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border-radius: 8px;
    padding: 3px;
    background: linear-gradient(270deg, #4fc3f7, #ff6ec4, #4fc3f7);
    background-size: 600% 600%;
    animation: neon-border 6s linear infinite;
    z-index: 0;
    mask: 
      linear-gradient(#fff 0 0) content-box, 
      linear-gradient(#fff 0 0);
    mask-composite: exclude;
    -webkit-mask-composite: destination-out;
  }

  @keyframes neon-border {
    0% { background-position: 0% 50%; }
    100% { background-position: 100% 50%; }
  }

  .container .card .input-wrapper .inputBox{
    padding: 1.2rem 1rem 0.6rem;
    background: transparent;
    border: none;
    border-radius: 8px;
    color: #f8f9fa;
    font-size: 1rem;
    position: relative;
    z-index: 1;
    outline: none;
    box-shadow: none;
    width: 90%;
  }
  .container .card .msg{
    margin-top: 2rem;
    color: #f0f0f0;
    text-align: center;
  }
  .container .card .msg-error{
    margin-top: 2rem;
    color: #FF6B6B;
    text-align: center;
  }

.container {
  --s: 16px; /* control the size*/
  --c1: #212529;
  --c2: #282b2e;
  
  --_l: #0000 46%,var(--c1) 47% 53%,#0000 54%;
  background:
    radial-gradient(100% 100% at 100% 100%,var(--_l)) var(--s) var(--s),
    radial-gradient(100% 100% at 0    0   ,var(--_l)) var(--s) var(--s),
    radial-gradient(100% 100%,#0000 22%,var(--c1) 23% 29%, #0000 30% 34%,var(--c1) 35% 41%,#0000 42%),
    var(--c2);
  background-size: calc(var(--s)*2) calc(var(--s)*2);
}

</style>

<div class="container">

  <div class="card">
    <div class="input-wrapper">
      <input
        class="inputBox"
        type="text"
        placeholder=""
        bind:value={nameInput}
        on:input={handleInput}
      />
      <label for="nome">Seu Nome</label>
      <span class="border-animation"></span>
    </div>
  
    {#if data.age !== null}
      <p class="msg">Idade estimada para "{data.name}": <strong>{data.age}</strong> anos</p>
    {:else if data.name === ''}
      <p class="msg">Digite um nome e descubra sua idade estimada.</p>
    {:else}
      <p class="msg-error">Nenhum resultado encontrado.</p>
    {/if}
  </div>
</div>
