<script>
  import Nested from "./Nested.svelte";
  let name = "Alex";
  let src = "/favicon.png";
  let string = "this string contains some <strong>HTML!!!</strong>";
</script>

<h1>Hello, {name.toUpperCase()}</h1>
<img {src} alt="Svelte favicon" />
<p>This is a paragraph</p>
<Nested />
{@html string}

<style>
  p {
    color: goldenrod;
    font-family: "Comic Sans MS", cursive;
    font-size: 2em;
  }
</style>
