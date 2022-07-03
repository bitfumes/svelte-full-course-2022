<script>
  import { onMount } from "svelte";
  import { flip } from "svelte/animate";
  import { cubicIn, quintOut } from "svelte/easing";
  import { tweened } from "svelte/motion";
  import { add, remove, users } from "../store";
  import FilterUser from "./FilterUser.svelte";
  import NewUser from "./NewUser.svelte";
  import User from "./User.svelte";
  $: filteredUsers = $users;

  const filter = ({ detail }) => {
    if (detail === "null") {
      filteredUsers = $users;
      return;
    }

    const active = detail === "true";
    filteredUsers = $users.filter((user) => user.active === active);
  };

  const progress = tweened(0, {
    duration: 1000,
    easing: cubicIn,
  });

  onMount(() => {
    progress.set(filteredUsers.length);
  });
</script>

<div>
  <h1 class="text-2xl text-center mt-10">List of Users</h1>

  <div class="flex justify-between mx-4 items-center">
    <FilterUser on:filter={filter} />

    <NewUser on:newUser={add} />
  </div>

  <progress max="10" min="0" value={$progress} class="w-full mx-4" />

  {#each filteredUsers as user, i (user.id)}
    <div animate:flip={{ delay: 250, duration: 1000, easing: quintOut }}>
      <User on:remove={remove} {user} {i} />
    </div>
  {:else}
    <p>No user found</p>
  {/each}
</div>
