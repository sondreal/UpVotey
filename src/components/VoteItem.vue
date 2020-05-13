<template>
  <div>
    <div class="section">
      <article class="media">
        <figure class="media-left">
          <img
            :src="require(`@/assets/images/submissions/${upVotesImage}.png`)"
            alt=""
            class="image is-64x64"
          />
        </figure>
        <div class="media-content">
          <div class="content">
            <p>
              <strong>
                <a href="">{{ upVotesTitle }}</a>
                <span class="tag is-small">#{{ upVotesNumberTag }}</span>
              </strong>
              <br />
              {{ upVotesText }}
              <br />
              <small class="is-size-7">
                Submitted by {{ upVotesSumbitter }}
                <img
                  :src="require(`@/assets/images/avatars/${upVotesAvatar}.jpg`)"
                  class="image is-24x24"
                  alt=""
                />
              </small>
            </p>
          </div>
        </div>
        <div class="media-right">
          <span class="icon is-small" v-on:click="upvote(upVotesNumberTag)">
            <i class="fa fa-chevron-up"></i>
            <strong class="has-text-info">{{ upVotes }}</strong>
          </span>
        </div>
      </article>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    "upVotes",
    "upVotesText",
    "upVotesNumberTag",
    "upVotesTitle",
    "upVotesSumbitter",
    "upVotesImage",
    "upVotesAvatar"
  ],
  methods: {
    upvote(submissionId) {
      this.$emit("update-votes", submissionId);
    }
  },
};
</script>

<style lang="scss" scoped>
.section {
  padding: 2rem 1.5rem;
}

.media {
  max-width: 600px;
  margin: 0 auto;
  border: 1px solid #e6e7e9;
  padding: 1em 1.5em 0.5em 1.5em;
  border-radius: 0.3em;
}

.media + .media {
  margin-top: 1.5rem;
}

.blue-border {
  border: 1px solid #3373dc !important;
}

.tag {
  font-size: 0.6rem !important;
}

.icon {
  cursor: pointer;
}

.image.is-24x24 {
  display: inline;
  position: relative;
  top: 5px;
  border-radius: 20px;
}
</style>
