<template>
  <div id="app">
    <div style="width:100vw">
      <img :src="`shots/thumbnails/${currShot}.jpg`">
    </div>
  </div>
</template>

<script>
import _ from 'lodash';

export default {
  name: 'App',
  components: {
  },
  computed: {
    laneIds() { // XXX remove me
      return _.range(4);
    }
  },
  data() {
    return {
      currShot: "ABindoors-125",
      shotNames: [
        "ABindoors-125",
        "Adoors-24",
        "AwalkingLR-46",
        "Astanding-53",
        "Asun-42",
        "Aenters-23",
        "Czoom-41",
        "Atalks-89",
        "Cclose-47",
        "AtalksSide-108",
        "Cfar-7",
        "AtalksSide-70",
        "Czoom-33",
        "Atalks-28",
        "Cblink-51",
        "Atalks-56a",
        "Czoom-57",
        "Atalks-36",
        "Cclose-42",
        "BrunningLR-27",
        "AlookingBack-20",
        "AB-76",
        "Btalks-27a",
        "AB-14",
        "Btalks-42a",
        "AtalksBbackground-22",
        "Btalks-14",
        "AB-31",
        "Czoom-9",
        "Cstare-26",
        "Btalks-42b",
        "AB-87",
        "Cstare-31",
        "Atalks-57",
        "Btalks-33",
        "AB-62",
        "Btalks-51a",
        "Atalks-27",
        "Btalks-76",
        "AB-39",
        "Btalks-51b",
        "AB-35",
        "Btalks-13a",
        "Atalks-56b",
        "Cblink-33",
        "Btalks-27b",
        "AB-38",
        "Btalks-28",
        "Atalks-110",
        "Btalks-11",
        "Atalks-58",
        "Btalks-13b",
        "Atalks-83",
        "Btalks-24",
        "Atalks-13",
        "AB-33",
        "CexitsRight-26",
        "AexitBaloneClose-17",
        "AexitBaloneFar-21",
        "Btalks-19",
        "AentersYells-49",
        "AtalksCries-35",
        "AtalksCriesIntoKneeling-14",
        "AkneelingBenters-30",
        "BtalksDown-16",
        "AtalksCriesKneeling-53",
        "BtalksDown-31",
        "AstandsIntoAB-68",
        "Btalks-80",
        "AzoomTears-84",
      ],
      authenticMarkovTransitions: [
        {
          from:"AB",
          to:"Btalks",
        },
        {
          from:"AB",
          to:"Btalks",
        },
        {
          from:"AB",
          to:"Btalks",
        },
        {
          from:"AB",
          to:"Btalks",
        },
        {
          from:"AB",
          to:"Btalks",
        },
        {
          from:"AB",
          to:"Btalks",
        },
        {
          from:"AB",
          to:"CexitsRight",
        },
        {
          from:"AB",
          to:"Cstare",
        },
        {
          from:"AB",
          to:"Czoom",
        },
        {
          from:"ABindoors",
          to:"Adoors",
        },
        {
          from:"Adoors",
          to:"AwalkingLR",
        },
        {
          from:"Aenters",
          to:"Czoom",
        },
        {
          from:"AentersYells",
          to:"AtalksCries",
        },
        {
          from:"AexitBaloneClose",
          to:"AexitBaloneFar",
        },
        {
          from:"AexitBaloneFar",
          to:"Btalks",
        },
        {
          from:"AkneelingBenters",
          to:"BtalksDown",
        },
        {
          from:"AlookingBack",
          to:"AB",
        },
        {
          from:"Astanding",
          to:"Asun",
        },
        {
          from:"AstandsIntoAB",
          to:"Btalks",
        },
        {
          from:"Asun",
          to:"Aenters",
        },
        {
          from:"Atalks",
          to:"AB",
        },
        {
          from:"Atalks",
          to:"Btalks",
        },
        {
          from:"Atalks",
          to:"Btalks",
        },
        {
          from:"Atalks",
          to:"Btalks",
        },
        {
          from:"Atalks",
          to:"Btalks",
        },
        {
          from:"Atalks",
          to:"Btalks",
        },
        {
          from:"Atalks",
          to:"Cblink",
        },
        {
          from:"Atalks",
          to:"Cblink",
        },
        {
          from:"Atalks",
          to:"Cclose",
        },
        {
          from:"Atalks",
          to:"Cclose",
        },
        {
          from:"Atalks",
          to:"Czoom",
        },
        {
          from:"AtalksBbackground",
          to:"Btalks",
        },
        {
          from:"AtalksCries",
          to:"AtalksCriesIntoKneeling",
        },
        {
          from:"AtalksCriesIntoKneeling",
          to:"AkneelingBenters",
        },
        {
          from:"AtalksCriesKneeling",
          to:"BtalksDown",
        },
        {
          from:"AtalksSide",
          to:"Cfar",
        },
        {
          from:"AtalksSide",
          to:"Czoom",
        },
        {
          from:"AwalkingLR",
          to:"Astanding",
        },
        {
          from:"AzoomTears",
          to:"END",
        },
        {
          from:"BrunningLR",
          to:"AlookingBack",
        },
        {
          from:"Btalks",
          to:"AB",
        },
        {
          from:"Btalks",
          to:"AB",
        },
        {
          from:"Btalks",
          to:"AB",
        },
        {
          from:"Btalks",
          to:"AB",
        },
        {
          from:"Btalks",
          to:"AB",
        },
        {
          from:"Btalks",
          to:"AB",
        },
        {
          from:"Btalks",
          to:"AB",
        },
        {
          from:"Btalks",
          to:"AentersYells",
        },
        {
          from:"Btalks",
          to:"Atalks",
        },
        {
          from:"Btalks",
          to:"Atalks",
        },
        {
          from:"Btalks",
          to:"Atalks",
        },
        {
          from:"Btalks",
          to:"Atalks",
        },
        {
          from:"Btalks",
          to:"Atalks",
        },
        {
          from:"Btalks",
          to:"Atalks",
        },
        {
          from:"Btalks",
          to:"AtalksBbackground",
        },
        {
          from:"Btalks",
          to:"AzoomTears",
        },
        {
          from:"BtalksDown",
          to:"AstandsIntoAB",
        },
        {
          from:"BtalksDown",
          to:"AtalksCriesKneeling",
        },
        {
          from:"Cblink",
          to:"Atalks",
        },
        {
          from:"Cblink",
          to:"Btalks",
        },
        {
          from:"Cclose",
          to:"AtalksSide",
        },
        {
          from:"Cclose",
          to:"BrunningLR",
        },
        {
          from:"CexitsRight",
          to:"AexitBaloneClose",
        },
        {
          from:"Cfar",
          to:"AtalksSide",
        },
        {
          from:"Cstare",
          to:"Atalks",
        },
        {
          from:"Cstare",
          to:"Btalks",
        },
        {
          from:"Czoom",
          to:"Atalks",
        },
        {
          from:"Czoom",
          to:"Atalks",
        },
        {
          from:"Czoom",
          to:"Atalks",
        },
        {
          from:"Czoom",
          to:"Cstare",
        },
        {
          from:"START",
          to:"Abindoors",
        },
      ],
    }
  },
  methods: {
    queueUpNextShot: function () {      
      // Given current shot, select a random markov transition and note the to shot
      //this.currShot = _.sample(_.filter(this.authenticMarkovTransitions, (transition) => (transition.from == this.currShot)));
      let nextShotBaseName = _.sample(_.filter(this.authenticMarkovTransitions, (transition) => (transition.from == this.currShot.split('-')[0]))).to;
      if (nextShotBaseName == 'END') {
        nextShotBaseName = 'ABindoors';
      }
      this.currShot = _.sample(_.filter(this.shotNames, (shot) => (shot.startsWith(nextShotBaseName))));
      // Get frames of selected destination shot, and use that to time the next transition
      if (this.currShot != undefined) {
        setTimeout(() => {
          this.queueUpNextShot();
        }, this.currShot.split('-')[1]*(1000.0/30.0));
        console.log(this.currShot.split('-')[1]*(1000.0/30.0))
      }
    },
  },
  mounted() {
    this.queueUpNextShot();
  },
}
</script>


<style lang="scss">
#app {
  background-color: #222;
  height: 100vh;
  text-align: center;
  color: white;

  display: flex;
  place-items: center;
}

</style>
