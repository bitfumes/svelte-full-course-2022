<script>
  import user1 from "../assets/images/user1.png";
  import user2 from "../assets/images/user2.png";
  import user3 from "../assets/images/user3.png";

  let users = [
    {
      image: user1,
      name: "John",
      email: "John@bitfumes.com",
    },
    {
      image: user2,
      name: "Jeni",
      email: "Jenie@bitfumes.com",
    },
    {
      image: user3,
      name: "Hacker",
      email: "hacker@bitfumes.com",
    },
  ];
</script>

<div>
  <h1>List of Users</h1>
  <div>
    <img src={users[0].image} alt={users[0].name} />
    <p>{users[0].name}</p>
    <p>{users[0].email}</p>
  </div>
  <div>
    <img src={users[1].image} alt={users[1].name} />
    <p>{users[1].name}</p>
    <p>{users[1].email}</p>
  </div>
  <div>
    <img src={users[2].image} alt={users[2].name} />
    <p>{users[2].name}</p>
    <p>{users[2].email}</p>
  </div>
</div>
