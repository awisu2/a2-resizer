<script lang="ts">
    import { convertFileSrc } from "@tauri-apps/api/core";

    let path = $state("")
    let safePath = $derived((() => {
        if (!path) return ""
        return path.replace(/"/g, "")
    })())

    let src = $derived((() => {
        if (!safePath) return ""
        return convertFileSrc(safePath)
    })())
</script>

<div>
    <input bind:value={path} />
</div>

<div>
    convertedSrc: {src}
</div>

<div>
    <img {src} class="image" alt="base image" />
</div>

<style>
    .image {
        max-width: 100%;
        width: 100%;
    }
</style>