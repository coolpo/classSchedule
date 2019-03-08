<template>
  <div class="parent">
    <h2>Simple Node Demo 2.0</h2>
    <div id="myDiagram" class="myCanvas"></div>
  </div>
</template>

<script>
import { Diagram, Node, Panel, Shape, TextBlock, GraphObject } from "gojs";
export default {
  name: "about",
  data() {
    return {
      mockDiagramData: null
    };
  },
  methods: {
    // init canvas
    initCanvas() {
      let _$ = GraphObject.make;
      let myDiagram = _$(Diagram, "myDiagram");
      let node = new Node(Panel.Auto);
      let shape = new Shape();
      shape.figure = "RoundedRectangle";
      shape.fill = "lightblue";
      node.add(shape);
      let textBlock = new TextBlock();
      textBlock.text = 'Hello world!';
      textBlock.margin = 5;
      node.add(textBlock);
      myDiagram.add(node);
    }
  },
  mounted() {
    this.initCanvas();
  }
};
</script>

<style lang="scss" scoped>
.parent {
  margin: 0;
  padding: 0;
  .myCanvas {
    width: 500px;
    height: 500px;
    background-color: darkgrey;
    margin: 0 auto;
  }
}
</style>
