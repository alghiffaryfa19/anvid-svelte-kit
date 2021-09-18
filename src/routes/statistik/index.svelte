<script context="module">

    export async function load({ fetch, page }) {
        let statistic;

        try {
            statistic = await fetch(`https://anvid.alghiffaryenterprise.id/api/statistik`);
            statistic = await statistic.json();
        } catch (e) {
            console.log(e);
        }
        return {
            props: {
                statistic
            }
        };
    }
</script>
<script>
	export let statistic;
</script>
<svelte:head>	
	<title>Statistik</title>		
</svelte:head>
<section>
    <ul>
        <li>
            Positif : {statistic.positif}
        </li>
        <li>
            Sembuh : {statistic.sembuh}
        </li>
        <li>
            Meninggal : {statistic.meninggal}
        </li>
        <li>
            Dirawat : {statistic.dirawat}
        </li>
    </ul>
</section>


