<script>
  import L from 'leaflet';
  import { onMount, afterUpdate } from 'svelte';

  export let events;
  export let contracts;

  let mapContainer;
  let leafletMap;

  const corner1 = L.latLng(25.549204282807214, -103.47397135208219);
  const corner2 = L.latLng(25.521026126702395, -103.36243547676693);
  const bounds = L.latLngBounds(corner1, corner2);

  onMount(async () => {
    
    const tiles = L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token={accessToken}', {
      attribution: '',
      maxZoom: 18,
      id: 'elsonny/ckr0mte00008w17nub12vdyxp',
      tileSize: 512,
      zoomOffset: -1,
      accessToken: 'pk.eyJ1IjoiZWxzb25ueSIsImEiOiJjazkwYWQ2d28wMDJ4M25vNjR3b2h5bWpiIn0.iQk1NtwS-2bJafmWg5Ol9w',
    });

    const eventMarkers = events.map(e =>{
      let offset = e.offset ? 'margin-left: '+e.offset+'px' : '';
      let icon = L.divIcon({
        className: 'custom-div-icon',
        html: "<div style='background-color:#"+e.color+";' class='event-marker'>"+e.letter+"</div>",
        iconSize: [40, 40],
        iconAnchor: [e.offset || 0, 0]
      });
      let tooltip = {
        className : 'event-tooltip',
        permanent: false,
        direction: 'right',
        permanent: false,
        offset: [-e.offset || 0, 0]
      }
      return L.marker([e.latitude, e.longitude],{icon:icon}).bindTooltip('<p class="date">'+e.date+'</p>'+e.text,tooltip);
    });

    const contractMarkers = contracts.map(c => {
      let icon = L.divIcon({
        className: 'contract-marker',
        html: "<div class='ammount'>"+c.ammount+"</div><div class='code'>"+c.key+"</div>",
        /*iconSize: [40, 40],*/
      });
      return L.marker([c.latStart,c.lngStart],{icon:icon});
      /*let start = [c.latStart,c.lngStart];
      let end = [c.latEnd,c.lngEnd]
      L.polyline([start,end], {color: 'white'}).addTo(leafletMap);*/
    });

    leafletMap = L.map(mapContainer, { 
      scrollWheelZoom: false,
      attributionControl: false,
      zoomControl : false,
      layers : [tiles,L.layerGroup(eventMarkers)]
    }).fitBounds(bounds);

    resize();
    // console.log(municipalities, counties)
  });
  
  const resize = () => {
    leafletMap.invalidateSize().fitBounds(bounds);
  };

</script>
<div class="map" bind:this="{mapContainer}">
</div>

<style>
  .map {
    height:350px;
    width: 100%;
  }

</style>