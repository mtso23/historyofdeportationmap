---
layout: default
title: "A History of Deportation Test Map"
---

## A History of Deportaton Test

See map below for animation

<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Migration Layer</title>
    <link rel="stylesheet" href="./lib/leaflet.css" />
    <style>
    html,body{
        margin: 0;
        padding: 0;
    }
    #map{
        position: absolute;
        height: 100%;
        width: 100%;
    }
    #event{
        position: absolute;
        top: 50px;
        right: 600px;
        height: 100px;
        width: 400px;
        z-index: 10000;
    }
    .btn{
        background-color: #4CAF50; /* Green */
        border: none;
        color: white;
        padding: 5px 10px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
   }
    </style>
</head>

<body>
    <div id="map"></div>
    <div id='event'>
        <input type="button" value="setData" class="btn" onclick="setData()">
        <input type="button" value="hide" class="btn" onclick="hide()">
        <input type="button" value="show" class="btn" onclick="show()">
        <input type="button" value="pause" class="btn" onclick="pause()">
        <input type="button" value="play" class="btn" onclick="play()">
        <input type="button" value="destroy" class="btn" onclick="destroy()">
    </div>
    <script src="./lib/leaflet.js"></script>
    <script src='./src/src.js'></script>
    <script>
        var lrmap = L.map('map').setView([25, -40], 3);
        L.tileLayer('https://{s}.basemaps.cartocdn.com/light_nolabels/{z}/{x}/{y}{r}.png', {
	attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors &copy; <a href="https://carto.com/attributions">CARTO</a>',
	subdomains: 'abcd',
	maxZoom: 19
})
        .addTo(lrmap);
        
        var data = [{"from":[-95.712891,37.090240],"to":[-102.552788,23.634501],"labels":["United States","Mexico"],"color":"#ff3a31"},{"from":[-95.712891,37.090240],"to":[-106.346771,56.130367],"labels":[null,"Canada"],"color":"#ff7e2b"},{"from":[-95.712891,37.090240],"to":[-88.896530,13.794185],"labels":[null,"El Salvador"],"color":"#ffc726"},{"from":[-95.712891,37.090240],"to":[-3.435973,55.378052],"labels":[null,"United Kingdom"],"color":"#e9ff20"},{"from":[-118.2705,33.9984],"to":[-92.145189,46.77372],"labels":[null,"Duluth"],"color":"#99ff1b"},{"from":[-118.2705,33.9984],"to":[-111.824547,40.788055],"labels":[null,"Salt Lake"],"color":"#45ff15"},{"from":[-118.2705,33.9984],"to":[-111.364615,47.536109],"labels":[null,"Great Falls"],"color":"#10ff33"},{"from":[-118.2705,33.9984],"to":[-97.585039,35.511099],"labels":[null,"Oklahoma"],"color":"#0aff84"},{"from":[-118.2705,33.9984],"to":[-115.157907,36.173032],"labels":[null,"Las Vegas"],"color":"#05ffd9"},{"from":[-118.2705,33.9984],"to":[-103.196215,34.418753],"labels":[null,"Clovis"],"color":"#00ccff"}];
        
        var data2=[{"from":[-73.875523,40.781063],"to":[-80.247887,25.792296],"labels":["New York","Miami"],"color":"#d7768a"},{"from":[-73.875523,40.781063],"to":[-118.2705,33.9984],"labels":[null,"Los Angeles"],"color":"#00ccff"},{"from":[-73.875523,40.781063],"to":[-87.724088,41.917846],"labels":[null,"Chicago"],"color":"#ffc726"},{"from":[-73.875523,40.781063],"to":[-71.058437,42.35902],"labels":[null,"Boston"],"color":"#e9ff20"},{"from":[-73.875523,40.781063],"to":[-75.683057,45.42172],"labels":[null,"Ottawa"],"color":"#99ff1b"}];

        data = data.map(item => { return {...item, value: parseInt(Math.random()*20)}});
        data2 = data2.map(item => { return {...item, value: parseInt(Math.random()*20)}});

        var migrationLayer = new L.migrationLayer({
            map: lrmap,
            data: data,
            pulseRadius:30,
            pulseBorderWidth:3,
            arcWidth:1,
            arcLabel:true,
            arcLabelFont:'10px sans-serif',
            maxWidth:10
            }
        );
        migrationLayer.addTo(lrmap);

        function setData(){
            migrationLayer.setData(data2);
        }
        function hide(){
            migrationLayer.hide();
        }
        function show(){
            migrationLayer.show();
        }
        function play(){
            migrationLayer.play();
        }
        function pause(){
            migrationLayer.pause();
        }
        function destroy() {
            migrationLayer.destroy();
        }
    </script>
</body>

</html>
