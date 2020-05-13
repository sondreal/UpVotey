<template>
  <div class="home">
    <h2 class="title has-text-centered dividing-header">UpVotey!</h2>
    <VoteItem
      v-for="submission in sortedSubmissions"
      :key="submission.id"
      :upVotesText="submission.description"
      :upVotesNumberTag="submission.id"
      :upVotesTitle="submission.title"
      :upVotesSumbitter="submission.submitter"
      :upVotes="submission.votes"
      :upVotesImage="submission.submissionImage"
      :upVotesAvatar="submission.avatar"
      @update-votes="updateVotes"
    />
  </div>
</template>

<script>
import VoteItem from "@/components/VoteItem.vue";

export default {
  components: {
    VoteItem
  },
  data() {
    return {
      submissions: [
        {
          id: 1,
          title: "Code Vue",
          description: "I will code VueJS all day.",
          url: "#",
          votes: 16,
          avatar: "daniel",
          submissionImage: "image-aqua",
          submitter: "Sondre"
        },
        {
          id: 2,
          title: "Laravel all day",
          description: "Laravel all day! ! !.",
          url: "#",
          votes: 20,
          avatar: "daniel",
          submissionImage: "image-rose",
          submitter: "Sondre"
        },
        {
          id: 3,
          title: "DevOps",
          description: "We will create some dank server networks on stream.",
          url: "#",
          votes: 14,
          avatar: "daniel",
          submissionImage: "image-yellow",
          submitter: "Sondre"
        },
        {
          id: 4,
          title: "GoLang",
          description: "We will make some really dank software with GoLang.",
          url: "#",
          votes: 7,
          avatar: "daniel",
          submissionImage: "image-steel",
          submitter: "Sondre"
        }
        // ...
        // ...
      ]
    };
  },
  computed: {
    sortedSubmissions () {
      return this.submissions.slice().sort((a, b) => {
        return b.votes - a.votes;
      });
    }
  },
  methods: {
    updateVotes(e) {
      const submission = this.submissions.find(
        submission => submission.id === e
      );
      submission.votes++;
    }
  }
};
</script>

<style lang="scss" scoped>
.dividing-header {
  margin-top: 1em;
  margin-bottom: 2em;
}
</style>
