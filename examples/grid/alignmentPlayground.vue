<template>
  <div>
    <v-container grid-list-md>
      <v-layout v-bind="layoutProps">
        <v-flex xs1 v-for="i in 3" :key="`${i}`">
          <v-card dark color="primary">
            <v-card-text class="px-0 text-xs-center">{{i}}</v-card-text>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
    <v-container grid-list-xs>
      <v-layout row wrap justify-center>
        <v-flex xs12>
          <v-card color="secondary">
            <v-card-title class="headline code"><code>&lt;v-layout {{ allProps }}&gt;</code></v-card-title>
            <v-card-text class="grey lighten-2">
              <v-layout row wrap>
               <v-flex xs12 md2>
                  <v-radio-group label="Direction" v-model="direction">
                    <v-radio
                      v-for="dir in directions"
                      :key="dir"
                      :label="dir"
                      :value="dir"
                    ></v-radio>
                  </v-radio-group>
                </v-flex>
                <v-flex xs12 md5>
                  <v-radio-group label="Justify (Same direction)" v-model="justify">
                    <v-radio
                      v-for="opt in justifyOptions"
                      :key="opt"
                      :label="`justify-${opt}`"
                      :value="`justify-${opt}`"
                    ></v-radio>
                  </v-radio-group>
                </v-flex>
                <v-flex xs12 md5>
                  <v-radio-group label="Alignment (Perpendicular direction)" v-model="align">
                    <v-radio
                      v-for="opt in alignOptions"
                      :key="opt"
                      :label="`align-${opt}`"
                      :value="`align-${opt}`"
                    ></v-radio>
                  </v-radio-group>
                </v-flex>

              </v-layout>
            </v-card-text>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
export default {

  name: 'AlignmentPlayground',

  data () {
    return {
      justifyOptions: ['start', 'center', 'end', 'space-around', 'space-between'],
      alignOptions: ['baseline', 'center', 'content-center', 'content-space-around', 'content-space-between', 'content-start', 'start', 'end'],
      directions: ['row', 'column'],
      direction: 'row',
      align: 'center',
      justify: 'justify-center',
    }
  },
  computed: {
    layoutProps() {
      return {
        [this.justify]: true,
        [this.align]: true,
        [this.direction]: true,
      }
    },
    allProps() {
      return `${this.justify} ${this.align} ${this.direction}`
    },
  }
}
</script>
