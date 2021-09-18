<script>
    export let row;
</script>
<div class="col-md-12">
    <ul>
        <li>
            Nama : {row.name}
            Telfon : {row.telp}
            Maps : <a href="https://maps.google.com/?q={row.latitude},{row.longitude}">Klik Disini</a>
        </li>
    </ul>
</div>