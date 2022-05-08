<script>
    export let item
</script>

<div class="card" ><slot></slot></div>

<style>
    .card{
        background-color: coral;
        border-radius: 15px;
        padding: 40px 50px;
        margin: 20px 0;
        position: relative;
    }
</style>