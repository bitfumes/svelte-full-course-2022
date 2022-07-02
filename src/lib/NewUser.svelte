<script>
  import Modal from "./Modal.svelte";
  let showModal = false;
</script>

<div class="mt-4">
  <button
    on:click={() => (showModal = true)}
    class="px-4 py-1 bg-blue-800 text-white rounded cursor-pointer"
    >New User</button
  >

  {#if showModal}
    <Modal on:close={() => (showModal = false)} />
  {/if}
</div>
