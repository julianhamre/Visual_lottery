<script>
  class selected_numbers {
    constructor() {
      this.selected = [];
    }

    add(number) {
      this.selected.push(number);
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

<h1>Select the 7 winning numbers</h1>

<div class="show_selected">
  <p>Selected numbers:</p>
  {#each numbers.selected as number}
    <div class="lottery_ball preview_ball selected">
      {number}
    </div>
  {/each}
</div>

<div class="select_cupon">
  {#each loops as i}
    {#if numbers.selected.includes(i)}
      <button
        class="lottery_ball selectable_ball selected"
        on:click={() => {
          numbers = numbers.remove(i);
        }}>{i}</button
      >
    {:else}
      <button
        class="lottery_ball selectable_ball"
        on:click={() => {
          numbers = numbers.add(i);
        }}>{i}</button
      >
    {/if}
  {/each}
</div>
