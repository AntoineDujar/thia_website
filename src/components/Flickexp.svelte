<script lang="ts">
  import Flicking, { FlickingPanel } from "@egjs/svelte-flicking";
  import { Arrow, Fade } from "@egjs/flicking-plugins";

  import "@components/svelte/pagination.css";
  import "@components/svelte/arrow.css";
  import "@egjs/svelte-flicking/dist/flicking.css";
  import { Pagination } from "@egjs/flicking-plugins";

  let flicking: Flicking;

  const plugins = [
    new Arrow(),
    new Fade(""),
    new Pagination({ type: "bullet" }),
  ];
</script>

<div class="container">
  <Flicking
    {plugins}
    options={{ circular: true, duration: 450, preventDefaultOnDrag: true }}
    bind:this={flicking}
  >
    <slot name="panels" />
    <!-- <FlickingPanel><slot name="video-1" /></FlickingPanel> -->
    <!-- <FlickingPanel>
      <iframe
        width="1400"
        height="787"
        src="https://www.youtube.com/embed/C7FN6su1e9I?si=uguFUp6r1p7sBsCZ"
        title="YouTube video player"
        allow=""
        allowfullscreen
      ></iframe> -->
    <!-- </FlickingPanel> -->
    <svelte:fragment slot="viewport">
      <span class="flicking-arrow-prev is-circle"></span>
      <span class="flicking-arrow-next is-circle"></span>
      <div class="flicking-pagination" style="color: white"></div>
    </svelte:fragment>
  </Flicking>
</div>

<style>
  .container {
    max-width: min(1500px, calc(95vw));
    border-radius: 8px;
    overflow: hidden;
  }
</style>
