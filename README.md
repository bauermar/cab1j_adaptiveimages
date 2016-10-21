# cab1j_adaptiveimages
TYPO3 Extension for adaptive images

add to .htaccess 

```
RewriteCond %{REQUEST_URI} !fileadmin/system/
RewriteCond %{REQUEST_URI} !typo3conf/
RewriteCond %{REQUEST_URI} !typo3/
# don't apply the AI behaviour to images inside AI's cache folder:
RewriteCond %{REQUEST_URI} !typo3temp/ai-cache

# Send any GIF, JPG, or PNG request that IS NOT stored inside one of the above directories
# to adaptive-images.php so we can select appropriately sized versions
RewriteRule \.(?:jpe?g|gif|png)$ typo3conf/ext/cab1j_adaptiveimages/Classes/Service/adaptive-images.php
```

add to head of page
```
<script>
	document.cookie='resolution='+Math.max(screen.width,screen.height)+("devicePixelRatio" in window ? ","+devicePixelRatio : ",1")+'; path=/';
</script>
```


