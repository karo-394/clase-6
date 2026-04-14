# clase-6
<!doctype html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <title>Un fetch</title>
        <style>
            body {
                font-family: Helvetica, Arial, sans-serif;
            }
			
			table{
				border-collapse: collapse;
			}
			
			td{
				border:1px solid black;
				padding:1rem;
			}
        </style>
    </head>
    <body>
        <h1>Exel</h1>
		<table>
			<thead>
				<tr>
					<th>Asignature</th>
					<th>Grupo</th>
					<th>Enfoque</th>
				</tr>
			</thead>
			<tbody></tbody>
		</table>
		<script>
			
			const t = document.querlySelector("table");
			
            const URL = "https://api.myjson.online/v1/records/94b4d353-dfc2-49d3-b28e-cf8fd02e7a16";
			
            fetch(URL)
                .then((respuesta) => {
                    if (!respuesta.ok) {
                        throw new Error("Error HTTP: " + respuesta.status);
                    }
                    return respuesta.json();
                })

                .then((datos) => {
                    var trabajo = datos.data;
                    console.log("Datos recibidos:", trabajo);
					trabajo.forEach((x) => {
						if(x.ok == 1){
							t.innerHTML += `<tr><td>${x.name}</td><td>${x.group}</td><td>${focus}</td><tr>`;
						}
					});
                })
                .catch((error) => {
                    console.error("Algo salió mal:", error);
                });
        </script>
    </body>
</html>
