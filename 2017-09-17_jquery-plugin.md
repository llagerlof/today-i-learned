# Como criar um plugin para jQuery

No exemplo abaixo, esse plugin "extractLinks" permite o usuário extrair para uma div todos os links que correspondem ao filtro definido.

```
(function ($) {
	$.fn.extractLinks = function() {
		// Cria uma div para colocar os links dentro.
		if ($('#divExtractedLinks').length == 0) {
			$("body").prepend("<div id='divExtractedLinks' style='border-style:solid; border-width: 1px; padding: 10px;'></div>");
		}
		$("#divExtractedLinks").html('');
		// Loop em todos os elementos encontrados.
		return this.each(function() {
			if ($(this).attr("class") != "extractedLink") {
				console.log($(this).attr("href"));
				$("#divExtractedLinks").append("<a class='extractedLink' href='" + $(this).attr("href") + "' target='_blank'>" + $(this).attr("href") + "</a>"  + ", " + $(this).text() + "<br>");
			}
		});
	};
}(jQuery));
```

Exemplo:

```
$('a').extractLinks(); // cria uma div no topo da página contendo a lista de todos os links e suas respectivas descrições.
```

---

*keywords: jquery, plugin, tutorial*

*reference: https://learn.jquery.com/plugins/basic-plugin-creation/*
