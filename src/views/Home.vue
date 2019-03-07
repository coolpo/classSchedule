<template>
  <div class="parent">
    <h2>A Simple GOJS Diagram</h2>
    <div id="myCanvas" class="myCanvas"></div>
  </div>
</template>

<script>
import {
  GraphObject,
  Node,
  Shape,
  Binding,
  TextBlock,
  GraphLinksModel,
  Diagram,
  Margin
} from "gojs";
export default {
  name: "home",
  data() {
    return {
      mockModelData: null,
      mockDiagram: null,
    };
  },
  methods: {
    initCanvas() {
      let _$ = GraphObject.make;
      let myDiagram = _$(Diagram, "myCanvas"); // 返回一个diagram对象，canvas的parent对象
      myDiagram.nodeTemplate = _$(
        Node,
        "auto",
        _$(Shape, "RoundedRectangle", new Binding("fill", "color")),
        _$(TextBlock, { margin: 3 }, new Binding("text", "key")) // 建立绑定的地方
      );

      myDiagram.model = new GraphLinksModel(
        [
          { key: "Alpha", color: "lightblue" },
          { key: "Beta", color: "orange" },
          { key: "Gamma", color: "ligthgreen" },
          { key: "Delta", color: "pink" }
        ],
        [
          { from: "Alpha", to: "Beta" },
          { from: "Alpha", to: "Gamma" },
          { from: "Beta", to: "Beta" },
          { from: "Gamma", to: "Delta" },
          { from: "Delta", to: "Alpha" }
        ]
      );
      myDiagram.undoManager.isEnabled = true;
      this.mockDiagram = myDiagram;
      console.log(this.mockDiagram.model);
      
    }
  },
  mounted() {
    this.initCanvas()
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