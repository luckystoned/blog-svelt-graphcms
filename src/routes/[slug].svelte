<script context="module">

    export const load = async ({ fetch, params }) => {

        const pathname = params.slug

        const res = await fetch(`/pages/${pathname}.json`);
        
        if(res.ok) {
            const { page } = await res.json()

            return {
                props: {
                    page
                },
            }
        }
    }

</script>

<script>

    export let page

    const { title, content: { html } } = page

</script>

<svelte:head>
    <title>Stoned Blog | {title}</title>
</svelte:head>

<h1 class="text-4xl font-semibold mb-5">{title}</h1>

<article class="prose">
    {@html html}
</article>