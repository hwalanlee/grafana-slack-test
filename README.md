git init && git add . && git commit -m "first commit" && git branch -M master && git remote add origin https://github.com/hwalanlee/grafana-slack-test.git && git push -u origin master
git add . && git commit -m "commit" && git push -u origin master

- metrics get above thresholds > grafana alerts triggered > posted on slack channel ( > instance restart )

- alert with rendered image
    - grafana.ini
        [server]
        root_url = http://x.x.x.x:3000/
        [external_image_storage]
        provider = s3
        [external_image_storage.s3]
        bucket = lan-xxx
        region = ap-northeast-2
        path = https://lan-xxx.s3.ap-northeast-2.amazonaws.com/     > no needed?
        access_key = ${AWS_ACCESS_KEY}
        secret_key = ${AWS_SECRET_KEY}
    - slack token 입력하면 작동 안 함
        - If use bot token (xoxb-), Grafana will upload the generated image via Slack’s file.upload API method (mean upload to Slack), not the external image destination.
    - 해야 할 것
        - /var/lib/grafana/png 이미지 파일이 얼마나 쌓이는지, 자동으로 지울 수 있게