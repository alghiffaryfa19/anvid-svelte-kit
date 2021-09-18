<script context="module">

    export async function load({ fetch, page }) {
        let article;

        try {
            article = await fetch(`https://anvid.alghiffaryenterprise.id/api/article/${page.params.slug}`);
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
	export let article;
</script>
<svelte:head>	
	<title>Detail</title>		
</svelte:head>
<section>
    <img src="{article.thumbnail}" alt="">
    <h3>{article.title}</h3>
    <p>{@html article.detail}</p>
    <span>Author : {article.user.name}</span>
    <br>
    <span>Dibuat : {article.tanggal}</span>
</section>


