This repo will sync the folder `src` with the cergentis Hubspot portal. Each commit to the master branch will try to upload the files to HS.

To update the header and the footer files, keep in mind that minor modifications are needed for these files:

Because Hubspot uses HubL language (similar to Jinja2), you will need to replace a few common codes to avoid Hubspot trying to use HubL within your minimized JS/CSS.

- Replace any of those matchs `{{` `{#` `{%`  `%}` `#}` `}}`, and add an space between them like: `{{` --> `{ {`.
- Add on the top of those files:
```
<!--
  templateType: global_partial
  label: Page Header
-->
```
OR
```
<!--
  templateType: global_partial
  label: Page Footer
-->
```

To improve the rendering in the server side, you can wrap your CSS and JS tags with 
```
{% require_css %}<style> ... </style>{% end_require_css %}
```
and
```
{% require_js %}<script></script>{% end_require_js %}
```
 You can add `position="footer"` to `{% require_js %}` for the JS you want to load in the footer: `{% require_js position="footer" %}`
