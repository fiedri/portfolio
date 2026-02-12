<script lang="ts">
  let {projects, title} = $props() 
  let scrollContainer: HTMLDivElement;

  function scroll(direction: 'left' | 'right') {
    const scrollAmount = 400;
    if (scrollContainer) {
      scrollContainer.scrollBy({
        left: direction === 'left' ? -scrollAmount : scrollAmount,
        behavior: 'smooth'
      });
    }
  }
</script>

<section class="featured-section" id="featured">
  <div class="header">
    <h2 class="poppins">{title}</h2>
    <div class="controls">
      <button onclick={() => scroll('left')} aria-label="Anterior"><i class="fa-solid fa-chevron-left"></i></button>
      <button onclick={() => scroll('right')} aria-label="Siguiente"><i class="fa-solid fa-chevron-right"></i></button>
    </div>
  </div>

  <div class="carousel-container" bind:this={scrollContainer}>
    <div class="carousel-track">
      {#each projects as project}
        <article class="project-card" data-aos="fade-left">
          <div class="image-wrapper">
            <img src={project.image} alt={project.name} loading="lazy" />
            <div class="card-overlay">
              <div class="overlay-content">
                <h3 class="poppins">{project.name}</h3>
                <p>{project.description}</p>
                <div class="tags">
                  {#each project.tags as tag}
                    <span>{tag}</span>
                  {/each}
                </div>
                <div class="actions">
                  <a href={project.link} target="_blank" class="btn-primary">Ver</a>
                  <a href={project.github} target="_blank" class="btn-icon"><i class="fa-brands fa-github"></i></a>
                </div>
              </div>
            </div>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<style>
  .featured-section {
    padding: 60px 5% 20px;
    overflow: hidden;
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 30px;
  }

  h2 {
    font-size: 2.5rem;
    color: white;
    margin: 0;
  }

  .controls button {
    background: rgba(255, 255, 255, 0.1);
    border: none;
    color: white;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    cursor: pointer;
    margin-left: 10px;
    transition: background 0.3s;
  }

  .controls button:hover {
    background: var(--violet-color);
  }

  .carousel-container {
    overflow-x: auto;
    scrollbar-width: none; 
    -ms-overflow-style: none; 
    /* Padding vertical para dar espacio al escalado (hover) */
    padding: 20px 0;
    margin: -20px 0; 
  }

  .carousel-container::-webkit-scrollbar {
    display: none; 
  }

  .carousel-track {
    display: flex;
    gap: 25px;
    /* Aseguramos espacio a los lados también */
    padding: 5px 10px;
  }

  .project-card {
    flex: 0 0 350px;
    position: relative;
    border-radius: 12px;
    overflow: hidden;
    background: #1a1a2e;
    transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    aspect-ratio: 16 / 9;
    border: 1px solid rgba(255, 255, 255, 0.05);
  }

  .project-card:hover {
    transform: scale(1.05);
    z-index: 50; /* Z-index alto para sobresalir */
    border-color: var(--violet-color);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6), 0 0 25px rgba(99, 47, 221, 0.4);
  }

  .image-wrapper {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: hidden;
  }

  .image-wrapper::after {
    content: '';
    position: absolute;
    inset: 0;
    background: rgba(0, 0, 0, 0);
    transition: background 0.3s ease;
    pointer-events: none;
    z-index: 1;
  }

  .project-card:hover .image-wrapper::after {
    background: rgba(0, 0, 0, 0.4); 
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: all 0.5s ease;
    filter: brightness(1) contrast(1);
  }

  .project-card:hover img {
    filter: brightness(0.2) contrast(1.1);
  }

  .card-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(0, 0, 0, 0.9) 0%, rgba(0, 0, 0, 0.4) 60%, transparent 100%);
    opacity: 0;
    transition: opacity 0.3s;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 20px;
    z-index: 2;
  }

  .project-card:hover .card-overlay {
    opacity: 1;
  }

  .overlay-content h3 {
    font-size: 1.6rem;
    font-weight: 800;
    margin: 0 0 8px 0;
    color: #ffffff;
    text-shadow: 
      0px 0px 10px var(--violet-color),
      0px 0px 20px rgba(99, 47, 221, 0.6);
  }

  .overlay-content p {
    font-size: 1rem;
    font-weight: 700;
    color: #ffffff;
    margin-bottom: 15px;
    line-height: 1.4;
    text-shadow: 1px 1px 4px rgba(0,0,0,1);
  }

  .tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 15px;
  }

  .tags span {
    font-size: 0.75rem;
    font-weight: 700;
    background: rgba(99, 47, 221, 0.4);
    color: #ffffff;
    padding: 4px 10px;
    border-radius: 6px;
    border: 1px solid rgba(167, 139, 250, 0.5);
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .actions {
    display: flex;
    align-items: center;
    gap: 15px;
  }

  .btn-primary {
    background: var(--violet-color);
    color: white;
    text-decoration: none;
    padding: 6px 20px;
    border-radius: 4px;
    font-weight: 600;
    font-size: 0.9rem;
  }

  .btn-icon {
    color: white;
    font-size: 1.2rem;
    text-decoration: none;
    opacity: 0.8;
    transition: opacity 0.3s;
  }

  .btn-icon:hover {
    opacity: 1;
    color: var(--violet-color);
  }

  @media (max-width: 640px) {
    .project-card {
      flex: 0 0 280px;
    }
    h2 {
      font-size: 1.8rem;
    }
  }
</style>