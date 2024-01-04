<script>
  import Nested from "./Nested.svelte";
  let name = "Alex";
  let src = "/favicon.png";
  let string = "this string contains some <strong>HTML!!!</strong>";

  let count = 0;

  function increment() {
    count++;
  }

  $: {
    if (count > 10) {
      count = 0;
    }
    console.log(`The value of count is ${count}`);
    console.log("This will also be logged");
  }

  $: doubled = count * 2;

  let numbers = [1, 2, 3, 4];
  function addNumbers() {
    // Option 1
    // numbers.push(numbers.length + 1);
    // numbers = numbers; // trigger the reactivity
    // Option 2
    // numbers = [...numbers, numbers.length + 1]; // using immutable data
    // Option 3
    numbers[numbers.length] = numbers.length + 1;
  }

  $: sum = numbers.reduce((t, n) => t + n, 0);
</script>

<h1>Hello, {name.toUpperCase()}</h1>
<img {src} alt="Svelte favicon" />
<p>This is a paragraph</p>
<Nested />
{@html string}

<button on:click={increment}>Clicked {count} {count === 1 ? "time" : "times"}</button>
<p>Count doubled is {doubled}</p>

<button on:click={addNumbers}>Expand the array</button>
<p>{numbers.join("+")} = {sum}</p>

<style>
  p {
    color: goldenrod;
    font-family: "Comic Sans MS", cursive;
    font-size: 2em;
  }
</style>
