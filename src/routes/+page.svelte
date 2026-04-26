<script>
  import About from "../lib/sections/About.svelte";
  import FeaturedProjects from "../lib/components/FeaturedProjects.svelte";
  import Hero from "../lib/sections/hero.svelte";
  import Projects from "../lib/sections/Projects.svelte";
  import { onMount } from "svelte";

  
</script>
<Hero/>
<!-- <div class="separator"></div> -->
<!-- <FeaturedProjects/> -->
<div class="separator"></div>
<Projects/>
<About/>
<style>
  .separator{
    margin-bottom: 90px;
  }
  @media(width < 640px) {
    .separator{
      margin-bottom: 50px;
    }
  }
</style>