# WhatsAudio

## How Does It Work?

Every audio or voice clip sent or received will be stored. Whenever you quote one of those messages and type `!ler`, that message will be forwarded to OpenAI to be transcribed. The transcribed text will then be sent as a message in the same chat screen.

## Build the Image

To build the image, run the following command:

```sh
podman build . -t whats
```

## Run it (change the variables as needed)

```sh
podman run --name=whats -d --restart always \
--volume=/data/whats/session:/session \
--volume=/data/whats/mp3:/mp3 \
-e OPENAI_API_KEY=sk-proj-yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy \
-e USER_PHONE=5511999998888 \
-e PATH_MP3=/mp3 \
-e PATH_SESSION=/session \
localhost/whats:latest
```

After the container is up and running, view the logs with:

```sh
podman logs -f --tail 100 whats
```

Finally, scan the QR code using your phone to complete the setup.
