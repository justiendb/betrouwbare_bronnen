<template>
<div id="app">
    <input type="radio" id="1one" value=20 v-on:change="reload()" v-model="checked1">
    <label for="1one">Auteur is bekend</label>
    <input type="radio" id="1two" value=0 v-on:change="reload()" v-model="checked1">
    <label for="1two">Auteur is onbekend</label>
<br>
    <input type="radio" id="2one" value=20 v-on:change="reload()" v-model="checked2">
    <label for="2one">Gefundeerde argumenten</label>
    <input type="radio" id="2two" value=0 v-on:change="reload()" v-model="checked2">
    <label for="2two">Ongefundeerde argumenten</label>
<br>
    <input type="radio" id="3one" value=20 v-on:change="reload()" v-model="checked3">
    <label for="3one">Objectief taalgebruik</label>
    <input type="radio" id="3two" value=0 v-on:change="reload()" v-model="checked3">
    <label for="3two">Subjectief taalgebruik</label>
<br>
    <input type="radio" id="4one" value=20 v-on:change="reload()" v-model="checked4">
    <label for="4one">Recent gepubliceerd</label>
    <input type="radio" id="4two" value=0 v-on:change="reload()" v-model="checked4">
    <label for="4two">Gedateerd</label>
<br>
    <input type="radio" id="5one" value=20 v-on:change="reload()" v-model="checked5">
    <label for="5one">Recensies</label>
    <input type="radio" id="5two" value=0 v-on:change="reload()" v-model="checked5">
    <label for="5two">Geen recensies</label>
<br>
<div id="chart-container">
<fusioncharts
:type="type"
:width="width"
:height="height"
:dataformat="dataformat"
:datasource="datasource"
>
</fusioncharts>
</div>
</div>
</template>

<script>
import Vue from 'vue';
import VueFusionCharts from 'vue-fusioncharts';
import FusionCharts from 'fusioncharts';
import AngularGauge from 'fusioncharts/fusioncharts.widgets';
import FusionTheme from 'fusioncharts/themes/fusioncharts.theme.fusion';

Vue.use(VueFusionCharts, FusionCharts, AngularGauge, FusionTheme);
export default {
name: 'app',
data () {
return {
    checked1: 0,
    checked2: 0,
    checked3: 0,
    checked4: 0,
    checked5: 0,
"type": "angulargauge",
"renderAt": "chart-container",
"width": "550",
"height": "350",
"dataFormat": "json",
"datasource": {
"chart": {
"caption": "Betrouwbaarheid bron",
"lowerLimit": "0",
"upperLimit": "100",
"showValue": "1",
"numberSuffix": "%",
"theme": "fusion",
"showToolTip": "0"
},
// Chart Data
"colorRange": {
"color": [{
"minValue": "0",
"maxValue": "25",
"code": "#FF0000"
}, {
"minValue": "25",
"maxValue": "50",
"code": "#F2726F"
},{
"minValue": "50",
"maxValue": "75",
"code": "#FFC533"
}, {
"minValue": "75",
"maxValue": "100",
"code": "#62B58F"
}]
},
"dials": {
"dial": [{
"value": ""
}]
}
}
}
},
methods: {
    reload: function() {
        this.datasource.dials.dial[0].value = parseInt(this.checked1) + parseInt(this.checked2) + parseInt(this.checked3) + parseInt(this.checked4) + parseInt(this.checked5)
    }
}
}
</script>

