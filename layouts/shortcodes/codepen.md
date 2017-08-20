{{/*

    Embarquer un pen provenant de  codepen.io


    L'unique paramètre requis est `id`.
    C'est le slug-hash du pen. À récupérer à partir de l'url.
    Pour d'autres paramètres et leurs valeurs par défaut, voir en-dessous.
    Ajustez-les selon vos besoins.

    Exemples:

    - Simple:

        {{% pen id="Gflmy" %}}


    - Montrer le pen dans l'onglet js :

        {{% pen id="Gflmy" tab="js" %}}

*/}}


{{/* DEFAULTS */}}
{{ $user    := "xtof-party" }}
{{ $height  := 500 }}
{{ $tab     := "result" }}{{/* html|css|js|result */}}
{{ $theme   := 8862 }}{{/* create on codepen.io */}}


<script
    data-slug-hash="{{ .Get "id" }}"
    data-user="{{ or (.Get "user") $user }}"
    data-height="{{ or (.Get "height") $height }}"
    data-default-tab="{{ or (.Get "tab") $tab }}"
    data-theme-id="{{ or (.Get "theme") $theme }}"
    class='codepen'
    async
    src="//codepen.io/assets/embed/ei.js"
></script>