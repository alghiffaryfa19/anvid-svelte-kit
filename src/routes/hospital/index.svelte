<script context="module">

</script>
<script>
// @ts-nocheck

    import Overlay from '$lib/Overlay.svelte';
    import RowWara from '$lib/RowWara.svelte';
    import axios from 'axios';
    let rows = [];
    let loading = true;
    function changePage(params) {
        axios.get('https://anvid.alghiffaryenterprise.id/api/hospital', {
        params: params
        })
        .then(function (response) {
        rows = response.data;
        })
        .catch(error => {
        console.error(error);
        })
        .finally(() => {
        loading = false;
        });
    }
    changePage();
    
    
</script>
<svelte:head>	
	<title>Rumah Sakit Terdekat</title>	
</svelte:head>
<section>
    <div style="margin-bottom: 10px;">
        <input class="form-control" placeholder="Lat Lon pisahkan dengan koma tanpa spasi" on:keyup={e => changePage({cari: e.target.value})}/>
    </div>

    {#if loading}
    <Overlay />
    {/if}
    <div id="data-wrapper">
        {#each rows as row}
        <RowWara {row} />
        
        {:else}
        <tr>
            <td colspan="100%">
            <h5 class="text-center">Belum ada wara-wara</h5>
            </td>
        </tr>
        {/each}
    </div>     
</section>