<script>
    import Note from './Note.svelte'
    import NotePlaceholder from './NotePlaceholder.svelte'

    export let notes
</script>

<div class="Dashboard">
   <div class="notes-container">
       <NotePlaceholder on:click/>
    {#each notes as n}
    <Note bind:note={n} on:update on:color on:remove/>
    {/each}
   </div>
</div>

<style>
    .Dashboard{
        box-sizing: border-box;
        width: 100%;
        padding: 20px;
    }
    .notes-container{
        display: grid;
        grid-template-columns: repeat(4,1fr);
        width: 100%;
        gap: 10px;
    }
</style>