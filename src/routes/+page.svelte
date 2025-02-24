<script lang="ts">
    import { convertFileSrc } from "@tauri-apps/api/core";

    const convertInput = (path: string): string =>  {
        if (!path) return ""

        const _path = path.replace(/"/g, "")
        console.log(_path);
        if (!_path) return ""

        return convertFileSrc(_path)
    }

    let path = $state("")
    let src = $derived(convertInput(path))
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