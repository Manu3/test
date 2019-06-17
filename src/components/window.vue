<template>
  <div>
    <button id="save">Descargar</button>
    <v-stage ref="stage" :config="configKonva">
      <v-layer>
        <v-rect v-for="item in square" :key="item.id" :config="item"/>
      </v-layer>
      <v-layer>
        <v-shape :config="configShape"/>
      </v-layer>
      <v-layer>
        <v-line :config="configLine"/>
      </v-layer>
      <v-layer>
        <v-shape :config="configShapeOne"/>
      </v-layer>
    </v-stage>
  </div>
</template>

<script>
import methods from "../../server/method";
var metodo = methods.msg();
let vm = {};
let color = "red";
export default {
  props: ["color"],
  data() {
    return {
      configKonva: {
        width: 1000,
        height: 500
      },
      square: [
        {
          x: 101,
          y: 20,
          width: 850,
          height: 450,
          fill: "white",
          stroke: "black",
          strokeWidth: 4,
          name: "rect1"
        }
      ],
      configShape: {
        sceneFunc: function(context) {
          context.beginPath();
          context.moveTo(105, -5);
          context.lineTo(105, 446);
          context.closePath();
          context.fillStrokeShape(this);
        },
        x: 450,
        y: 25,
        fill: "#00D2FF",
        stroke: "black",
        strokeWidth: 4,
        draggable: false
      },
      configShapeOne: {
        sceneFunc: function(context) {
          context.beginPath();
          context.moveTo(-112, 255);
          context.lineTo(300, 255);
          context.closePath();
          context.fillStrokeShape(this);
        },
        x: 450,
        y: 25,
        fill: "#00D2FF",
        stroke: "black",
        strokeWidth: 4,
        draggable: false
      },
      configLine: {
        x: 450,
        y: 25,
        points: [-350, -7, -347, 442, 80, 99, 130, 100, 500, 440, 500, -5],
        fill: this.color,
        stroke: "black",
        strokeWidth: 5,
        closed: true,
        tension: 0,
        /*fillLinearGradientStartPoint: { x: -50, y: -50 },
        fillLinearGradientEndPoint: { x: 50, y: 50 },
        fillLinearGradientColorStops: [0, "red", 1, "yellow"], */
        draggable: false
      }
    };
  }
};
</script>

