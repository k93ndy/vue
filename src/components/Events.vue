<template>
  <table>
    <caption><strong>Events</strong></caption>
    <thead>
      <tr>
        <th>Title</th>
        <th>Memo</th>
        <th>Number of participants</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="event in events" :key="event.id">
        <td>{{ event.title }}</td>
        <td>{{ event.memo }}</td>
        <td>{{ event.num_of_participants }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'Events',
  data() {
    return {
      events: [],
      connectionStatus: 'loading'
    }
  },
  created: function() {
    axios.get('https://www.splitthebill.ml/api/v1alpha/events/')
    .then(function (response) {
      events.connectionStatus = 'Data loaded.'
      events.events = response.data
    })
    .catch(function (error) {
      events.connectionStatus = 'Failed in loading data.'
    })
  }
}
</script>

<style>
table, th, td {
  border-style: solid;
  border-color: cornflowerblue;
  border-width: 0.1rem;
}
</style>
