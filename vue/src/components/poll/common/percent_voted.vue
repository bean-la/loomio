<script lang="coffee">
export default
  props:
    poll: Object
</script>

<template>
  <span class="text--secondary" v-if="poll.closingAt" v-t="{ path: 'poll_common_percent_voted.sentence', args: { numerator: poll.decidedVotersCount, denominator: poll.votersCount, percent: poll.castStancesPct } }"></span>
</template>
