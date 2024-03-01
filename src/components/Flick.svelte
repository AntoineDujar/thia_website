<script lang="ts">
  import Flicking, { FlickingPanel } from "@egjs/svelte-flicking";
  import { AutoPlay, Arrow, Fade } from "@egjs/flicking-plugins";

  import "@egjs/flicking-plugins/dist/arrow.css";
  import "@egjs/flicking-plugins/dist/pagination.css";
  import "@egjs/svelte-flicking/dist/flicking.css";

  let flicking: Flicking;

  const plugins = [
    new AutoPlay({ duration: 15000, direction: "NEXT", stopOnHover: false }),
    new Arrow(),
    new Fade(""),
  ];
</script>

<div class="container">
  <Flicking
    {plugins}
    options={{ circular: true, duration: 450, preventDefaultOnDrag: true }}
    bind:this={flicking}
  >
    <FlickingPanel><slot name="video-1" /></FlickingPanel>
    <FlickingPanel><slot name="video-2" /></FlickingPanel>
    <FlickingPanel><slot name="video-3" /></FlickingPanel>
    <svelte:fragment slot="viewport">
      <span class="flicking-arrow-prev is-circle"></span>
      <span class="flicking-arrow-next is-circle"></span>
    </svelte:fragment>
  </Flicking>
</div>

<style>
  .flicking-arrow-prev::before,
  .flicking-arrow-prev::after,
  .flicking-arrow-next::before,
  .flicking-arrow-next::after {
    background-color: rgb(0, 0, 0);
  }

  .is-circle {
    background-color: white;
  }

  .container {
    max-width: 35rem;
    border-radius: 8px;
    overflow: hidden;
  }
</style>
