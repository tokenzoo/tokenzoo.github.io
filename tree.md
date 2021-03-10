---
layout: tree
banner: tree.jpg
---

Here is a tree representation of anonymous credentials schemes. Click on a vertex to go to the right page

<style> /* set the CSS */

.node circle {
  fill: #d2c7c7;
  stroke: steelblue;
  stroke-width: 2px;
}

.node text {
    font: 12px sans-serif;
    fill: #ffffff;
}

.link {
  fill: none;
  stroke: #434648;
  stroke-width: 3px;
}

</style>

<!-- load the d3.js library -->
<script src="https://d3js.org/d3.v4.min.js"></script>
<script src="./tree_data.js"></script>
<script>

// set the dimensions and margins of the diagram
var margin = {top: 40, right: 90, bottom: 50, left: 90},
    width = 1600 - margin.left - margin.right,
    height = 600 - margin.top - margin.bottom;

// declares a tree layout and assigns the size
var treemap = d3.tree()
    .size([width, height]);

//  assigns the data to a hierarchy using parent-child relationships
var nodes = d3.hierarchy(treeData);

// maps the node data to the tree layout
nodes = treemap(nodes);

// append the svg obgect to the body of the page
// appends a 'group' element to 'svg'
// moves the 'group' element to the top left margin
var svg = d3.select("body").append("svg")
      .attr("width", width + margin.left + margin.right)
      .attr("height", height + margin.top + margin.bottom),
    g = svg.append("g")
      .attr("transform",
            "translate(" + margin.left + "," + margin.top + ")");

// adds the links between the nodes
var link = g.selectAll(".link")
    .data( nodes.descendants().slice(1))
  .enter().append("path")
    .attr("class", "link")
    .attr("d", function(d) {
       return "M" + d.x + "," + d.y
         + "C" + d.x + "," + (d.y + d.parent.y) / 2
         + " " + d.parent.x + "," +  (d.y + d.parent.y) / 2
         + " " + d.parent.x + "," + d.parent.y;
       });

// adds each node as a group
var node = g.selectAll(".node")
    .data(nodes.descendants())
  .enter().append("g")
    .attr("class", function(d) {
      return "node" +
        (d.children ? " node--internal" : " node--leaf"); })
    .attr("transform", function(d) {
      return "translate(" + d.x + "," + d.y + ")"; });

// adds the circle and the link to the node
  node.append("a")
    .attr("xlink:href", function(d) { return d.data.url; })
    .append("circle")
    .attr("r", 10);


// adds the text to the node
node.append("text")
  .attr("dy", ".35em")
  .attr("y", function(d) { return d.children ? -20 : 20; })
  .style("text-anchor", "middle")
  .text(function(d) { return d.data.name; });

</script>
