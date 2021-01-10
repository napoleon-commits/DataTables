<template>
  <v-container>
    <v-dialog>
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          v-bind="attrs"
          v-on="on"
        >
          DataTable table
        </v-btn>
      </template>
      <v-list>
          <v-list-item>
            <v-list-item-title class="text-wrap">
              <span>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur dictum,
                tortor eu rhoncus lobortis, velit urna lacinia dui, eget blandit justo diam vitae nibh. 
                Pellentesque aliquet laoreet pretium. Quisque hendrerit tellus ut nisl feugiat, a laoreet est luctus.
              </span>
              <div class="mt-3">
                <StaticChessBoard
                  pieceString="rnbqkbnrpppppppp................................PPPPPPPPRNBQKBNR"
                />
              </div>
            </v-list-item-title>
          </v-list-item>
        </v-list>
    </v-dialog>
  </v-container>
</template>

<script>
  import StaticChessBoard from '@/components/subcomponents/StaticChessBoard';

  export default {
    name: 'HelloWorld',

    components: {
      StaticChessBoard,
    },

    data: () => ({
    }),

    mounted(){
      // window.$('#table_id').DataTable({
      //   bPaginate: false,
      //   bInfo: false,
      //   searching: false,
      // });
    }
  }
</script>
