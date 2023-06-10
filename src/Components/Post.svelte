<script>
  import { Link } from "svelte-routing";
  export let name = "Undefined";
  export let EditPost = () => {};
  export let DateOfEditing;
  export let id;
  export let text;
  export let getId = () => {};
</script>

<div on:click={(e) => getId(e, id)}>
  <h1>{name}</h1>
  <p>Дата создания-{id}</p>
  <p>Дата редактирования -{DateOfEditing}</p>
  <p>{text ? text : ""}</p>
  <Link to="/" on:click={EditPost}>Редактировать пост</Link>
</div>

<style>
  div {
    cursor: pointer;
    background-color: rgb(247, 241, 241);
    width: 500px;
    height: auto;
    border: 2px solid black;
    margin-top: 10px;
    margin-bottom: 10px;
  }
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 1em;
    font-weight: 100;
  }
</style>
