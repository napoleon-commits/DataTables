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
                <div class="ma-auto" :style="`width: ${(windowWidth*goldenRatio)+4}px; border: 2px solid rgba(0,0,0,0.87)`">
                  <v-row no-gutters v-for="(n, rank) in 8" :key="rank" :style="``">
                    <v-col
                      v-for="(n, file) in 8" 
                      :key="file" 
                      :style="`
                        backgroundColor: ${
                        ((rank+file)%2===1)?'#FFF':'#888'
                        } !important;
                      `"
                    >
                    <div
                      v-if="pieceString[rank*8+file]==='x' || pieceString[rank*8+file]==='o'"
                      class="text-xl-h3 text-lg-h3 text-md-h3 text-sm-h3 text-subtitle-2"
                      style="color: rgba(0,0,0,0.87); text-align: center;"
                    >
                      <span v-if="pieceString[rank*8+file]==='x'">&times;</span>
                      <span v-else>&bull;</span>
                    </div>
                    <ChessPieceImage
                      :letter="pieceString[rank*8+file]"
                      :maxWidth="windowWidth*(goldenRatio)/8"
                      :maxHeight="windowHeight*(goldenRatio)/8"
                      v-else
                    />
                    </v-col>
                  </v-row>
                </div>
              </div>
            </v-list-item-title>
          </v-list-item>
        </v-list>
    </v-dialog>
    <div class="mt-5">
      <div class="ma-auto" :style="`width: ${windowWidth < 842 ? (windowWidth*goldenRatio)+4:(842*goldenRatio)+4}px; border: 2px solid rgba(0,0,0,0.87)`">
        <v-row no-gutters v-for="(n, rank) in 8" :key="rank" :style="``">
        <v-col
          v-for="(n, file) in 8" 
          :key="file" 
          :style="`
            backgroundColor: ${
            ((rank+file)%2===1)?'#FFF':'#888'
            } !important;
          `"
        >
        <div
          v-if="pieceString[rank*8+file]==='x' || pieceString[rank*8+file]==='o'"
          class="text-xl-h3 text-lg-h3 text-md-h3 text-sm-h3 text-subtitle-2"
          style="color: rgba(0,0,0,0.87); text-align: center;"
        >
          <span v-if="pieceString[rank*8+file]==='x'">&times;</span>
          <span v-else>&bull;</span>
        </div>
        <ChessPieceImage
          :letter="pieceString[rank*8+file]"
          :maxWidth="windowWidth*(goldenRatio)/8"
          :maxHeight="windowHeight*(goldenRatio)/8"
          v-else
        />
        </v-col>
        </v-row>
      </div>
    </div>
  </v-container>
</template>

<script>
  // import StaticChessBoard from '@/components/subcomponents/StaticChessBoard';
  import ChessPieceImage from '@/components/subcomponents/ChessPieceImage';
  import goldenRatio from '@/static/GoldenRatio';

  export default {
    name: 'HelloWorld',

    components: {
      // StaticChessBoard,
      ChessPieceImage,
    },

    data: () => ({
      pieceString:"rnbqkbnrpppppppp................................PPPPPPPPRNBQKBNR",
      goldenRatio,
      windowHeight: window.innerHeight,
      windowWidth: window.innerWidth,
    }),

    mounted(){
      this.$nextTick(() => {
            window.addEventListener('resize', this.onResize);
        });
    },
    methods: {
        onResize() {
            this.windowHeight = window.innerHeight;
            this.windowWidth = window.innerWidth;
        }
    },
    beforeDestroy() { 
        window.removeEventListener('resize', this.onResize); 
    },
    computed: {
      borderColor(){
            if(this.$vuetify.theme.dark){
                return 'white';
            }
            return 'grey';
        }
    }
  }
</script>
