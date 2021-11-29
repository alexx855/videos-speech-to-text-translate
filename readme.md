# Convert video to audio file
```
docker run --rm -it -v $(pwd):/tmp/workdir jrottenberg/ffmpeg -stats -i demo-video.mp4 audio-data.wav
```

# Upload audio file to Google Cloud Storage
```
gsutil cp audio-data.wav gs://GCP_BUCKET_URL
```

# Make sure to export the environment variables for google cloud
```
export GOOGLE_APPLICATION_CREDENTIALS="KEY_PATH"
```

# Install deps
```
pip3 install --upgrade google-api-python-client
pip3 install --upgrade google-cloud-speech
pip3 install --upgrade google-cloud-translate
```

# Run transcribe on google cloud
```
python3 transcribe_model_selection.py gs://GCP_BUCKET_URL/audio-data.wav --model video >> response.text
```