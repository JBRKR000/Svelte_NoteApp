<script lang="ts">
    import { fade } from 'svelte/transition';
</script>

<section class="flex flex-col items-center justify-center  text-white font-manrope px-4 py-16">
    <h2 class="text-4xl md:text-5xl font-bold mb-10 text-center">How It Works</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 w-full max-w-5xl">
        <div class="flex flex-col items-center p-6 bg-black/30 rounded-xl shadow-lg" transition:fade>
            <!-- Icon: Pencil -->
            <svg class="w-12 h-12 mb-4 text-cyan-400" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M16.862 3.487a2.25 2.25 0 1 1 3.182 3.182L7.5 19.213l-4 1 1-4 14.362-14.726z"/>
            </svg>
            <h3 class="text-xl font-semibold mb-2">Create Notes</h3>
            <p class="text-center text-gray-300">Quickly add your thoughts, tasks, or ideas in a simple and intuitive editor.</p>
        </div>
        <div class="flex flex-col items-center p-6 bg-black/30 rounded-xl shadow-lg" transition:fade>
            <!-- Icon: List -->
            <svg class="w-12 h-12 mb-4 text-emerald-400" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h7"/>
            </svg>
            <h3 class="text-xl font-semibold mb-2">Organize</h3>
            <p class="text-center text-gray-300">Keep your notes organized and accessible from anywhere, anytime.</p>
        </div>
        <div class="flex flex-col items-center p-6 bg-black/30 rounded-xl shadow-lg" transition:fade>
            <!-- Icon: Check -->
            <svg class="w-12 h-12 mb-4 text-pink-400" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7"/>
            </svg>
            <h3 class="text-xl font-semibold mb-2">Be Productive</h3>
            <p class="text-center text-gray-300">Focus on what matters and boost your productivity every day.</p>
        </div>
    </div>
</section>