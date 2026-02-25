<script>
  export let heading = "";
  export let content = "";
</script>

<div class="my-4 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <h2 class="font-semibold mb-2">
    {#if $$slots.heading}
      <slot name="heading" />
    {:else}
      {heading}
    {/if}
  </h2>

  <div>
    {#if $$slots.content}
      <slot name="content" />
    {:else}
      {content}
    {/if}
  </div>
</div>
