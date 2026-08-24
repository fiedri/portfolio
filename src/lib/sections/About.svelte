<script>
  import Skills from "./Skills.svelte";
  import "./about.css";
  let benefits = [
    {
      name: "Autodidacta",
      description:
        "Aunque estudio en la universidad, lo que más he aprendido ha sido por mi cuenta, haciendo proyectos reales, equivocándome y mejorando poco a poco.",
    },
    {
      name: "Apasionado por crear cosas útiles",
      description:
        "No programo por programar. Me gusta hacer cosas que realmente sirvan, aunque sean simples. Si puedo compartirlas con otros, mejor.",
    },
    {
      name: "Creativo",
      description:
        "Me gusta experimentar y darle mi toque a todo lo que hago. Ya sea una página de sorteos o una barbería falsa, siempre intento que se vea cool.",
    },
  ];

  let certificates = [
    {
      title: "Legacy Responsive Web Design",
      date: 2024,
      issuer: "freeCodeCamp",
      issuerLogo: "/certificates/logo.webp",
      verifyLink: "https://www.freecodecamp.org/certification/friedrichruiz/responsive-web-design",
    },{
      title: "Relational Databases",
      date: 2026,
      issuer: "freeCodeCamp",
      issuerLogo: "/certificates/logo.webp",
      verifyLink: "https://www.freecodecamp.org/certification/friedrichruiz/relational-database-v8",
    },
    {
      title: "Solana LATAM Builders Bootcamp",
      date: 2026,
      issuer: "Way Learn",
      issuerLogo: "https://images.seeklogo.com/logo-png/42/2/solana-sol-logo-png_seeklogo-423095.png",
      verifyLink: "/certificates/certificado_solana.png"
    },
    {
title: "Servicio Tecnico a equipos y usuario",
date: 2026,
issuer: "Universidad Politécnica Territorial de Falcón 'Alonso Gamero'",
issuerLogo: "",
verifyLink: "/certificates/certificacion_servicio_tecnico.jpeg"
    }
  ];
</script>

<section id="about" class="about-section">
  <div class="title-block">
    <h6 class="subtitle">¿Quieres saber más?</h6>
    <h3 class="title">
      Un poco <span class="highlight poppins">sobre</span> mí.
    </h3>
  </div>

  <p class="intro-text poppins">Soy . . .</p>

  <div class="benefits-list">
    {#each benefits as benefit, index}
      <div
        class="benefit-item"
        data-aos="zoom-in"
        data-aos-duration="1000"
        data-aos-once="true"
      >
        <p class="benefit-number poppins">0{index + 1}</p>
        <div class="benefit-text">
          <h3 class="benefit-name">
            {benefit.name}
          </h3>
          <p class="benefit-description">{benefit.description}</p>
        </div>
      </div>
    {/each}
  </div>
</section>
<Skills />
<section class="certificates-section">
  <h3 class="title">Certificados</h3>
  <div class="certificates-container">
    {#each certificates as certificate}
      <div class="certificate" data-aos="flip-up"
      data-aos-easing="ease-out-cubic"
    data-aos-duration="1000" data-aos-once="true">
        <div class="certificate-header">
          {#if certificate.issuerLogo}
            <div class="img-container">
            <img src={certificate.issuerLogo} alt="Logo del emisor" />
          </div>
          {/if}
          <div>
            <h4 class="certification-title {certificate.issuerLogo ? '' : 'whithour-logo'}">{certificate.title}</h4>
          </div>
        </div>
        <div class="separator"></div>
        <div class="certification-info">
          <p class="issuer poppins">{certificate.issuer}</p>
          <span class="date poppins">{certificate.date}</span>
          <a href="{certificate.verifyLink}" target="_blank" class="verify-link">
            <p class="verify-text">Verificar →</p>
          </a>
        </div>
      </div>
    {/each}
  </div>
</section>

<style>
  /* Si 'Poppins' no está importada globalmente, 
    deberías importarla al inicio de este <style> 
  */
  .poppins {
    font-family: "Poppins", sans-serif;
  }

  /* --- Contenedor Principal --- */
  .about-section {
    padding-top: 2.5rem;
    padding-bottom: 5rem;
    gap: 4rem; /* gap-16 */
  }
  .certificates-section {
    gap: 1rem;
    padding-bottom: 5rem;
  }
  .certificates-section,
  .about-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    padding-left: 1rem; /* px-4 */
    padding-right: 1rem;
    max-width: 80rem;
    margin-left: auto;
    margin-right: auto;
    color: white;
  }

  /* --- Bloque del Título --- */
  .title-block {
    display: flex;
    flex-direction: column;
    gap: 1rem; /* gap-4 */
    text-align: center;
    position: relative;
    width: 100%;

    padding-top: 2rem; /* py-8 */
    padding-bottom: 2rem;
    padding-left: 1rem; /* px-4 */
    padding-right: 1rem;
  }
  .title-block::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 66.6667%; /* w-2/3 */
    height: 0.375rem; /* h-1.5 */
    background-color: rgb(109 40 217); /* bg-violet-700 */
  }
  .title-block::after {
    content: "";
    position: absolute;
    bottom: 0;
    right: 0;
    width: 66.6667%; /* w-2/3 */
    height: 0.375rem; /* h-1.5 */
    background-color: rgb(109 40 217); /* bg-violet-700 */
  }

  .subtitle {
    font-size: 1.125rem; /* text-lg */
    line-height: 1.75rem;
    color: rgb(203 213 225); /* text-slate-300 */
    margin-bottom: 0.5rem; /* mb-2 */
  }

  .title {
    font-weight: 700;
    font-size: 2.25rem; /* text-4xl */
    line-height: 2.5rem;
    color: white;
    line-height: 1.25; /* leading-tight */
  }
  .title .highlight {
    color: rgb(139 92 246); /* text-violet-400 */
  }

  /* --- Texto Introductorio --- */
  .intro-text {
    margin-left: auto;
    margin-right: auto;
    font-weight: 600;
    font-size: 1.125rem; /* text-lg */
    line-height: 1.75rem;
  }

  /* --- Lista de Beneficios --- */
  .benefits-list {
    display: flex;
    flex-direction: column;
    gap: 5rem; /* gap-20 */
    width: 100%;
    margin-left: auto;
    margin-right: auto;
    max-width: 800px; /* max-w-[800px] */
  }

  .benefit-item {
    display: flex;
    gap: 1.5rem; /* gap-6 */
  }

  .benefit-number {
    font-size: 2.25rem; /* text-4xl */
    line-height: 2.5rem;
    color: rgb(100 116 139); /* text-slate-500 */
    font-weight: 600;
  }

  .benefit-text {
    display: flex;
    flex-direction: column;
    gap: 1.5rem; /* gap-6 */
  }

  .benefit-name {
    font-size: 1.5rem; /* text-2xl */
    line-height: 2rem;
    font-weight: 700;
  }

  .benefit-description {
    /* Estilos base para buena legibilidad */
    font-size: 1rem;
    line-height: 1.6;
    color: rgb(203 213 225); /* text-slate-300 (asumido) */
  }

  /* --- Media Queries (Puntos de quiebre de Tailwind) --- */

  /* sm: 640px */
  @media (min-width: 640px) {
    .about-section {
      gap: 5rem; /* sm:gap-20 */
      padding-left: 1.5rem; /* sm:px-6 */
      padding-right: 1.5rem;
    }
    .title-block {
      padding-left: 1.5rem; /* sm:px-6 */
      padding-right: 1.5rem;
    }
    .subtitle {
      font-size: 1.25rem; /* sm:text-xl */
      line-height: 1.75rem;
    }
    .title {
      font-size: 3rem; /* sm:text-5xl */
      line-height: 1;
    }
    .intro-text {
      font-size: 1.25rem; /* sm:text-xl */
      line-height: 1.75rem;
    }
    .benefit-item {
      gap: 2rem; /* sm:gap-8 */
    }
    .benefit-number {
      font-size: 3rem; /* sm:text-5xl */
      line-height: 1;
    }
    .benefit-text {
      gap: 2rem; /* sm:gap-8 */
    }
    .benefit-name {
      font-size: 1.875rem; /* sm:text-3xl */
      line-height: 2.25rem;
    }
  }

  /* md: 768px */
  @media (min-width: 768px) {
    .about-section {
      gap: 6rem; /* md:gap-24 */
      padding-left: 2rem; /* md:px-8 */
      padding-right: 2rem;
    }
    .title-block {
      padding-left: 2rem; /* md:px-8 */
      padding-right: 2rem;
    }
    .subtitle {
      font-size: 1.5rem; /* md:text-2xl */
      line-height: 2rem;
    }
    .title {
      font-size: 3.75rem; /* md:text-6xl */
      line-height: 1;
    }
    .intro-text {
      font-size: 1.5rem; /* md:text-2xl */
      line-height: 2rem;
    }
    .benefit-number {
      font-size: 3.75rem; /* md:text-6xl */
      line-height: 1;
    }
    .benefit-name {
      font-size: 3rem; /* md:text-5xl */
      line-height: 1;
    }
  }

  /* lg: 1024px */
  @media (min-width: 1024px) {
    .about-section {
      /* lg:py-32 anula lg:pt-16 y pt-10/py-20 */
      padding-top: 8rem; /* lg:py-32 */
      padding-bottom: 8rem; /* lg:py-32 */
    }
  }
</style>
