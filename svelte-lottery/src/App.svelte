<script>
  class selected_numbers {
    constructor() {
      this.selected = [];
    }

    get() {
      return this.selected;
    }

    in(number) {
      return this.selected.includes(number);
    }

    add(number) {
      this.selected.push(number);
      this.selected = this.selected;
      return this;
    }

    remove(number) {
      let index = this.selected.indexOf(number);
      this.selected.splice(index, 1);
      return this;
    }

    is_complete() {
      if (this.selected >= 7) {
        return true;
      }
      return false;
    }
  }

  function range(size, start_at) {
    return [...Array(size).keys()].map((i) => i + start_at);
  }

  let loops = range(34, 1);
  let numbers = new selected_numbers();
</script>

<p>
  {numbers.get()}
</p>

<p>
  {#each loops as i}
    {#if numbers.selected.includes(i)}
      <button
        class="selected"
        on:click={() => {
          numbers = numbers.remove(i);
        }}>{i}</button
      >
    {:else}
      <button
        on:click={() => {
          numbers = numbers.add(i);
        }}>{i}</button
      >
    {/if}
  {/each}
</p>
