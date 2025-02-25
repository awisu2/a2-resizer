<script lang="ts">
    import { convertFileSrc } from "@tauri-apps/api/core";

    let path = $state("")
    let src = $state("")

    // 最初はで$deriveで直接更新していたが、
    // pathの更新時に、pathを再帰的に更新したかったため、$effectで対応するように変更
    $effect(() => {
        src = ""
        if (!path) return

        const _path = path.replace(/"/g, "")
        if (!path || path != _path) {
            path = _path
        }

        src = convertFileSrc(path)
    }) 
</script>

<div>
    <input bind:value={path} />
</div>

<div>
    convertedSrc: {src}
</div>

{#if src}
    <div>
        <img {src} class="image" alt="base image" />
    </div>
{/if}

<style>
    .image {
        max-width: 100%;
        width: 100%;
    }
</style>