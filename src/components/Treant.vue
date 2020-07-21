<template>
  <div id="tree-simple" style="height: 100vh; margin: 5px; width: 100%;" />
</template>

<script>
// http://fperucic.github.io/treant-js/
import "treant-js/Treant.css";
import "treant-js/examples/basic-example/basic-example.css";
import Raphael from "raphael";

export default {
  data() {
    return {
      treant: null,
      chart_config: null,
    };
  },
  mounted() {
    window.Raphael = Raphael;
    let Treant = require("treant-js/Treant");
    Treant = Treant.Treant;
    new Treant({
      chart: {
        container: "#tree-simple",
      },
      connectors: {
        type: "step",
      },
      nodeStructure: {
        text: {
          name: "Simple node",
          title: "One of kind",
          desc: "A basic example",
        },
        children: [
          {
            image:
              "http://flat-icon-design.com/f/f_object_167/s256_f_object_167_0bg.png",
          },
          {
            image:
              "http://flat-icon-design.com/f/f_object_80/s256_f_object_80_0bg.png",
            children: [
              {
                image:
                  "http://flat-icon-design.com/f/f_object_78/s256_f_object_78_0bg.png",
              },
              {
                image:
                  "http://flat-icon-design.com/f/f_object_114/s256_f_object_114_0bg.png",
                children: [
                  {
                    image:
                      "http://flat-icon-design.com/f/f_object_67/s256_f_object_67_0bg.png",
                  },
                ],
              },
            ],
          },
        ],
      },
    });
  },
};
</script>

<style lang="scss">
#tree-simple {
  width: 100%;
  height: 100vh;
  margin: 5px;
  .node {
    border: 1px solid red;
    padding: 0 20px;
  }
  .node-name {
    color: red;
  }
}
</style>
