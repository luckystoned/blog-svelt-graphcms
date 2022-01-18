<script>
    export let pages
</script>
<div class="navbar mb-2 shadow-lg bg-neutral text-neutral-content rounded-box">
    <div class="px-2 mx-2 navbar-start">
      <span class="text-lg font-bold">
            Stoned Blog
        </span>
    </div> 
    <div class="px-2 mx-2 navbar-center lg:flex">
      <div class="flex items-stretch">
            <a href="/" class="btn btn-ghost btn-sm rounded-btn">
                Home
            </a>
          {#each pages as { title, slug }}              
            <a exact href={`/${slug}`} class="btn btn-ghost btn-sm rounded-btn">
                {title}
            </a>
          {/each}
      </div>
    </div> 
    <div class="navbar-end">
    </div>
  </div>