var newCenterMarker = null;
var newCenterMarkerInfo = null;
var antennasCircle = null;
var markersArray = [];

// Initialize and add the map
function initMap() {
  // The location of Uluru
  const uluru = { lat: 26.739483, lng: 75.85058 };
  
  // The map, centered at Uluru, 
  const map = new google.maps.Map(document.getElementById("map"), {
    zoom: 10,
    center: uluru,
  });
	const allCentres = [["Achrol - SC", [27.1418,75.96436]], ["Akera Dungar - SP", [27.01077,75.79708]], ["Amer - SP", [26.98966,75.85308]], ["Bagru - SC", [26.77919,75.57433]], ["Bajdoli - SP", [26.65825,75.79497]], ["Banskho - SP", [26.84138,76.15066]], ["Bassi - SP", [26.81666,76.04461]], ["Bhainslana - SP", [27.058,75.29155]], ["Bichpuri - SP", [27.36905,75.88869]], ["Bilonchi - SP", [27.1285,75.84852]], ["Bisalu - SP", [26.45913,75.69522]], ["Boraj - SC", [26.87458,75.50313]], ["Chaksu - SP", [26.60891,75.93677]], ["Chhaparwas Basna - SP", [27.09102,75.97508]], ["Chomu - SC", [27.15655,75.74508]], ["Dantli - SP", [26.81525,75.90125]], ["Daulatpura - SP", [26.76997,75.64327]], ["Dhanota - SP", [27.31475,75.7785]], ["Dhula Rao Ji - SP", [26.93166,76.1558]], ["Ganpatpura - SC", [26.85677,75.74211]], ["Hadota - SP", [27.21019,75.7308]], ["Harmara - C", [27.02258,75.76566]], ["Hathoj - SP", [26.96297,75.66466]], ["Jaipur-I - MC", [26.74061,75.86252]], ["Jaipur-II - C", [26.90205,75.82919]], ["Jaisinghpura Khor - SP", [26.95066,75.87344]], ["Jalmahal - C", [26.9565,75.83813]], ["Jhalana Doongri - SC", [26.8735,75.82266]], ["Jobner - SP", [26.9943,75.40919]], ["Kala Dera - SP", [27.18069,75.62841]], ["Keshwana Rajput - SP", [27.81277,76.30572]], ["Khawaraniji - SP", [26.99675,76.0978]], ["Khora Bisal - SP", [27.02194,75.68519]], ["Khora Meena - SP", [27.05219,75.9328]], ["Kishangarh Renwal - SP", [27.15797,75.35486]], ["Kotputli - SP", [27.73119,76.1913]], ["Kukas - SP", [27.03747,75.87961]], ["Lalgarh - SP", [26.78391,76.10394]], ["Luniawas - SC", [26.87061,75.88802]], ["Maharani Farm - SC", [26.84886,75.77538]], ["Mahesh Nagar - SP", [26.88338,75.77891]], ["Majipura - SP", [27.20355,76.00316]], ["Malviya Nagar - C", [26.85752,75.82119]], ["Manoharpur - SP", [27.29144,75.96]], ["Manpura Machedi - SP", [27.20636,75.87877]], ["Mansarovar - C", [26.86883,75.7595]], ["Med - SP", [27.36352,76.13125]], ["Mohanpura - SP", [26.87333,76.07452]], ["Nangal Panditpura - SP", [27.66308,76.21875]], ["Nayabas - SP", [27.26272,75.85336]], ["Naila - SP", [26.90658,75.9755]], ["Pachar - SP", [26.90658,75.9755]], ["Paota - SP", [27.58138,76.10522]], ["Pathredi - SP", [27.6173,76.10419]], ["Phagi - SP", [26.56811,75.56616]], ["Phulera - SP", [26.88311,75.23922]], ["Rajarampura - SP", [27.09286,75.75616]], ["Ramganj - SC", [26.91927,75.83961]], ["Ramnagaria - SC", [26.81586,75.86219]], ["Rampura - SC", [26.83633,75.7293]], ["Raniyawas - SP", [26.95327,75.97408]], ["Renwal Maji - SP", [26.66186,75.66752]], ["Sambhar Lake - SP", [26.91441,75.19141]], ["Sambhariya - SP", [26.73313,76.04013]], ["Sanganer - SC", [26.73313,76.04013]], ["Seemaliyawas - SC", [26.68438,75.82886]], ["Shahpura - SP", [27.38855,75.94838]], ["Shastri Nagar - C", [26.95144,75.78588]], ["Singod Khurd - SP", [27.30377,75.67544]], ["Siwar - SP", [26.92902,75.61161]], ["Triveni Nagar - SC", [26.86722,75.78227]], ["Vaishali Nagar - C", [26.90161,75.68938]], ["Virat Nagar - SP", [27.43155,76.16016]]];
	
	//const allCentres = [["Achrol - SC", [27.1418,75.96436]], ["Akera Dungar - SP", [27.01077,75.79708]], ["Amer - SP", [26.98966,75.85308]], ["Bagru - SC", [26.77919,75.57433]]];
   
	$(function() {
		$('#btnShowOnMap').click(function() {
			clearMap();
			var latitude = $('#latitude').val();
			var longitude = $('#longitude').val();
			var radius = $('#radius').val();
			var newCenterLocation = { lat: parseFloat(latitude), lng: parseFloat(longitude) }
			
			placeNewCenterMaker(newCenterLocation);
			drawRange(newCenterLocation, radius);
			placeCentersMarkerInRange(latitude, longitude, radius);
			showCentresInRadius(latitude, longitude, radius);
			fitBounds();
			
		});
		
		$('#openNav').click(function() {
		  document.getElementById("mySidebar").style.width = "250px";
		  document.getElementById("main").style.marginLeft = "250px";
		});

		/* Set the width of the sidebar to 0 and the left margin of the page content to 0 */
		function closeNav() {
		  document.getElementById("mySidebar").style.width = "0";
		  document.getElementById("main").style.marginLeft = "0";
		}
	});
	
	function clearMap() {
		if (markersArray) {
			for (i in markersArray) {
			  markersArray[i].setMap(null);
			}
		}
		if(antennasCircle) {
			antennasCircle.setMap(null);
		}
		markersArray = [];
	}
	
	function fitBounds() {
		if(markersArray.length == 1) {
			map.setCenter(markersArray[0].getPosition());
		}
		else if(markersArray.length > 1) {
			var bounds = new google.maps.LatLngBounds();
			for(i=0;i<markersArray.length;i++) {
			   bounds.extend(markersArray[i].getPosition());
			}
			console.log(bounds);
			map.fitBounds(bounds);
			//map.setZoom(map.getZoom()-1); 
			//$('#sidebarCollapse').click();
		}
	}

	
	function placeNewCenterMaker(newCenterLocation) {
		// -- Clear if already new centre marker placed.
		clearIfAlreadyPlaced();
		
		var newCenterMarker = new google.maps.Marker({
		  position: newCenterLocation,
		  map: map,
		  title: "Proposed Land",
		  icon: {
			labelOrigin: new google.maps.Point(16,44),
			url: "./images/red-star_32.png"
		  },
		  label: {
			text: "Proposed Land",
			color: "white",
			fontWeight: "bold",
			fontSize: "16px"
		  }
		});
		markersArray.push(newCenterMarker);
	
		//newCenterMarker.setIcon('./images/red-star_32.png')
		//---------------------------------------------
		
		//-- Draw Info on New Centre Marker.
		var infoContent = '<div style="height:20px; color:black"><div style="font-size:14px;height:20px">New Satsang Centre</div></div>';
		newCenterMarkerInfo = new google.maps.InfoWindow({
			content: infoContent
		});
		
		google.maps.event.addListener(newCenterMarker, 'click', function () {
			info.setContent('<div style="height:20px; color:black">' + infoContent + '</div>');
			info.open(map, newCenterMarker);
		});
		//-----------------------------------
	}
	
	function drawRange(location, radius) {
		 antennasCircle = new google.maps.Circle({
		  //strokeColor: "#d14747",
		  strokeColor: "#000",
		  strokeOpacity: 0.8,
		  strokeWeight: 2,
		  fillOpacity: 0,
		  map: map,
		  //center: {
			//lat: 26.739483,
			//lng: 75.85058
		  //},
		  center: location,
		  radius: radius * 1000
		});
	}
	
	function distance(lat1,lon1,lat2,lon2) {
		var R = 6371; // km (change this constant to get miles)
		var dLat = (lat2-lat1) * Math.PI / 180;
		var dLon = (lon2-lon1) * Math.PI / 180; 
		var a = Math.sin(dLat/2) * Math.sin(dLat/2) +
			Math.cos(lat1 * Math.PI / 180 ) * Math.cos(lat2 * Math.PI / 180 ) * 
			Math.sin(dLon/2) * Math.sin(dLon/2); 
		var c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a)); 
		var d = R * c;
		//if (d > 1) 
		return d.toFixed(1);
		//else if (d<=1) return Math.round(d*1000)+"m";
		//return d;
	}
	
	function showCentresInRadius(latitude, longitude, radius) {
		var places = allCentres;
		var centerInRadiusHTML = "";
		centerInRadiusHTML = "<h5>Centers In Range of " + radius +" Kms.</h5><br/><table border='1' cellpadding='5' style='width:233px;font-size:14px;'><th>Centre</th><th>Distance</th>";
		for (var i = 0; i < places.length; i++) {
			var position = places[i][1];
			var d = distance(parseFloat(position[0]), parseFloat(position[1]), latitude, longitude);
		
			if(d <= parseFloat(radius)) {
				centerInRadiusHTML += "<tr><td>" + allCentres[i][0] + "</td><td>" + d + " Kms.</td></tr>";
			}
		}
		centerInRadiusHTML += "</table>";
		$('#nearby-centres').html(centerInRadiusHTML);
	}
	
	function placeCentersMarkerInRange(newCentreLat, newCentreLon, radius) {
		for (var i = 0; i < allCentres.length; i++) {
			var markerIcon = './images/green-triangle_16.png';
			var markerLetter = 'P';
			// The marker, positioned at Uluru
			var centreLocation = allCentres[i][1];
			if(allCentres[i][0].indexOf('- C') > -1){
				markerIcon = './images/green-star_16.png';
				markerLetter = 'C';
				
			} else if(allCentres[i][0].indexOf('- SC') > -1){
				markerIcon = './images/green-dot_16.png';
				markerLetter = 'SC';
			}
			
			var d = distance(parseFloat(centreLocation[0]), parseFloat(centreLocation[1]), newCentreLat, newCentreLon);
			if(parseFloat(d) <= parseFloat(radius)) {
				var marker = new google.maps.Marker({
					position: { lat: parseFloat(centreLocation[0]), lng: parseFloat(centreLocation[1]) },
					map: map,
					icon: {
						//labelOrigin: new google.maps.Point(16,12),
						url: markerIcon
					}
				});
				markersArray.push(marker);
				
				bindMarkerInfo(map, marker, ("<div>" + allCentres[i][0] +" </div>"));
			}
		}
	}
	
	function bindMarkerInfo(map, marker, content, defaultOpen) {
		var info = new google.maps.InfoWindow({
			content: '<div style="height:20px; color:black">' + content + '</div>'
		});
		
		google.maps.event.addListener(marker, 'click', function () {
			info.setContent('<div style="height:20px; color:black">' + content + '</div>');
			info.open(map, marker);
		});
		
		if(defaultOpen) {
			info.open(map, marker);
		}
	}
	/* Set the width of the sidebar to 250px and the left margin of the page content to 250px */
	
	function clearIfAlreadyPlaced() {
		if(newCenterMarker != null) {
			newCenterMarker.setMap(null);
			newCenterMarkerInfo.close();
			antennasCircle.setMap(null);
		}
	}
}