# index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
   
    <title>Gewinn- und Erlösfunktion</title>
</head>
<script>
    function fprogramm() {
        var vAusgabe="";
        var vX;
        var vKosten;
        var vVKosten;
        var vFKosten;
		var vPreis;
		var vGewinn;
		var vErlös;
		var vPMenge;
		var vGewinnschwelle;
		var vBEP;
		
		vX= 0;
        
		vPMenge =parseFloat(document.getElementById("idPMenge").value);
		vVKosten =parseFloat(document.getElementById("idVKosten").value);
		vFKosten =parseFloat(document.getElementById("idFKosten").value);	
		vPreis =parseFloat(document.getElementById("idPreis").value);
        
       
		
		vAusgabe = vAusgabe + "<table border=1>";
		vAusgabe = vAusgabe + "<tr><th>Menge</th>";
		vAusgabe = vAusgabe + "<th>Kosten K(x)= kf+kv*x</th>";
		vAusgabe = vAusgabe + "<th>Erlöse E(x)=p*x</th>";
		vAusgabe = vAusgabe + "<th>Gewinn G(x)=E(x)-k(x)</th>";
		vAusgabe = vAusgabe + "<th>Bemerkung</th></tr>";
		
		while (vX <=vPMenge) {
			
			vKosten= vFKosten+vVKosten * vX;
			vErlös= vPreis*vX;
			vGewinn= vErlös-vKosten;
			
			vAusgabe=vAusgabe+"<tr><td>"+vX+"</td>"
			vAusgabe=vAusgabe + "<td>" + vKosten + "</td>";
			vAusgabe=vAusgabe + "<td>" + vErlös + "</td>";
			
			if (vGewinn < 0){
				vAusgabe=vAusgabe + "<td style=color:red>" + vGewinn + "</td>";
				vAusgabe=vAusgabe + "<td>Verlust</td></tr>";
			} else {
				vAusgabe=vAusgabe + "<td>" + vGewinn + "</td>";
				vAusgabe=vAusgabe + "<td>Gewinn</td></tr>";
				
			}
			vX = vX + 1000;
		}
		vAusgabe=vAusgabe + "</table>";
		
		vBEP = vFKosten/(vPreis-vVKosten);
		vGewinnschwelle = parseFloat(vBEP)*vPreis;
		vAusgabe=vAusgabe + "<br>Break-Even-Point: " + vBEP + " Stück<br>";
		vAusgabe=vAusgabe + "Gewinnschwelle: " + vGewinnschwelle.toFixed(2) + " €";
		
		document.getElementById("idAusgabe").innerHTML=vAusgabe;
	}
</script>
	
<body>
		<h1>Gewinn- und Erlösfunktion</h1>

   		Kosten-Variable(k): x läuft von 1 bis <input id="idVKosten" type="text" value="4.50">
		Kosten -fix: <input id="idFKosten" type="text" value="12800"><br><br>
		Produktionsmenge (x): <input id="idPMenge" type="text" value="2000">
		Verkaufspreis: <input id="idPreis" type="text" value="6.00"><br><br>
		<button onClick="fprogramm();">Wertetabelle erzeugen!</button><br><br>
		<div id="idAusgabe">Button klicken!</div>
</body>
</html>
