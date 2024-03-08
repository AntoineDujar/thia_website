<script lang="ts">
  import Flicking, { FlickingPanel } from "@egjs/svelte-flicking";
  import { Arrow, Fade } from "@egjs/flicking-plugins";

  import "@components/svelte/pagination.css";
  import "@components/svelte/arrow.css";
  import "@egjs/svelte-flicking/dist/flicking.css";
  import { Pagination } from "@egjs/flicking-plugins";

  let flicking: Flicking;
</script>

<FlickingPanel>
  <slot name="iframe" />
</FlickingPanel>
