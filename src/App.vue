<template>
  <div id="app">
    <div id="splashscreen" class="gentlebg" v-if="showSplash">
      <div id="splashGraph"></div>
      <div style="z-index: 20000;pointer-events: none; text-shadow: 3px 3px 3px black;">
        Super Markov Robot Solar 123: <br><i>An Infinite Drama</i>
      </div>
      <div style="z-index: 20000">
        <div style="display:flex;flex-direction:column;">
          <a style="display: block;margin-bottom:60px" v-if="videoLoaded" href="#" @click="clearSplashscreen()">Begin 🔈</a>
          <a style="display: block;" v-if="videoLoaded" href="#" @click="clearSplashscreen(true)">Begin 🔊</a>
          <template v-else>Loading video...</template>
        </div>
      </div>
    </div>
    <div style="width:100vw;height:100vh;display:flex;justify-content:center;align-items:center;">
      <audio src="audioblocks-the-endgame_BnG_uQ_Xw-SBA-300504840.mp3" id="dramaticMusic" loop style="height:0;width:0;" /> 
      <div style="position:relative;width: min(100vw, 990px);height:720px;z-index:2;">
        <video
          muted
          preload="auto"
          id="dramaclip"
          style="width: min(100vw, 990px);height:720px;position:absolute;top:0;left:0;"
        />
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
      currShot: "START",
      videoLoaded: 0,
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
        "AtalksSide-68",
        "Cfar-47",
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
        "AtalksCries-34",
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
          from: "START",
          to: "ABindoors-125",
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
          to: "ABindoors",
        },
      ],
      shotTimings: {
          "ABindoors-125": {
            startFrame: 1,
            numFrames: 125
          },
"Adoors-24": {
            startFrame: 126,
            numFrames: 24
          },
"AwalkingLR-46": {
            startFrame: 150,
            numFrames: 46
          },
"Astanding-53": {
            startFrame: 196,
            numFrames: 53
          },
"Asun-42": {
            startFrame: 249,
            numFrames: 42
          },
"Aenters-23": {
            startFrame: 291,
            numFrames: 23
          },
"Czoom-41": {
            startFrame: 314,
            numFrames: 41
          },
"Atalks-89": {
            startFrame: 355,
            numFrames: 89
          },
"Cclose-47": {
            startFrame: 444,
            numFrames: 47
          },
"AtalksSide-68": {
            startFrame: 491,
            numFrames: 68
          },
"Cfar-47": {
            startFrame: 559,
            numFrames: 47
          },
"AtalksSide-70": {
            startFrame: 606,
            numFrames: 70
          },
"Czoom-33": {
            startFrame: 676,
            numFrames: 33
          },
"Atalks-28": {
            startFrame: 709,
            numFrames: 28
          },
"Cblink-51": {
            startFrame: 737,
            numFrames: 51
          },
"Atalks-56a": {
            startFrame: 788,
            numFrames: 56
          },
"Czoom-57": {
            startFrame: 844,
            numFrames: 57
          },
"Atalks-36": {
            startFrame: 901,
            numFrames: 36
          },
"Cclose-42": {
            startFrame: 937,
            numFrames: 42
          },
"BrunningLR-27": {
            startFrame: 979,
            numFrames: 27
          },
"AlookingBack-20": {
            startFrame: 1006,
            numFrames: 20
          },
"AB-76": {
            startFrame: 1026,
            numFrames: 76
          },
"Btalks-27a": {
            startFrame: 1102,
            numFrames: 27
          },
"AB-14": {
            startFrame: 1129,
            numFrames: 14
          },
"Btalks-42a": {
            startFrame: 1143,
            numFrames: 42
          },
"AtalksBbackground-22": {
            startFrame: 1185,
            numFrames: 22
          },
"Btalks-14": {
            startFrame: 1207,
            numFrames: 14
          },
"AB-31": {
            startFrame: 1221,
            numFrames: 31
          },
"Cstare-26": {
            startFrame: 1261,
            numFrames: 26
          },
"Btalks-42b": {
            startFrame: 1287,
            numFrames: 42
          },
"AB-87": {
            startFrame: 1329,
            numFrames: 87
          },
"Cstare-31": {
            startFrame: 1416,
            numFrames: 31
          },
"Atalks-57": {
            startFrame: 1447,
            numFrames: 57
          },
"Btalks-33": {
            startFrame: 1504,
            numFrames: 33
          },
"AB-62": {
            startFrame: 1537,
            numFrames: 62
          },
"Btalks-51a": {
            startFrame: 1599,
            numFrames: 51
          },
"Atalks-27": {
            startFrame: 1650,
            numFrames: 27
          },
"Btalks-76": {
            startFrame: 1677,
            numFrames: 76
          },
"AB-39": {
            startFrame: 1753,
            numFrames: 39
          },
"Btalks-51b": {
            startFrame: 1792,
            numFrames: 51
          },
"AB-35": {
            startFrame: 1843,
            numFrames: 35
          },
"Btalks-13a": {
            startFrame: 1878,
            numFrames: 13
          },
"Atalks-56b": {
            startFrame: 1891,
            numFrames: 56
          },
"Cblink-33": {
            startFrame: 1947,
            numFrames: 33
          },
"Btalks-27b": {
            startFrame: 1980,
            numFrames: 27
          },
"AB-38": {
            startFrame: 2007,
            numFrames: 38
          },
"Btalks-28": {
            startFrame: 2045,
            numFrames: 28
          },
"Atalks-110": {
            startFrame: 2073,
            numFrames: 110
          },
"Btalks-11": {
            startFrame: 2183,
            numFrames: 11
          },
"Atalks-58": {
            startFrame: 2194,
            numFrames: 58
          },
"Btalks-13b": {
            startFrame: 2252,
            numFrames: 13
          },
"Atalks-83": {
            startFrame: 2265,
            numFrames: 83
          },
"Btalks-24": {
            startFrame: 2348,
            numFrames: 24
          },
"Atalks-13": {
            startFrame: 2372,
            numFrames: 13
          },
"AB-33": {
            startFrame: 2385,
            numFrames: 33
          },
"CexitsRight-26": {
            startFrame: 2418,
            numFrames: 26
          },
"AexitBaloneClose-17": {
            startFrame: 2444,
            numFrames: 17
          },
"AexitBaloneFar-21": {
            startFrame: 2461,
            numFrames: 21
          },
"Btalks-19": {
            startFrame: 2482,
            numFrames: 19
          },
"AentersYells-49": {
            startFrame: 2501,
            numFrames: 49
          },
"AtalksCries-34": {
            startFrame: 2550,
            numFrames: 34
          },
"AtalksCriesIntoKneeling-14": {
            startFrame: 2585,
            numFrames: 14
          },
"AkneelingBenters-30": {
            startFrame: 2599,
            numFrames: 30
          },
"BtalksDown-16": {
            startFrame: 2629,
            numFrames: 16
          },
"AtalksCriesKneeling-53": {
            startFrame: 2645,
            numFrames: 53
          },
"BtalksDown-31": {
            startFrame: 2698,
            numFrames: 31
          },
"AstandsIntoAB-68": {
            startFrame: 2729,
            numFrames: 68
          },
"Btalks-80": {
            startFrame: 2797,
            numFrames: 80
          },
"AzoomTears-84": {
            startFrame: 2877,
            numFrames: 84
          },
      },
    };
  },
  methods: {
    clearSplashscreen: function(playMusic = false) {
      this.showSplash = false;
      this.queueUpNextShot();
      if (playMusic) {
        document.getElementById('dramaticMusic').play();
      }
    },
    queueUpNextShot: function(caller = null) {
      if (this.showSplash) {
        return;
      }
      if (caller != null && caller != this.currShot) {
        return;
      }

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
      console.log(nextShotBaseName)

      let nextShot = _.sample(
        _.filter(this.shotNames, (shot) => shot.startsWith(nextShotBaseName))
      );
      let nextShotStartTime = (this.shotTimings[nextShot].startFrame-1) * (1/29.97);
      let videoElement = document.getElementById('dramaclip');
      videoElement.currentTime = nextShotStartTime;
      videoElement.play();

      let numFrames = this.shotTimings[nextShot].numFrames-1;

      if (nextShot == 'AzoomTears-84') {
        // Let fade to black play through properly
        numFrames = 250;
      }

      let that = this;
      setTimeout(() => {
        that.queueUpNextShot();
      }, (numFrames) * (1000/29.97));

      this.currShot = nextShot;
    },
  },
  async mounted() {
    // Validate data all matches
    console.log(_.difference(this.shotNames, Object.keys(this.shotTimings)))
    console.log(_.difference(Object.keys(this.shotTimings), this.shotNames))

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

    // Download video
    let videoFile = await (await fetch('dramaclip.mp4')).blob();
    this.videoLoaded = true;
    document.getElementById('dramaclip').src = URL.createObjectURL(videoFile);
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
  width: 100vw;
  height: 100vh;
  z-index: 10000;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  font-size: 5vw;

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
