<script>
    import Logo from './utils/Logo.svelte'
    import Search from './utils/Search.svelte'
    import Settings from './utils/Settings.svelte'
</script>

<div class="Header">

    <Logo/>
    <Search on:input/>
    <Settings/>
</div>

<style>
    .Header{
        box-sizing: border-box;
        display: grid;
        width: 100%;
        grid-template-columns: repeat(3, 1fr);
        border: none;
        box-shadow:  2px 2px 1px rgba(0, 0, 0, 0.2);
        background: transparent;
    }

</style>

