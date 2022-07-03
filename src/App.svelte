<script>
  import { Link, Route, Router } from "svelte-navigator";
  import HomePage from "./page/HomePage.svelte";
  import UserPage from "./page/UserPage.svelte";
</script>

<Router>
  <!-- <Route path="/">
    <Home />
  </Route> -->
  <nav class="p-4 bg-blue-800 text-white">
    <Link class="mx-4 cursor-pointer hover:underline" to="/">Home</Link>
    <Link class="mx-4 cursor-pointer hover:underline" to="/users">Users</Link>
  </nav>

  <Route path="/">
    <HomePage />
  </Route>
  <Route path="/users">
    <UserPage />
  </Route>
</Router>
