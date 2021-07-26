<template>
  <div id="app">
    <div
      id="splashscreen"
      class="gentlebg"
      :style="{ display: showSplash ? '' : 'none' }"
    >
      <div id="splashGraph"></div>
      <div style="z-index: 20000;pointer-events: none; ">
        Clips Loaded: {{ Math.min(loadedShots, shotNames.length) }} of
        {{ shotNames.length }}
      </div>
      <div style="z-index: 20000">
        <a href="#" @click="clearSplashscreen()">Begin</a>
      </div>
    </div>
    <!--div style="display:none">
      <video controls v-for="shot in shotNames" :key="shot" preload="auto" @canplaythrough="incrementReady()">
        <source :src="`shots/${shot}.mp4`" type="video/mp4" >
      </video>
    </div-->
    <div style="width:100vw;display:flex;justify-content:center;">
      <!--<img :src="`shots/thumbnails/${currShot}.jpg`"-->
      <!--video controls preload="auto" autoplay :src="`shots/${currShot}.mp4`">
      </video-->
      <!-- :style="{display:(currShot == shot)?'':'none'}" -->
      <div style="position:relative;width: min(100vw, 990px);">
        <video
          v-for="shot in shotNames"
          :key="shot"
          preload="auto"
          @canplaythrough="incrementReady()"
          :style="{ zIndex: currShot == shot ? '100' : '10' }"
          :id="`video-${shot}`"
          :src="`shots/${shot}.mp4`"
          @ended="queueUpNextShot(shot)"
          style="width: min(100vw, 990px);position:absolute;top:0;left:0;"
        />
        <img src="shots/thumbnails/Adoors-24.jpg" />
      </div>
    </div>
  </div>
</template>

<script>
import _ from "lodash";
import cytoscape from "cytoscape";

export default {
  name: "App",
  components: {},
  computed: {},
  data() {
    return {
      showSplash: true,
      currShot: "ABindoors-125",
      loadedShots: 0,
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
          from: "AB",
          to: "Btalks",
        },
        {
          from: "AB",
          to: "Btalks",
        },
        {
          from: "AB",
          to: "Btalks",
        },
        {
          from: "AB",
          to: "Btalks",
        },
        {
          from: "AB",
          to: "Btalks",
        },
        {
          from: "AB",
          to: "Btalks",
        },
        {
          from: "AB",
          to: "CexitsRight",
        },
        {
          from: "AB",
          to: "Cstare",
        },
        {
          from: "AB",
          to: "Czoom",
        },
        {
          from: "ABindoors",
          to: "Adoors",
        },
        {
          from: "Adoors",
          to: "AwalkingLR",
        },
        {
          from: "Aenters",
          to: "Czoom",
        },
        {
          from: "AentersYells",
          to: "AtalksCries",
        },
        {
          from: "AexitBaloneClose",
          to: "AexitBaloneFar",
        },
        {
          from: "AexitBaloneFar",
          to: "Btalks",
        },
        {
          from: "AkneelingBenters",
          to: "BtalksDown",
        },
        {
          from: "AlookingBack",
          to: "AB",
        },
        {
          from: "Astanding",
          to: "Asun",
        },
        {
          from: "AstandsIntoAB",
          to: "Btalks",
        },
        {
          from: "Asun",
          to: "Aenters",
        },
        {
          from: "Atalks",
          to: "AB",
        },
        {
          from: "Atalks",
          to: "Btalks",
        },
        {
          from: "Atalks",
          to: "Btalks",
        },
        {
          from: "Atalks",
          to: "Btalks",
        },
        {
          from: "Atalks",
          to: "Btalks",
        },
        {
          from: "Atalks",
          to: "Btalks",
        },
        {
          from: "Atalks",
          to: "Cblink",
        },
        {
          from: "Atalks",
          to: "Cblink",
        },
        {
          from: "Atalks",
          to: "Cclose",
        },
        {
          from: "Atalks",
          to: "Cclose",
        },
        {
          from: "Atalks",
          to: "Czoom",
        },
        {
          from: "AtalksBbackground",
          to: "Btalks",
        },
        {
          from: "AtalksCries",
          to: "AtalksCriesIntoKneeling",
        },
        {
          from: "AtalksCriesIntoKneeling",
          to: "AkneelingBenters",
        },
        {
          from: "AtalksCriesKneeling",
          to: "BtalksDown",
        },
        {
          from: "AtalksSide",
          to: "Cfar",
        },
        {
          from: "AtalksSide",
          to: "Czoom",
        },
        {
          from: "AwalkingLR",
          to: "Astanding",
        },
        {
          from: "AzoomTears",
          to: "END",
        },
        {
          from: "BrunningLR",
          to: "AlookingBack",
        },
        {
          from: "Btalks",
          to: "AB",
        },
        {
          from: "Btalks",
          to: "AB",
        },
        {
          from: "Btalks",
          to: "AB",
        },
        {
          from: "Btalks",
          to: "AB",
        },
        {
          from: "Btalks",
          to: "AB",
        },
        {
          from: "Btalks",
          to: "AB",
        },
        {
          from: "Btalks",
          to: "AB",
        },
        {
          from: "Btalks",
          to: "AentersYells",
        },
        {
          from: "Btalks",
          to: "Atalks",
        },
        {
          from: "Btalks",
          to: "Atalks",
        },
        {
          from: "Btalks",
          to: "Atalks",
        },
        {
          from: "Btalks",
          to: "Atalks",
        },
        {
          from: "Btalks",
          to: "Atalks",
        },
        {
          from: "Btalks",
          to: "Atalks",
        },
        {
          from: "Btalks",
          to: "AtalksBbackground",
        },
        {
          from: "Btalks",
          to: "AzoomTears",
        },
        {
          from: "BtalksDown",
          to: "AstandsIntoAB",
        },
        {
          from: "BtalksDown",
          to: "AtalksCriesKneeling",
        },
        {
          from: "Cblink",
          to: "Atalks",
        },
        {
          from: "Cblink",
          to: "Btalks",
        },
        {
          from: "Cclose",
          to: "AtalksSide",
        },
        {
          from: "Cclose",
          to: "BrunningLR",
        },
        {
          from: "CexitsRight",
          to: "AexitBaloneClose",
        },
        {
          from: "Cfar",
          to: "AtalksSide",
        },
        {
          from: "Cstare",
          to: "Atalks",
        },
        {
          from: "Cstare",
          to: "Btalks",
        },
        {
          from: "Czoom",
          to: "Atalks",
        },
        {
          from: "Czoom",
          to: "Atalks",
        },
        {
          from: "Czoom",
          to: "Atalks",
        },
        {
          from: "Czoom",
          to: "Cstare",
        },
        {
          from: "START",
          to: "Abindoors",
        },
      ],
    };
  },
  methods: {
    clearSplashscreen: function() {
      this.showSplash = false;
      this.queueUpNextShot();
    },
    incrementReady: function() {
      this.loadedShots++;
    },
    queueUpNextShot: function(caller = null) {
      if (this.showSplash) {
        return;
      }
      if (caller != null && caller != this.currShot) {
        return;
      }
      let lastShotVideo = document.getElementById(`video-${this.currShot}`);

      // Given current shot, select a random markov transition and note the to shot
      let nextShotBaseName = _.sample(
        _.filter(
          this.authenticMarkovTransitions,
          (transition) => transition.from == this.currShot.split("-")[0]
        )
      ).to;
      if (nextShotBaseName == "END") {
        nextShotBaseName = "ABindoors";
      }

      let nextShot = _.sample(
        _.filter(this.shotNames, (shot) => shot.startsWith(nextShotBaseName))
      );
      let shotVideo = document.getElementById(`video-${nextShot}`);
      shotVideo.currentTime = 0;
      shotVideo.play();
      this.currShot = nextShot;

      // Cleanup!
      lastShotVideo.currentTime = 0;
    },
  },
  mounted() {
    let elements = [];

    // Some ECMAScript 2017 goodness
    function noDupes2(...args) {
      return [].concat(...args).filter((v, i, arr) => arr.indexOf(v) == i);
    }

    noDupes2(this.shotNames.map((x) => x.split("-")[0])).forEach((shotName) => {
      elements.push({
        group: "nodes",
        data: {
          id: shotName,
        },
      });
    });

    this.authenticMarkovTransitions.forEach((transition, i) => {
      if (transition.to != "END" && transition.from != "START") {
        elements.push({
          group: "edges",
          data: {
            id: `edge${i}`,
            source: transition.from,
            target: transition.to,
          },
        });
      }
    });

    let cy = cytoscape({
      wheelSensitivity: 0.3,
      /*userZoomingEnabled: false,
      userPanningEnabled: false,
      boxSelectionEnabled: false,
      autoungrabify: true,
      autolock: true,*/
      container: document.getElementById("splashGraph"),
      elements: elements,
      style: [
        {
          selector: "node",
          style: {
            "background-color": "#F5876F",
            width: "5",
            height: "5",
          },
        },

        {
          selector: "edge",
          style: {
            width: 0.8,
            "line-color": "#F7A9A8",
            "target-arrow-color": "#F2A58F",
            "target-arrow-shape": "triangle",
            "curve-style": "straight",
            "line-dash-pattern": [1, 1],
            "arrow-scale": 0.6,
          },
        },
      ],
      //layout: ,
    });

    cy.elements().layout({
      name: "cose",
      fit: true,
      animate: false,
      padding: 50,
      randomize: true,
    }).run();
  },
};
</script>

<style lang="scss">
#app {
  background-color: #222;
  height: 100vh;
  text-align: center;
  color: white;

  display: flex;
  place-items: center;
  overflow: hidden;
}

#splashscreen {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 10000;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  font-size: 4em;
}

#splashscreen a {
  color: white;
}

#splashscreen a:visited {
  color: white;
}

#splashGraph {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 10001;
}

// I guess I'm bugfixing cytoscape.js now
#splashGraph div canvas {
  left: 0;
}

.gentlebg {
  background: rgb(229, 135, 76);
  background: linear-gradient(
    125deg,
    rgba(229, 135, 76, 1) 0%,
    rgba(245, 203, 135, 1) 33%,
    rgba(253, 210, 184, 1) 100%
  );
}
</style>
