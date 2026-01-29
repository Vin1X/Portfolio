<script>
  export let heading = '';
  export let content = '';
</script>

<div class="my-4 p-2 border-2 border-gray-300 bg-gray-500 bg-opacity-75 rounded-md">
  <h2 class="font-semibold">
    {#if $$slots.heading}
      <slot name="heading" />
    {:else}
      {heading}
    {/if}
  </h2>

  <div class="mt-2">
    {#if $$slots.content}
      <slot name="content" />
    {:else}
      {content}
    {/if}
  </div>
</div>