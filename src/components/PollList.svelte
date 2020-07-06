<script>
  import PollDetails from '../components/PollDetails.svelte';

  export let polls = [
    {
      id: 0,
      question: 'Add your own poll!',
      answerA: 'Your option',
      answerB: 'Another one'
    }
  ];
</script>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
</style>

<div class="poll-list">
  {#each polls as poll (poll.id)}
    <div>
      <PollDetails {poll} on:vote />
    </div>
  {/each}
</div>
