<script>
import { createEventDispatcher } from 'svelte';
export let songPlaying;
export let playbackSpeed;

const dispatch = createEventDispatcher();

function jumpBack () {
    dispatch('jump', 'back');
}

function prevSong () {
    dispatch('prevSong');
}

function playMusic () {
    dispatch('playMusic');
}

function nextSong () {
    dispatch('nextSong');
}

function jumpForward () {
    dispatch('jump', 'forward');
}

function playbackRate (speed) {
    dispatch('playbackRate', speed);
}
</script>

<div class="btn-group" role="group">
    <button
        type="button"
        id="jumpBack"
        class="btn btn-primary-outline btn-lg d-flex align-items-center flex-column justify-content-center"
        on:focus={(e) => e.target.blur()}
        on:click={jumpBack}>
        <div class="text-white">-30</div>
        <div><i class="fas fa-angle-double-left fa-2x fa-inverse" /></div>
    </button>

    <button
        type="button"
        id="prevBtn"
        class="btn btn-primary-outline btn-lg"
        on:focus={(e) => e.target.blur()}
        on:click={prevSong}>
        <i class="fas fa-step-backward fa-2x fa-inverse" />
    </button>

    {#if !songPlaying}
        <button
            type="button"
            id="playBtn"
            class="btn btn-primary-outline btn-lg"
            on:focus={(e) => e.target.blur()}
            on:click={playMusic}>
            <i class="far fa-play-circle fa-4x fa-inverse" />
        </button>
    {:else}
        <button
            type="button"
            id="pauseBtn"
            class="btn btn-primary-outline btn-lg"
            on:focus={(e) => e.target.blur()}
            on:click={playMusic}>
            <i class="far fa-pause-circle fa-4x fa-inverse" />
        </button>
    {/if}

    <button
        type="button"
        id="nextBtn"
        class="btn btn-primary-outline btn-lg"
        on:focus={(e) => e.target.blur()}
        on:click={nextSong}>
        <i class="fas fa-step-forward fa-2x fa-inverse" />
    </button>

    <button
        type="button"
        id="jumpForward"
        class="btn btn-primary-outline btn-lg d-flex align-items-center flex-column justify-content-center"
        on:focus={(e) => e.target.blur()}
        on:click={jumpForward}>
        <div class="text-white">+30</div>
        <div><i class="fas fa-angle-double-right fa-2x fa-inverse" /></div>
    </button>
</div>

<div class="row">
    <div class="col mt-3">
        <div>
            Narration Speed {playbackSpeed}
        </div>
        <div class="btn-group" role="group">
            <button
                type="button"
                id="playbackRate0"
                class="btn btn-primary-outline btn-lg mr-1"
                on:focus={(e) => e.target.blur()}
                on:click={() => playbackRate(0.5)}>
                <div class="{playbackSpeed === 0.5 ? 'text-danger' : 'text-white'}">X0.5</div>
            </button>

            <button
                type="button"
                id="playbackRate1"
                class="btn btn-primary-outline btn-lg mr-1"
                on:focus={(e) => e.target.blur()}
                on:click={() => playbackRate(1)}>
                <div class="{playbackSpeed === 1 ? 'text-danger' : 'text-white'}">X1</div>
            </button>
            
            <button
                type="button"
                id="playbackRate1-5"
                class="btn btn-primary-outline btn-lg mr-1"
                on:focus={(e) => e.target.blur()}
                on:click={() => playbackRate(1.5)}>
                <div class="{playbackSpeed === 1.5 ? 'text-danger' : 'text-white'}">X1.5</div>
            </button>

            <button
                type="button"
                id="playbackRate2"
                class="btn btn-primary-outline btn-lg mr-1"
                on:focus={(e) => e.target.blur()}
                on:click={() => playbackRate(2)}>
                <div class="{playbackSpeed === 2 ? 'text-danger' : 'text-white'}">X2</div>
            </button>
        </div>
    </div>
</div>
