<script>
  import AllPosts from "./AllPosts.svelte";
  import { Link, Route, Router } from "svelte-routing";
  import Home from "./Home.svelte";
  let Bool = false;
  let findedPost;
  export let url = "/";
  const data = [];
  localStorage.setItem("ArrayPost", JSON.stringify(data));
  localStorage.setItem("Title", "");
  localStorage.setItem("Text", "");
  let Text = localStorage.getItem("Text");
  let Title = localStorage.getItem("Title");
  function EditPost(post) {
    Bool = true;
    findedPost = post;
    Title = post.title;
    Text = post.text;
    localStorage.setItem("Title", Title);
    localStorage.setItem("Text", Text);
  }
</script>

<div class="PostsBox">
  <Router {url}>
    <nav>
      <Link to="/">Создание/Редактирование постов</Link>
      <Link to="/allposts" on:click={() => (Bool = false)}>Все посты</Link>
    </nav>
    <div>
      <Route path="/allposts">
        <AllPosts {EditPost} />
      </Route>
      <Route path="/">
        <Home {Bool} {findedPost} />
      </Route>
    </div>
  </Router>
</div>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }
  .PostBox {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
