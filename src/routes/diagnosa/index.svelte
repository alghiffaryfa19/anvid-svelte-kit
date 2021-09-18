<script context="module">

    export async function load({ fetch, page }) {
        let article;

        try {
            article = await fetch(`https://anvid.alghiffaryenterprise.id/api/diagnosa/18`);
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
    <ul class="list-decimal">
        {#each article['pertanyaan'] as item, index}
        <li>
            {item.tanya}
            <input type="hidden" name="tanya_id[{index}]" value="{item.id}">
        </li>
        
        {#each article['pilihan_jawaban'] as items}
                <div class="flex items-center mr-4 mb-4">
                    <input id="radio{item.id}{items.id}" type="radio" name="jawab_id[{index}]" value="{items.id}" />
                    <label for="radio{item.id}{items.id}" class="flex items-center cursor-pointer text-xl">
                    <span class="w-8 h-8 inline-block mr-2 rounded-full border border-grey flex-no-shrink"></span>
                    {items.jawab}</label>
               </div>
               {/each}
        {/each}
    </ul>
</section>