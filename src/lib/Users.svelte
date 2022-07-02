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

  const getUsers = () => {
    return users;
  };
</script>

<div>
  <h1 class="text-2xl text-center mt-10">List of Users</h1>
  {#each getUsers() as user, i (user.id)}
    <User {user} {i} />
  {:else}
    <p>No user found</p>
  {/each}
</div>
