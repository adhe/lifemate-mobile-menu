<script>
  import { fade } from "svelte/transition";
  import { Menu, Phone, MapPin } from "lucide-svelte";
  import { createDialog, melt } from "@melt-ui/svelte";

  const {
    elements: { trigger, overlay, content, portalled },
    states: { open },
  } = createDialog({
    forceVisible: true,
  });
</script>

<div
  class="flex justify-between items-center bg-white p-2 border-b border-gray-200"
>
  <div class="bg-gray-300 h-12 w-56 rounded"></div>
  <div class="flex space-x-1">
    <button
      class="bg-white size-8 rounded flex items-center justify-center border"
    >
      <MapPin size="20" color="#00AA00" />
    </button>
    <button
      class="bg-white size-8 rounded flex items-center justify-center border"
    >
      <Phone size="20" color="#00AA00" />
    </button>
    <button
      use:melt={$trigger}
      class="bg-white size-8 rounded flex items-center justify-center border"
    >
      <Menu size="20" color="#00AA00" />
    </button>
  </div>
</div>

{#if $open}
  <div use:melt={$portalled}>
    <div
      use:melt={$overlay}
      class="fixed inset-0 z-50 bg-black/50"
      transition:fade={{ duration: 100 }}
    ></div>
  </div>
{/if}
