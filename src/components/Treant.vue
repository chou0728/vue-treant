<template>
  <div id="tree-simple" />
</template>

<script>
// http://fperucic.github.io/treant-js/
import "treant-js/Treant.css";
import Raphael from "raphael";
import $ from "jquery";

export default {
  mounted() {
    window.Raphael = Raphael;
    window.$ = $;
    let Treant = require("treant-js/Treant");
    Treant = Treant.Treant;
    new Treant({
      chart: {
        container: "#tree-simple",
        connectors: {
          type: "step",
        },
        node: {
          collapsable: true,
        },
      },
      nodeStructure: {
        text: {
          name: "Simple node",
          title: "One of kind",
          desc: "A basic example",
        },
        children: [
          {
            text: {
              name: "Simple node",
              title: "One of kind",
              desc: "A basic example",
            },
          },
          {
            text: {
              name: "Simple node",
              title: "One of kind",
              desc: "A basic example",
            },
          },
          {
            text: {
              name: "Simple node",
              title: "One of kind",
              desc: "A basic example",
            },
          },
          {
            text: {
              name: "Simple node",
              title: "One of kind",
              desc: "A basic example",
            },
            children: [
              {
                text: {
                  name: "Simple node",
                  title: "One of kind",
                  desc: "A basic example",
                },
              },
              {
                text: {
                  name: "Simple node",
                  title: "One of kind",
                  desc: "A basic example",
                },
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
    border: 1px solid black;
    max-width: 200px;
    padding: 0 10px;
    text-align: center;
  }
  .node-name {
    color: red;
  }
  .collapse-switch {
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    border: none;
    background-color: transparent;
  }
}
</style>
