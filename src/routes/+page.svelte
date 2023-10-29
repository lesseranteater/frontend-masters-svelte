<script>
  import Nested from "./Nested.svelte";

  let name = "Svelte";
  let src = "/favicon.png";
  let htmlText = "This string contains some <strong>HTML</strong>.";
  let numbers = [1, 2, 3, 4];

  let count = 0;
  $: doubled = count * 2; // a reactive declaration
  $: {
    if (count >= 10) {
      alert("the count is too large");
      count = 10;
    } else {
      console.log(`the count is ${count}`);
      console.log("this will also be logged whenever count changes");
    }
  }

  function increment() {
    count += 1;
  }

  function addNumbers() {
    numbers.push(numbers.length + 1);
    numbers = numbers; // this is mandatory to trigger the reactive behavior
    // alternatively
    // numbers = [...numbers, numbers.length + 1];
    // yet another approach
    // numbers[numbers.length] = numbers.length + 1;
  }

  $: sum = numbers.reduce((t, n) => t + n, 0);
</script>

<h1>Hello {name.toUpperCase()}!</h1>
<img {src} alt="Favicon" />
<p>This is a paragraph.</p>
<Nested />
<p>{@html htmlText}</p>

<button on:click={increment}>Clicked {count} {count === 1 ? "count" : "counts"}</button>
<p>{count} doubled is {doubled}</p>

<button on:click={addNumbers}>Add a number</button>
<p>{numbers.join(" + ")} sum: {sum}</p>

<style>
  p {
    color: goldenrod;
    font-family: "Courier New", Courier, monospace;
    font-size: 2em;
  }
</style>
