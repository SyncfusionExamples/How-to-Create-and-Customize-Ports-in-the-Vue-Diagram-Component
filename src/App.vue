<template>
  <div class="container">
    <ejs-button class="button" @click="removePort">Remove Port</ejs-button>
    <ejs-button class="button" @click="updatePort">Update Port</ejs-button>
  </div>
  <ejs-diagram ref="diagramObject" :width="width" :height="height" :nodes="nodes"></ejs-diagram>
</template>
<script>

let diagramInstance;

let ports = [
  {
    id: 'rightMidPort',
    offset: { x: 1, y: 0.5 },
    visibility: PortVisibility.Visible,
    constraints: PortConstraints.Draw | PortConstraints.Default
  }, 
  /* {
    id: 'port1',
    offset: { x:0, y:0 },
    visibility: PortVisibility.Visible,
    style: {
      fill: 'orange',
      strokeWidth: 2
    },
    height: 20,
    width: 20,
    shape: 'Custom',
    pathData: "M540.3643,137.9336L546.7973,159.7016L570.3633,159.7296L550.7723,171.9366L558.9053,194.9966L540.3643,179.4996L521.8223,194.9966L529.9553,171.9366L510.3633,159.7296L533.9313,159.7016L540.3643,137.9336z"
  },
  {
    id: 'topMidPort',
    offset: { x: 0.5, y: 0 },
    visibility: PortVisibility.Visible
  }, */

  /* {
    id: 'bottomMidPort',
    offset: { x: 0.5, y: 1 },
    visibility: PortVisibility.Visible
  },*/
   {
    id: 'leftMidPort',
    offset: { x: 0, y: 0.5 },
    visibility: PortVisibility.Visible
  },/*
  {
    id: 'centerPort',
    offset: { x: 0.5, y: 0.5 },
    visibility: PortVisibility.Visible
  } */
];

let nodes = [
  {
    id: "node1",
    offsetX: 300,
    offsetY: 200,
    height: 200,
    width: 200,
    //ports: ports,
    annotations: [{ content: "Node1" }],
    style: { fill: '#6495ED' }
  },
  {
    id: "node2",
    offsetX: 700,
    offsetY: 200,
    height: 200,
    width: 200,
    annotations: [{ content: "Node2" }],
    style: { fill: '#6495ED' },
    ports: ports
  }
];

import {
  DiagramComponent,
  PortConstraints,
  PortVisibility
} from '@syncfusion/ej2-vue-diagrams';
import { ButtonComponent } from '@syncfusion/ej2-vue-buttons';

export default {
  components: {
    'ejs-diagram': DiagramComponent,
    'ejs-button': ButtonComponent
  },
  data: function () {
    return {
      width: '1102px',
      height: '602px',
      nodes: nodes,
      removePort: ()=>{
        diagramInstance.removePorts(diagramInstance.nodes[0], ports);
      },
      updatePort: ()=>{
        //diagramInstance.nodes[0].ports[0].offset = { x:0, y:0 };
        diagramInstance.nodes[0].ports[0].verticalAlignment = 'Bottom';
        diagramInstance.nodes[0].ports[0].horizontalAlignment = 'Right';
      }
    };
  },
  mounted: function(){
    diagramInstance = this.$refs.diagramObject.ej2Instances;
    diagramInstance.addPorts(diagramInstance.nodes[0], ports);
  }
}
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-buttons/styles/material.css";

.container{
  text-align: left;
  margin-bottom: 10px;
}

.button{
  margin-right: 10px;
}
</style>