<script>
    import { Toaster } from "svelte-sonner";

    import "../app.css";
    import "../tailwind.css";

    import "tippy.js/dist/tippy.css";

    import { setContext, onMount } from "svelte";
    import i18n, { initI18n, getLanguages } from "$lib/i18n";

    let { children } = $props();

    setContext("i18n", i18n);

    onMount(async () => {
        const languages = await getLanguages();

        const browserLanguage = navigator.languages
            ? navigator.languages[0]
            : navigator.language || navigator.userLanguage;

        initI18n("en-US");
    });
</script>

<svelte:head>
    <meta
        name="keywords"
        content="Open WebUI, Ollama, OpenAI, Chatbot, Local AI, Open-Source, Assistant Models, Language Models, Character AI"
    />
    <meta name="robots" content="index, follow" />
    <meta name="googlebot" content="index, follow" />
    <meta name="revisit-after" content="7 days" />
    <meta name="language" content="English" />
    <meta name="og:url" content="https://www.openwebui.com" />
    <meta name="og:site_name" content="Open WebUI" />
    <meta name="og:type" content="website" />
</svelte:head>

<Toaster position="top-center" richColors theme="dark" />

<div
    class="app h-fit min-h-screen bg-white text-gray-700 dark:bg-black dark:text-gray-100"
>
    {@render children()}
</div>
