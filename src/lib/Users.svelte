<script>
  let user = {
    image: "https://cdn-icons-png.flaticon.com/128/3135/3135715.png",
    name: "John",
    email: "John@bitfumes.com",
  };
</script>

<div>
  <h1>List of Users</h1>
  <div>
    <img src={user.image} alt={user.name} />
    <p>{user.name}</p>
    <p>{user.email}</p>
  </div>
</div>
