<script>
  let arr = JSON.parse(localStorage.getItem("ArrayPost"));
  export let EditPost = () => {};
  let Pid;
  import Post from "./Post.svelte";
  const getId = (e, id) => {
    e.stopPropagation();
    Pid = id;
  };
</script>

<div class="PostsBox">
  {#if Pid}
    {#each arr as post}
      {#if post.id === Pid}
        <Post
          name={post.title}
          DateOfEditing={post.DateOfEditing}
          text={post.text}
          id={post.id}
        />
      {/if}
    {/each}
  {:else}
    {#each arr as post}
      <Post
        getId={(e) => getId(e, post.id)}
        EditPost={() => EditPost(post)}
        name={post.title}
        rpost={post}
        DateOfEditing={post.DateOfEditing}
        id={post.id}
      />
    {/each}
  {/if}
</div>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }
  .PostsBox {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 20px;
    font-weight: 100;
  }
</style>
