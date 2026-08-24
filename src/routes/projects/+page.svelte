<script lang="ts">
  import FeaturedProjects from "../../lib/components/FeaturedProjects.svelte";

  let project = [
    {
      categories: ["Full Stack", "Web application"],
      name: "Anime Beats",
      image: "/web_apps/animeBeats.webp",
      description: "Streaming de música de anime",
      tags: ["SvelteKit", "GraphQL", "MongoDB"],
      link: "https://animebeats.netlify.app/",
      github: "https://github.com/fiedri/AnimeBeats"
    },
    {
      categories: ["Full Stack", "Web application"],
      name: "#ROOT Indexer",
      image: "/web_apps/root_indexer.webp",
      description: "Tu segundo Cerebro para recursos de codigo",
      tags: ["Supabase", "v0"],
      link: "https://v0-root-indexer-build.vercel.app/",
      github: "https://github.com/fiedri/v0-root-indexer-build"
    },
    {
      categories: ["Frontend", "Web application"],
      name: "BarberHero",
      image: "/web_apps/barber_hero.webp",
      description: "Landing page para barberías",
      tags: ["JavaScript", "Svelte", "CSS"],
      link: "https://barberhero.netlify.app/",
      github: "https://github.com/fiedri/barberHero.git"
    },
    {
      categories: ["Frontend", "Web application"],
      name: "Spotify Clone",
      image: "/web_apps/spotify_clone.webp",
      description: "Clon de Spotify con reproducción de música",
      tags: ["SvelteKit", "TypeScript", "Tailwind"],
      link: "https://clone-spo-friedrich.netlify.app/",
      github: "https://github.com/fiedri/spotify_clone"
    },
    {
      categories: ["Frontend", "Web application"],
      name: "Pokédex",
      image: "/web_apps/pokedex.webp",
      description: "Buscador de Pokémon con PokeAPI",
      tags: ["JavaScript", "HTML", "CSS"],
      link: "https://pokephiexd.netlify.app/",
      github: "https://github.com/fiedri/pokedex.git"
    },
    {
      categories: ["Utilities", "Browser Extension"],
      name: "Root Blocker",
      image: "/extensions/root_blocker.png",
      description: "Bloqueador de sitios y palabras",
      tags: ["JavaScript", "extension"],
      github: "https://github.com/fiedri/root-blocker.git",
      link: "/extensions/root_blocker.png"
    },
    {
      categories: ["Telegram Bot", "Automation"],
      name: "Monitor BCV",
      image: "/monitor_bcv.webp",
      description: "Precio del dólar en tiempo real",
      tags: ["nodejs", "Telegram", "Bot"],
      github: "https://github.com/fiedri/Monitor_bcv_bot.git",
      link: "/monitor_bcv.webp"
    },
    {
      categories: ["CLI Tool", "Web Scraping"],
      name: "MAL Scraper",
      image: "/cli/web_scrapper1.png",
      description: "Extractor de datos musicales",
      tags: ["nodejs", "web scraping"],
      github: "https://github.com/fiedri/web_scraping_for_animeBeats",
      link: "/cli/web_scrapper1.png"
    },
    {
      categories: ["CLI Tool", "Algorithms"],
      name: "Anime Engine",
      image: "/cli/arm.webp",
      description: "Sugerencias basadas en gustos",
      tags: ["nodejs", "algorithms"],
      github: "https://github.com/fiedri/anime_recomendation_motor.git",
      link: "/cli/arm.webp"
    },
    {
      categories: ["Utilities", "VS Code Extension"],
      name: "Root Dark",
      description: "Tema oscuro para programadores",
      image: "/extensions/dark_mode.webp",
      tags: ["vs code", "extension"],
      github: "https://github.com/fiedri/ROOT-Dark-mode-vscode.git",
      link: "https://marketplace.visualstudio.com/items?itemName=fiedri.root-dark-theme"
    },
    {
      categories: ["Games", "Web application"],
      name: "Snake Game",
      description: "Clásico Snake en JavaScript",
      image: "/web_apps/cyberWhorm.webp",
      tags: ["JavaScript", "game"],
      github: "https://github.com/fiedri/Juego-snake.git",
      link: "https://cyberworm.netlify.app/"
    },
    // {
    //   categories: [],
    //   name: "Emoji Panel",
    //   description: "Panel de emojis para vs code",
    //   image: "/extensions/emoji_panel.png",
    //   tags: ["vs code", "extension"],
    //   github: " 
    // }
    {
      categories: ["Utilities", "CLI Tool"],
      name: "API Generator",
      description: "Generador de bases para APIs",
      image: "/api_template_generator.webp",
      tags: ["nodejs", "cli tool"],
      github: "https://github.com/fiedri/api-templates-generator.git",
      link: ""
    },{
      categories: ["Telegram Bot", "Utilities"],
      name: "NeoDown",
      description: "Descagador de contenido de redes",
      tags: ["Python", "Telegram", "Bot"],
      github: "https://github.com/fiedri/downloader_bot",
      link: ""
    },{
  categories: ["Desktop App", "Data Science"],
  name: "Movie Log",
  description: "Motor de recomendación inteligente",
  tags: ["Python", "Tkinter", "SQLite"],
  image: '/movie_log.webp',
  github: "https://github.com/fiedri/movie_log",
  link: '/movie_log.webp'
},{
  categories: ["Mobile App", "Android"],
  name: "Vibe",
  description: "Reproductor de música local, offline y sin anuncios",
  tags: ["Svelte", "Capacitor"],
  image: "/mobile/vibe.webp",
  github: "https://github.com/fiedri/vibe-player",
  link: ""
}
  ];

  let fullWA = project.filter(p => p.categories.some(c => ["Full Stack", "Web application"].includes(c)));
  let cliTools = project.filter(p => p.categories.some(c => ["CLI Tool"].includes(c)));
  let utilities = project.filter(p => p.categories.some(c => ["Utilities"].includes(c)));
  let telegramBots = project.filter(p => p.categories.some(c => ["Telegram Bot"].includes(c)));
  let desktopApps = project.filter(p => p.categories.some(c=>["Desktop App"].includes(c)))
  let mobileApps = project.filter(p => p.categories.some(c=>["Mobile App"].includes(c)))
</script>

<div class="projects-page-container">
  <FeaturedProjects projects={fullWA} title="Full Stack y aplicaciones web"/>
  <FeaturedProjects projects={cliTools} title="CLI Tools"/>
  <FeaturedProjects projects={utilities} title="Utilidades"/>
  <FeaturedProjects projects={telegramBots} title="Telegram Bots"/>
  <FeaturedProjects projects={desktopApps} title="Desktop App"/>
  <FeaturedProjects projects={mobileApps} title="Mobile App"/>
</div>

<style>
  .projects-page-container {
    padding-top: 80px;
    padding-bottom: 100px;
    min-height: 100vh;
  }
</style>
