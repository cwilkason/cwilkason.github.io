d3.select(window).on("resize", throttle);

var svg, g, world, fy16sectors, places, countryData, programSectors;
var rankingArrays = {
  world: [],
  lac: [],
  africa: [],
  amee: []
};
var scoreLookup = {};
var sliders = [];
var groupToggles = document.getElementsByClassName('group-toggle');
var regionToggles =  document.getElementsByClassName('region-toggle');

var fy16sectors = [];
var checkboxes = $("#program-sectors input[type=checkbox]");
for (i=0; i<checkboxes.length; i++) {
    var prgObj = {}
    prgObj.key = checkboxes[i].value;
    prgObj.label = $(checkboxes[i]).parent().text();
    fy16sectors.push(prgObj)
}


var defaultFill = '#d7d7d8';
var zeroFill = '#000000';

var width, height;

function setDimensions(){
  width = document.getElementById('map').offsetWidth-100;
  if(width / 2 <= window.innerHeight - 60) {
    height = width / 2;
  } else {
    height = window.innerHeight - 60;
    width = height * 2;
  }

}

setDimensions();

function setup(width,height){

  projection = d3.geo.kavrayskiy7()
    .translate([0, 0])
    .scale(width / 2 / Math.PI);

  path = d3.geo.path()
      .projection(projection);
  svg = d3.select("#map").append("svg")
      .attr("width", width)
      .attr("height", height)
      .append("g")
      .attr("transform", "translate(" + width / 2 + "," + height / 2 + ")");
      // .call(zoom);
