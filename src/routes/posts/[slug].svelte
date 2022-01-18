<script context="module">

    export const load = async ({ fetch, url }) => {
        const { pathname } = url

        const res = await fetch(`${pathname}.json`);

        if(res.ok) {
            const { post } = await res.json()

            return {
                props: {
                    post
                },
            }
        }
    }

</script>

<script>

    export let post

    const { title, date, tags, author: { name, authorTitle, picture}, content: { html }, coverImage } = post

</script>

<svelte:head>
    <title>Stoned Blog | Welcome</title>
</svelte:head>

<div class="sm:-mx-5 md:-mx-10 lg:-mx-20 xl:-mx-38 mb-5">
    <img src={coverImage.url} alt={`Cover Image for ${title}`}>
</div>

<h1 class="text-4xl font-semibold mb-5">{title}</h1>

<a href="/" class="inline-flex items-center mb-3">
    <img src={picture.url} alt={name} class="w-12 h-12 rounded-full flex-shrink-0 object-cover object-center">
    <span class="flex-grow flex flex-col pl-4">
        <span class="title-font font-medium">{name}</span>
        <span class="text-secondary text-xs tracking-widest mt-0.5">{authorTitle}</span>
    </span>
</a>

<p class="text-secondary text-xs tracking-widest mt-0.5">
    {new Date(date).toDateString()}
</p>

<div class="mb-5 flex justify-content">
    <div>
        {#if tags}
            <div class="mt-5 space-x-2">
                {#each tags as tag}
                    <span class="badge badge-primary">
                        {tag}
                    </span>
                {/each}
            </div>
        {/if}
    </div>
</div>


<article class="prose">
    {@html html}
</article>