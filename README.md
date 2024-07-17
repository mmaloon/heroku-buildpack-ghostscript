# Heroku Buildpack for Ghostscript (full version)

Currently installs Ghostscript 9.22 on Heroku Cedar. This buildpack takes the binary available at https://www.ghostscript.com/download/gsdnld.html

## Install

    $ cd /path/to/your-app
    $ heroku buildpacks:add https://github.com/phbernard/heroku-buildpack-ghostscript.git

    # Push changes to deploy
    $ git push


## Testing Release:

```bash
heroku run bash
```

```bash
curl -o /tmp/original.pdf https://d3rw207pwvlq3a.cloudfront.net/attachments/000/360/561/original/Winter_2024_-_MATH_101B_-_Course_Syllabus.pdf

convert -thumbnail x250 -background white -alpha remove /tmp/original.pdf[0] /tmp/result.jpg
```

```bash
# get upload url (local bash):
rails runner 'puts S3FileService.put_object_url(object_name: "test-file.jpg")'
```

```bash
curl -X PUT -T /tmp/result.jpg 'UPLOAD_URL'
```

```bash
# download file (local bash)
aws s3 presign s3://wize-dev/test-file.jpg --expires-in 3600
# delete file (local bash)
aws s3 rm s3://wize-dev/test-file.jpg
```


https://github.com/ArtifexSoftware/ghostpdl-downloads/releases/download/gs10021/ghostscript-10.02.1.tar.gz

https://github.com/mmaloon/heroku-buildpack-ghostscript.git