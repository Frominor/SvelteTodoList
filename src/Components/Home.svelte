<script>
  let Title = localStorage.getItem("Title");
  let Text = localStorage.getItem("Text");
  export let Bool = false;
  export let findedPost;
  let arr = JSON.parse(localStorage.getItem("ArrayPost"));
  function AddPost() {
    if (!Bool) {
      arr.push({
        id: new Date().toISOString(),
        title: Title,
        DateOfEditing: "Не редактировалось",
        text: Text,
      });
      arr = [...arr];
      arr = JSON.stringify(arr);
      localStorage.setItem("ArrayPost", arr);
    } else {
      for (let k of arr) {
        if (k.id == findedPost.id) {
          k.text = Text;
          k.title = Title;
          k.DateOfEditing = new Date().toISOString();
        }
      }
      arr = [...arr];
      localStorage.setItem("ArrayPost", JSON.stringify(arr));
      Bool = false;
    }
    Text = "";
    Title = "";
    localStorage.setItem("Text", "");
    localStorage.setItem("Title", "");
  }
</script>

<div class="PostsBox">
  <input
    value={Title}
    on:change={(e) => (Title = e.target.value)}
    placeholder="Введите Заголовок "
  />
  <textarea
    value={Text}
    placeholder="Введите текст поста"
    on:change={(e) => (Text = e.target.value)}
  />
  <button on:click={AddPost}>{Bool ? "Изменить пост" : "Добавить пост"}</button>
</div>

<style>
  .PostsBox {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
