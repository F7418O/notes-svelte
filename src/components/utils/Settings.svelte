<script>
    import { darkMode } from "../../store/store.js";

    const handleMode = () => {
        darkMode.update((mode) => !mode);
    };
</script>

<div class="Settings">
    <div class={$darkMode ? "switch on" : "switch"}>
        <button class="circle" on:click={handleMode} />
    </div>
</div>

<style>
    .Settings {
        padding: 10px 0;
        position: relative;
        align-items: center;
    }
    .switch {
        position: relative;
        background-color: #ccc;
        width: 50px;
        height: 25px;
        border-radius: 30px;
        margin: 0 10px;
        left: 85%;
    }
    .switch .circle {
        cursor: pointer;
        width: 25px;
        height: 25px;
        border-radius: 50%;
        transition: all 0.2s;
    }

    .on .circle {
        margin-left: 45%;
    }

    .on {
        background-color: rgb(58, 54, 54);
    }
</style>
