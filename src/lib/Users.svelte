<script>
  import user1 from "../assets/images/user1.png";
  import { users } from "../store";
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

  const remove = ({ detail }) => {
    $users = $users.filter((user) => user.id !== detail);
  };

  const add = ({ detail }) => {
    $users = [
      {
        id: $users.length + 1,
        image: user1,
        ...detail,
      },
      ...$users,
    ];
  };
</script>

<div>
  <h1 class="text-2xl text-center mt-10">List of Users</h1>

  <div class="flex justify-between mx-4 items-center">
    <FilterUser on:filter={filter} />

    <NewUser on:newUser={add} />
  </div>
  {#each filteredUsers as user, i (user.id)}
    <User on:remove={remove} {user} {i} />
  {:else}
    <p>No user found</p>
  {/each}
</div>
