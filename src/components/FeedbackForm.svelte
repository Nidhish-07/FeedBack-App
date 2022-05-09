<script>
  import { createEventDispatcher } from "svelte";
  import { v4 as uuidv4 } from "uuid";
  import Button from "../UI/Button.svelte";
  import Card from "../UI/Card.svelte";
  import RatingSelect from "../UI/RatingSelect.svelte";

  const dispatch = createEventDispatcher();
  let text = "";
  let rating = 10;
  let btnDisabled = true;
  let min = 10;
  let msg;

  const handleInput = function () {
    if (text.trim().length <= min) {
      msg = `Text must be atleast ${min} characters`;
      btnDisabled = true;
    } else {
      msg = null;
      btnDisabled = false;
    }
  };

  const handleSelect = function (e) {
    rating = e.detail;
  };

  const handleSubmit = function () {
    if (text.trim().length > min) {
      const newFeedback = { id: uuidv4(), text, rating: +rating };
      dispatch("add-feedback", newFeedback);
      text = "";
    }
  };
</script>

<Card>
  <header>
    <h2>How do you rate our service?</h2>
  </header>
  <form action="" on:submit|preventDefault={handleSubmit}>
    <RatingSelect on:rating-select={handleSelect} />
    <div class="input-group">
      <input
        type="text"
        bind:value={text}
        on:input={handleInput}
        name="feedback"
        id="feedback"
        placeholder="Tell us something"
      />
      <Button type="submit" disabled={btnDisabled}>Send</Button>
    </div>
    {#if msg}
      <div class="message">
        {msg}
      </div>
    {/if}
  </form>
</Card>
