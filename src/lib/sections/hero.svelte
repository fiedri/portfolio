<script>
  import { fly } from "svelte/transition";
  import { typewriter } from "../typewriter";
  import { onMount } from "svelte";
  let show = $state(false);
  onMount(() => {
    show = true;
  });
</script>

<section id="introPage">
  <div class="margin" in:fly={{ y: 20, duration: 600, delay: 200 }}>
    {#if show}
      <h2 transition:typewriter={{ speed: 0.3 }}>
        Soy <span class="poppins highlight">Friedrich Ruiz</span><br />
        <span class="poppins highlight">Desarrollador</span> Web
      </h2>
    {/if}
    <p class="text poppins">
      Hago cosas geniales usando <span style="color: #f7df1e;">JavaScript</span
      >,
      <span style="color: #ff3e00;">SvelteKit</span>,
      <span style="color: #68a063;">Node.js</span>
      y
      <span style="color: #4db33d;">Sql</span>
    </p>

    <div class="btn-container">
      <a
        href="/Friedrich_Ruiz-Curriculum.pdf"
        download="Friedrich_Ruiz-Curriculum.pdf"
        class="poppins download-button btn"><i class="fa-solid fa-download" style="margin-right: 5px;"></i>CV</a
      >
      <a
        href="mailto:ruizlopezfriedrichjavier@gmail.com"
        target="_blank"
        class="contact-button poppins btn"
      >
        Contactame &rArr;
      </a>
    </div>
  </div>
  {#if show}
    <div class="img-container" in:fly={{ y: 50, duration: 700, delay: 500 }}>
      <img src="foto.webp" alt="profile of Friedrich Ruiz" />
    </div>
  {/if}
</section>

<style>
  .poppins {
    font-family: "Poppins", sans-serif;
  }

  /* --- Estilos base (Desktop-first) --- */
  section {
    display: grid;
    min-height: 100vh;
    align-items: center;
    grid-template-columns: 1fr auto;
    grid-template-rows: 1fr;
    gap: 10px;
    padding: 10px;
    margin: 0 75px;
  }

  .margin {
    /* Era .text-content */
    display: flex;
    flex-direction: column;
    justify-content: center; /* lg:justify-center */
    text-align: left; /* lg:text-left */
    gap: 2.3rem; /* lg:gap-10 */
    color: white;
  }

  .margin h2 {
    font-weight: 600; /* font-semibold */
    font-size: 3.75rem; /* md:text-6xl (Tomado como base) */
    line-height: 1.1;
  }

  .highlight {
    color: #8b5cf6; /* text-violet-400 */
  }

  .text {
    font-size: 1.25rem;
    font-weight: 600;
  }
.btn{
    padding: 12px 24px;
    border-radius: 9999px;
text-decoration: none;

    transition: all 0.3s ease;
    align-self: flex-start;
    font-size: 1.1rem;
    text-transform: uppercase;
    font-weight: 600;
}
  .download-button {
    background-color: #632fdd;
    
    color:  white;
  }
  .contact-button {
    margin: 0;
    background-color: white;
    color: black;

  }
  .contact-button:hover {
    background-color: #632fdd;
    color: white;
    transform: translateY(-3px);
  }

  .img-container {
    position: relative;
    display: grid;
    place-items: center;
    max-height: 50vh;
    aspect-ratio: 1 / 1;
    border-radius: 9999px;
    box-shadow: 0 20px 40px -10px rgb(139 92 246 / 0.5);
    background-color: rgb(15 23 42); /* bg-slate-900 */
    padding: 1rem; /* p-4 */
    overflow: hidden;
  }

  .img-container img {
    object-fit: cover;
    z-index: 2;
    width: 100%;
    height: 100%;
    aspect-ratio: 1 / 1;
    border-radius: 9999px;
  }
.btn-container{
display: flex;
flex-direction: row;
gap: 1.25rem;
}

  @media (width < 800px) {
    section {
      grid-template-columns: 1fr;
      grid-template-rows: auto auto;
      align-items: center;
      margin: auto;
      justify-items: center;
      overflow: hidden;
      min-height: auto;
      margin: 60px 0;
      padding: 40px 20px;
    }
    .btn-container{
    justify-content: center;
    align-items: center;
    }

    .img-container {
      width: 250px;
      overflow: hidden;
    }

    .text {
      margin: 0 20px;
      font-size: 1.125rem;
      text-align: center;
    }

    .margin {
      text-align: center;
      gap: 1.5rem;
    }
    .download-button{
    margin: auto;
    }

    .margin h2 {
      font-size: 3rem;
    }

    .contact-button {
      align-self: center;
    }
    #introPage {
      gap: 20px;
    }
  }

  @media (width < 640px) {
    .margin h2 {
      font-size: 2.25rem;
    }
    .text {
      font-size: 1rem;
    }
    .btn-container{
    flex-direction: column-reverse;
    justify-content: center;
    align-items: center;
    }
  }
</style>

