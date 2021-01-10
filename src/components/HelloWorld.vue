<template>
  <v-container>
    <table id="table_id" class="display">
      <thead>
        <tr>
          <th>Column 1</th>
          <th>Column 2</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Row 1 Data 1</td>
          <td>Row 1 Data 2</td>
        </tr>
        <tr>
          <td>Row 2 Data 1</td>
          <td>Row 2 Data 2</td>
        </tr>
      </tbody>
    </table>
  </v-container>
</template>

<script>
  window.$ = window.jquery = require('jquery');
  window.dt = require('datatables.net');

  export default {
    name: 'HelloWorld',

    data: () => ({
    }),

    mounted(){
      window.$('#table_id').DataTable({
        bPaginate: false,
        bInfo: false,
        searching: false,
      });
    }
  }
</script>
