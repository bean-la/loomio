<script lang="coffee">
import PollFormOptionsMixin from '@/mixins/poll_form_options'

export default
  mixins: [PollFormOptionsMixin]

  props:
    poll: Object
    addOptionsOnly:
      type: Boolean
      default: false

  data: ->
    menu: false

</script>

<template lang="pug">
.poll-meeting-form-options
  poll-meeting-add-option-menu(@close="menu = false" :poll="poll")
  v-combobox.poll-meeting-time-field__datepicker-container(v-model="poll.pollOptionNames" @change="persistOptions()" multiple chips small-chips deletable-chips readonly :label="$t('poll_meeting_form.timeslots')")
    template(v-slot:selection="data")
      v-chip(:close="canRemove(data.item)" :color="colorFor(data.item)" @click:close="removeOptionName(data.item)")
        poll-meeting-time(:name="data.item")
  validation-errors(:subject="poll" field="pollOptions")
</template>
