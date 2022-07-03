<script>
  import { createEventDispatcher } from "svelte";
  import Modal from "./Modal.svelte";
  const dispatch = createEventDispatcher();

  let newUser = {};

  $: disableSubmitButton = !newUser.name || !newUser.email;

  let showModal = false;

  function handleForm() {
    dispatch("newUser", newUser);
    showModal = false;
  }
</script>

<div class="mt-4">
  <button
    on:click={() => (showModal = true)}
    class="px-4 py-1 bg-blue-800 text-white rounded cursor-pointer"
    >New User</button
  >

  {#if showModal}
    <Modal on:close={() => (showModal = false)} on:submit={handleForm}>
      <h1 class="text-2xl text-center">Create new user</h1>
      <div class="py-1 px-2 my-4">
        <label for="">Name</label>
        <input
          bind:value={newUser.name}
          type="text"
          class="px-2 py-1 w-full rounded border"
        />
      </div>

      <div class="py-1 px-2 my-4">
        <label for="">Email</label>
        <input
          bind:value={newUser.email}
          type="email"
          class="px-2 py-1 w-full rounded border"
        />
      </div>

      <div class="py-1 px-2 my-4 flex justify-between">
        <label for="true">Active:</label>
        <div class="flex">
          <label for="true">Yes</label>
          <input
            type="radio"
            value={true}
            id="true"
            bind:group={newUser.active}
            name="active"
            class="px-2 py-1 w-full rounded border mx-5"
          />
          <label for="false">No</label>
          <input
            type="radio"
            value={false}
            id="false"
            bind:group={newUser.active}
            name="active"
            class="px-2 py-1 w-full rounded border mx-5"
          />
        </div>
      </div>

      <button
        type="submit"
        disabled={disableSubmitButton}
        id="submit-button"
        slot="right-button"
        class="px-2 py-1 bg-blue-800 text-white rounded">Create</button
      >
    </Modal>
  {/if}
</div>
