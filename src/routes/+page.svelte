<script>
    import Navbar from "$lib/components/Navbar.svelte";
    import Footer from "$lib/components/Footer.svelte";
    import PresentationSection from "$lib/components/PresentationSection.svelte";
	import HowItWorks from "$lib/components/HowItWorks.svelte";
</script>

<head>
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@200..800&display=swap" rel="stylesheet">
</head>


<div class="min-h-screen font-manrope bg-gradient-to-t from-indigo-950 to-black">
    <Navbar />
    <PresentationSection />
    <HowItWorks />
    <Footer />
</div>

