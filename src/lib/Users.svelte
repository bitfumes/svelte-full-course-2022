<script>
  import user1 from "../assets/images/user1.png";
  import user2 from "../assets/images/user2.png";
  import user3 from "../assets/images/user3.png";
  import User from "./User.svelte";

  let users = [
    {
      id: 1,
      image: user1,
      name: "John",
      email: "John@bitfumes.com",
      active: false,
    },
    {
      id: 2,
      image: user2,
      name: "Jeni",
      email: "Jenie@bitfumes.com",
      active: true,
    },
    {
      id: 3,
      image: user3,
      name: "Hacker",
      email: "hacker@bitfumes.com",
      active: false,
    },
  ];

  let filteredUsers = users;

  const filter = (e) => {
    if (e.target.value === "null") {
      filteredUsers = users;
      return;
    }

    const active = e.target.value === "true";
    filteredUsers = users.filter((user) => user.active === active);
  };
</script>

<div>
  <h1 class="text-2xl text-center mt-10">List of Users</h1>

  <div class="ml-4 mt-4">
    <label for="user-filter">Filter User</label>
    <select
      on:change={filter}
      name="user-filter"
      id="user-filter"
      class="border rounded-lg px-4 py-2 ml-4"
    >
      <option value={null}>All</option>
      <option value={true}>Active</option>
      <option value={false}>Inactive</option>
    </select>
  </div>

  {#each filteredUsers as user, i (user.id)}
    <User {user} {i} />
  {:else}
    <p>No user found</p>
  {/each}
</div>
