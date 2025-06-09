<script lang="ts">
    import { onMount, tick, onDestroy } from 'svelte';

    let displayed = '';
    let text = 'Start being productive.'
    let delay = 75;
    let typeFinished = false;
    let showCaret = true;
    let caretInterval: ReturnType<typeof setInterval>;

    onMount(() => {
        function typeText(){
            for (let i = 0; i < text.length; i++) {
                setTimeout(async () => {
                    displayed += text[i];
                    if(i === text.length - 1) {
                        typeFinished = true;
                        clearInterval(caretInterval);
                        showCaret = false;
                        await tick();
                    }
                }, i * delay);
            }
        }
        typeText();

        caretInterval = setInterval(() => {
            if (!typeFinished) showCaret = !showCaret;
        }, 500);
    });

    onDestroy(() => {
        clearInterval(caretInterval);
    });
</script>

<div class="presentation bg-black min-h-screen font-manrope flex items-center justify-center">
    <h1 class="text-3xl md:text-5xl font-bold text-white whitespace-pre-line">
        {displayed}<span class="carret text-white">{!typeFinished && showCaret ? '|' : ''}</span>
    </h1>
</div>