---
layout: page
title: Swagger UI
---

<div id="swagger-ui"></div>

<script src="{{ '/dist/swagger-ui/swagger-ui-bundle.js' | relative_url }}"></script>
<script src="{{ '/dist/swagger-ui/swagger-ui-standalone-preset.js' | relative_url }}"></script>
<script>
window.onload = function() {
  const ui = SwaggerUIBundle({
    url: "https://github.com/VR-API-Integration/youforce-api-Swagger-ui/blob/main/API/WFMSwagger.json",
    dom_id: '#swagger-ui',
    presets: [
      SwaggerUIBundle.presets.apis,
      SwaggerUIStandalonePreset
    ],
    layout: "BaseLayout"
  })
}
</script>
