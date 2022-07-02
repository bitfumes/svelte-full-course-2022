<script>
  import user1 from "../assets/images/user1.png";
  import user2 from "../assets/images/user2.png";
  import user3 from "../assets/images/user3.png";

  let users = [
    {
      id: 1,
      image: user1,
      name: "John",
      email: "John@bitfumes.com",
    },
    {
      id: 2,
      image: user2,
      name: "Jeni",
      email: "Jenie@bitfumes.com",
    },
    {
      id: 3,
      image: user3,
      name: "Hacker",
      email: "hacker@bitfumes.com",
    },
  ];

  const getUsers = () => {
    return users;
  };
</script>

<div>
  <h1>List of Users</h1>
  {#each getUsers() as { image, name, email, id }, i (id)}
    <div>
      <p>{i + 1}</p>
      <img src={image} alt={name} />
      <p>{name}</p>
      <p>{email}</p>
    </div>
  {:else}
    <p>No user found</p>
  {/each}
</div>
