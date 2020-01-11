# elmUploaderByBase64
Elm uploader by post base64

# Test
nc -l 8000 > testElmUploader.b64
ctrl+c after click upload

Last file:
cat testElmUploader.b64 | tail -n 1 | sed "s/^.*,//g" | sed "s/|//g" | base64 -d -o imageFile.ext

origin=$(md5sum originFile.ext)

upload=$(md5sum imageFile.ext)

test "$origin" -eq "$upload" && echo 'Equals' || echo 'No deal'
