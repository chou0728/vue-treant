<template>
  <div id="tree-simple" />
</template>

<script>
// http://fperucic.github.io/treant-js/
import 'treant-js/Treant.css';
import Raphael from 'raphael';
import $ from 'jquery';

const config = {
  container: '#tree-simple',
  connectors: {
    type: 'step',
  },
  node: {
    collapsable: true,
  },
  callback: {
    onTreeLoaded: function() {
      console.log('onTreeLoaded');
    },
    onToggleCollapseFinished: function(treeNode, bIsCollapsed) {
      console.log(treeNode);
      console.log(bIsCollapsed);
      console.log('onToggleCollapseFinished');
    },
  },
};

const parent_node = {
  text: { name: 'Parent node' },
  HTMLid: 'parent_node',
};
const first_child = {
  parent: parent_node,
  text: { name: 'First child' },
  HTMLid: 'first_child',
};
const second_child = {
  parent: parent_node,
  text: { name: 'Second child' },
  HTMLid: 'second_child',
};
const third_child = {
  parent: second_child,
  text: { name: 'Third child' },
  HTMLid: 'third_child',
};

export default {
  data() {
    return {
      simple_chart_config: [config, parent_node, first_child, second_child],
    };
  },
  mounted() {
    window.Raphael = Raphael;
    window.$ = $;
    let Treant = require('treant-js/Treant');
    Treant = Treant.Treant;

    new Treant(this.simple_chart_config);

    $('.node').click(() => {
      // const key = e.target.parentNode.id;
      this.simple_chart_config.push(third_child);
      new Treant(this.simple_chart_config);
      console.log(this.simple_chart_config);
    });

    // new Treant({
    //   chart: {
    //     container: "#tree-simple",
    //     connectors: {
    //       type: "step",
    //     },
    //     node: {
    //       collapsable: true,
    //     },
    //   },
    //   nodeStructure: {
    //     text: {
    //       name: "Simple node",
    //       title: "One of kind",
    //       desc: "A basic example",
    //     },
    //     children: [
    //       {
    //         text: {
    //           name: "Simple node",
    //           title: "One of kind",
    //           desc: "A basic example",
    //         },
    //       },
    //       {
    //         text: {
    //           name: "Simple node",
    //           title: "One of kind",
    //           desc: "A basic example",
    //         },
    //       },
    //       {
    //         text: {
    //           name: "Simple node",
    //           title: "One of kind",
    //           desc: "A basic example",
    //         },
    //       },
    //       {
    //         text: {
    //           name: "Simple node",
    //           title: "One of kind",
    //           desc: "A basic example",
    //         },
    //         children: [
    //           {
    //             text: {
    //               name: "Simple node",
    //               title: "One of kind",
    //               desc: "A basic example",
    //             },
    //           },
    //           {
    //             text: {
    //               name: "Simple node",
    //               title: "One of kind",
    //               desc: "A basic example",
    //             },
    //           },
    //         ],
    //       },
    //     ],
    //   },
    // });
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
