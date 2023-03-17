---
title: WFM API
tags: [wfm, api]
keywords: wfm, api
last_updated: 03/17/2023
sidebar: guides_sidebar
permalink: wfm_swagger.html
folder: guides/domain-apis
topnav: topnav

layout: page
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
