<script lang="ts">
	import { onMount } from 'svelte';

    let displayed = '';
    let text = 'Start being productive.'
    let delay = 75;
    onMount(() => {
        function typeText(){
            let i = 0;
            for (let char of text) {
                setTimeout(() => {
                    displayed += char;
                }, i * delay);
                i++;
            }
        }
        typeText();
    });

</script>

<div class="presentation bg-black min-h-screen font-manrope flex items-center justify-center">
	<h1 class="text-3xl md:text-5xl font-bold text-white whitespace-pre-line">
		{displayed}
	</h1>
</div>

<style>
    .presentation {
        font-family: 'Manrope', sans-serif;
        font-weight: 200;
    }
</style>