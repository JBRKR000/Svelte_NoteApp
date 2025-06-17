<script>
    import { fade, fly } from "svelte/transition";
    import Navbar from "$lib/components/Navbar.svelte";
    import Footer from "$lib/components/Footer.svelte";
    import PresentationSection from "$lib/components/PresentationSection.svelte";
    import HowItWorks from "$lib/components/HowItWorks.svelte";
    import { onMount } from "svelte";
    let show = false;
    let animationFinished = false;

    onMount(() => {
        setTimeout(() => show = true, 10);
    });
</script>

<div class="fixed inset-0 -z-10 bg-gradient-to-t from-indigo-950 to-black"></div>

{#if show}
    <div
        class="min-h-screen font-manrope relative"
        transition:fly={{ y: 40, opacity: 0, duration: 600, delay: 80 }}
    >
        <Navbar />
        <PresentationSection bind:animationFinished />
        <HowItWorks {animationFinished}/>
        <Footer />
    </div>
{/if}