<script>
  import Header from './components/Header.svelte';
  import Footer from './components/Footer.svelte';
  import PollList from './components/PollList.svelte';
  import CreatePollForm from './components/CreatePollForm.svelte';
  import Tabs from './shared/Tabs.svelte';

  // tabs
  let items = ['Current Polls', 'Add New Poll'];
  let activeItem = 'Current Polls';

  // polls
  let polls = [
    {
      id: 1,
      question: 'Python or JavaScript?',
      answerA: 'Python',
      answerB: 'JavaScript',
      votesA: 9,
      votesB: 15
    }
  ];

  const tabChange = e => {
    activeItem = e.detail;
  };

  const handleAdd = e => {
    const poll = e.detail;
    polls = [poll, ...polls];
    console.log(polls);
    activeItem = 'Current Polls';
  };

  const handleVote = e => {
    const { id, option } = e.detail;
    let copiedPolls = [...polls];
    let upvotedPoll = copiedPolls.find(poll => poll.id === id);
    option === 'a' ? upvotedPoll.votesA++ : upvotedPoll.votesB++;
    polls = copiedPolls;
  };
</script>

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>

<Header />
<main>
  <Tabs {activeItem} {items} on:tabChange={tabChange} />
  {#if activeItem === 'Current Polls'}
    <PollList {polls} on:vote={handleVote} />
  {:else if activeItem === 'Add New Poll'}
    <CreatePollForm on:add={handleAdd} />
  {/if}
</main>
<Footer />
