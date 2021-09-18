<script context="module">

    export async function load({ fetch, page }) {
        let article;

        try {
            article = await fetch(`https://anvid.alghiffaryenterprise.id/api/article`);
            article = await article.json();
        } catch (e) {
            console.log(e);
        }
        return {
            props: {
                article
            }
        };
    }
</script>
<script>
import RowWara from "$lib/RowWara.svelte";


	export let article;
</script>

<section>
    <ul>
        {#each article as item}
            <li>
                <a href="/artikel/{item.slug}">{item.title}</a>
            </li>
        {/each}
    </ul>
</section>