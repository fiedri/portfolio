<script lang="ts">
  import FeaturedProjects from "../../components/FeaturedProjects.svelte";

  let project = [
    {
      categories: ["Full Stack", "Web application"],
      name: "Anime Beats",
      image: "/web_apps/animeBeats.png",
      description: "Plataforma de streaming de OP/ED",
      tags: ["SvelteKit", "GraphQL", "MongoDB"],
      link: "https://animebeats.netlify.app/",
      github: "https://github.com/fiedri/AnimeBeats"
    },
    {
      categories: ["UI/UX & Frontend", "Web application"],
      name: "BarberHero",
      image: "/web_apps/barber_hero.png",
      description: "Landing page para barbería moderna",
      tags: ["JavaScript", "Svelte", "CSS"],
      link: "https://barberhero.netlify.app/",
      github: "https://github.com/fiedri/barberHero.git"
    },
    {
      categories: ["Web application"],
      name: "Pokédex",
      image: "/web_apps/pokedex.png",
      description: "Explorador de información Pokémon",
      tags: ["JavaScript", "HTML", "CSS"],
      link: "https://pokephiexd.netlify.app/",
      github: "https://github.com/fiedri/pokedex.git"
    },
    {
      categories: [],
      name: "#ROOT-BLOCKER",
      image: "/snapshot.png",
      description: "Extensión para bloquear sitios web y Palabras clave",
      tags: ["JavaScript", "extension"],
      github: "https://github.com/fiedri/root-blocker.git",
      link: ""
    },
    {
      categories: [],
      name: "Monitor Bcv",
      image: "/monitor_bcv.png",
      description: "Bot de Telegram para monitorear el precio del dólar en Venezuela",
      tags: ["nodejs", "Telegram Bot"],
      github: "https://github.com/fiedri/Monitor_bcv_bot.git",
      link: ""
    },
    {
      categories: [],
      name: "Web Scraper for MyAnimeList",
      Image: "/web_scraper.png",
      description: "Web scraper para extraer información de OPs/EDs de MyAnimeList",
      tags: ["nodejs", "web scraping"],
      github: "https://github.com/fiedri/web_scraping_for_animeBeats",
      link: ""
    },{
      categories: [],
      name: "Motor de recomendación de anime",
      image: "/recommender_system.png",
      description: "Sistema de recomendación de anime basado en similitud de contenido",
      tags: ["nodejs", "algorithms"],
      github: "https://github.com/fiedri/anime_recomendation_motor.git",
      link: ""
    },
    {
      categories: [],
      name: "#ROOT-DARK-MODE",
      description: "Tema oscuro para vs code",
      image: "/ex"
      tags: ["vs code", "extension"],
      github: "https://github.com/fiedri/ROOT-Dark-mode-vscode.git",
      link: "https://marketplace.visualstudio.com/items?itemName=fiedri.root-dark-theme"
    }
  ];

  let fullWA = project.filter(p => p.categories.some(c => ["Full Stack", "Web application"].includes(c)));
  
</script>

<div class="projects-page-container">
  <FeaturedProjects projects={fullWA} title="Full Stack y aplicaciones web"/>
  <!-- <FeaturedProjects projects={uiUxProjects} title="UI/UX & Frontend"/> -->
</div>

<style>
  .projects-page-container {
    padding-top: 80px;
    padding-bottom: 100px;
    min-height: 100vh;
  }
</style>
