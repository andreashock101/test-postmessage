<script>
    import {convertFileSrc} from "@tauri-apps/api/tauri";
    import {homeDir, join} from "@tauri-apps/api/path";

    async function convertFileSrcString() {
        const homeDirPath = await homeDir();
        const filePath = await join(homeDirPath, "example.pdf");
        return convertFileSrc(filePath);
    }
</script>

<main class="container">
    {#await convertFileSrcString() then src}
        <iframe id="iframe" title="This works, but throws an error" src="{src}"></iframe>
    {/await}
</main>

<style>
</style>