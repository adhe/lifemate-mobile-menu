<script>
  import { fade } from "svelte/transition";
  import { Menu, Phone, MapPin } from "lucide-svelte";
  import { createDialog, melt } from "@melt-ui/svelte";

  const {
    elements: { trigger, overlay, content, portalled, close },
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
    <!-- Overlay -->
    <div
      use:melt={$overlay}
      class="fixed inset-0 z-50 bg-black/50"
      transition:fade={{ duration: 100 }}
    ></div>

    <!-- Content Dialog -->
    <div
      use:melt={$content}
      class="fixed left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 z-50 max-h-[70vh] w-[90vw] max-w-[450px] bg-lifemate-green rounded-lg shadow-md p-2"
      transition:fade={{ duration: 75 }}
    >
      <div class="flex justify-between">
        <div class="bg-white/20 w-72 h-12 rounded"></div>
        <button use:melt={$close} class="bg-white/20 size-8 rounded"></button>
      </div>

      <div class="">
        <div>Menu 1</div>
        <div>Menu 2</div>
        <div>Menu 3</div>
      </div>
    </div>
  </div>
{/if}
