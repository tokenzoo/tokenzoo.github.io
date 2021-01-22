---
layout: tree
banner: tree.jpg
---

Here is a tree representation of anonymous credentials schemes. Click on a vertex to go to the right page

<style>

<style>

.node circle {
  fill: #d2c7c7;
  stroke: steelblue;
  stroke-width: 2px;
}

.node text {
    font: 12px sans-serif;
    fill: #ffffff;
}

.node--internal circle {
  fill: #555;
}

.link {
  fill: none;
  stroke: #434648;
  stroke-width: 3px;
}

form {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  position: absolute;
  left: 5px;
  top: 5px;
}

label {
  display: block;
}

</style>
<svg width="500" height="500"></svg>
<script src="https://d3js.org/d3.v4.min.js"></script>
<script src="./tree_data.js"></script>
<script>

function diagonal(d) {
  return "M" + d.y + "," + d.x
      + "C" + (d.parent.y + 100) + "," + d.x
      + " " + (d.parent.y + 100) + "," + d.parent.x
      + " " + d.parent.y + "," + d.parent.x;
}


var svg = d3.select("svg"),
    width = +svg.attr("width"),
    height = +svg.attr("height"),
    g = svg.append("g").attr("transform", "translate(40,0)");

// declares a tree layout and assigns the size
var cluster = d3.cluster()
    .size([height, width - 70]);

//  assigns the data to a hierarchy using parent-child relationships
var nodes = d3.hierarchy(treeData);

// maps the node data to the tree layout
// assigns x and y
cluster(nodes);

var link = g.selectAll(".link")
    .data(nodes.descendants().slice(1))
    .enter().append("path")
    .attr("class", "link")
    .attr("d", diagonal);

// adds each node as a group
  var node = g.selectAll(".node")
      .data(nodes.descendants())
    .enter().append("g")
      .attr("class", function(d) { return "node" + (d.children ? " node--internal" : " node--leaf"); })
      .attr("transform", function(d) { return "translate(" + d.y + "," + d.x + ")"; });

// adds the circle and the link to the node
node.append("a")
    .attr("xlink:href", function(d) { return d.data.url; })
    .append("circle")
    .attr("r", 5);

// adds the text to the node
node.append("text")
    .attr("dy", 3)
    .attr("x", function(d) { return d.children ? -8 : 8; })
    .style("text-anchor", function(d) { return d.children ? "end" : "start"; })
    .text(function(d) { return d.data.name; });

</script>
