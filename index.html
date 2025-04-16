<!DOCTYPE html>
<meta charset="utf-8">
<style>
  body { margin: 0; background: #000; }
  svg { width: 100vw; height: 100vh; display: block; }
  line { stroke: #aaa; }
  circle { stroke: #fff; stroke-width: 1.5px; fill: #69b3a2; }
  text { font: 10px sans-serif; fill: #fff; text-anchor: middle; }
</style>
<body>
<svg></svg>
<script src="https://d3js.org/d3.v7.min.js"></script>
<script>
const apiKey = "patB8cm7VUd15sLk8.e54309b459eb1ebf40e9515d4e0a840b84dc7eba0421a5ad79c3b67f1899c65b";
const baseId = "appbvoK6uB9kPATTN";
const tableName = "Pairings";
const viewName = "2025%20View";
const url = `https://api.airtable.com/v0/${baseId}/${tableName}?view=${viewName}&pageSize=100`;

async function fetchData() {
  const res = await fetch(url, {
    headers: { Authorization: `Bearer ${apiKey}` }
  });
  const data = await res.json();
  return data.records.map(r => r.fields);
}

function generateEdges(data) {
  const grouped = {};
  data.forEach(row => {
    const key = `${row.Robin}__${row.Group}`;
    if (!grouped[key]) grouped[key] = [];
    grouped[key].push(row.Name);
  });

  const links = [];
  const countMap = {};

  Object.values(grouped).forEach(group => {
    for (let i = 0; i < group.length; i++) {
      for (let j = i + 1; j < group.length; j++) {
        const source = group[i];
        const target = group[j];
        const key = [source, target].sort().join("-");
        countMap[key] = (countMap[key] || 0) + 1;
        links.push({ source, target });
      }
    }
  });

  const nodeSet = new Set(links.flatMap(link => [link.source, link.target]));
  const nodes = Array.from(nodeSet).map(id => ({ id }));
  return { nodes, links, countMap };
}

function renderCircularGraph(graph) {
  const width = window.innerWidth;
  const height = window.innerHeight;
  const radius = Math.min(width, height) / 2 - 80;

  const svg = d3.select("svg").attr("viewBox", [0, 0, width, height]);

  const angle = d3.scalePoint()
    .domain(graph.nodes.map(d => d.id))
    .range([0, 2 * Math.PI]);

  const positions = {};
  graph.nodes.forEach(d => {
    const a = angle(d.id);
    d.x = width / 2 + radius * Math.cos(a);
    d.y = height / 2 + radius * Math.sin(a);
    positions[d.id] = { x: d.x, y: d.y };
  });

  svg.selectAll("line")
    .data(graph.links)
    .join("line")
    .attr("x1", d => positions[d.source].x)
    .attr("y1", d => positions[d.source].y)
    .attr("x2", d => positions[d.target].x)
    .attr("y2", d => positions[d.target].y)
    .attr("stroke-width", d => {
      const key = [d.source, d.target].sort().join("-");
      return graph.countMap[key] || 1;
    });

  svg.selectAll("circle")
    .data(graph.nodes)
    .join("circle")
    .attr("r", 6)
    .attr("cx", d => d.x)
    .attr("cy", d => d.y);

  svg.selectAll("text")
    .data(graph.nodes)
    .join("text")
    .attr("x", d => d.x)
    .attr("y", d => d.y - 10)
    .text(d => d.id);
}

fetchData().then(data => {
  const graph = generateEdges(data);
  renderCircularGraph(graph);
});
</script>
</body>
