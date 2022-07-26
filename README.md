# Speech emotion recognition

## Welcome

The service receives an audio file and uses it as an input for a trained model.

## What’s the point?

The service performs speech emotion recognition using machine learning techniques. The service receives the audio file in binary format and outputs the text string resulting from audio recognition.
The service performs speech emotion recognition using machine learning techniques. The service receives the audio file in binary format and outputs the text string resulting from audio recognition.

## Model details:

The service receives an English-language WAV audio file and uses it as input to a modified Wav2Vec2.0 model based on a deep convolutional neural network trained with half precision on a mixture of natural data, and outputs the result of Speech Emotion Pattern Recognition as a text sequence. The model runs on a V100 GPU equipped with tensor cores to provide greater service throughput. the optimal duration of the processed audio track should be no more than 90 seconds for 320 kbps audio.

## How does it work?

The user must provide the following inputs in order to start the service and get a response:

Inputs:

 -   `endpoint`: asr.naint.tech.
 -   `method`: e2t.
 -   `input_path`: Path to '\*.txt' file containing JSON representation of input argument 'file@data' and its value - path to '\*.wav' input audio file.

Example of input file content:

```
{"file@data": "samples/sample.wav"}
```

You can call the service from SingularityNET CLI (`snet`).

Assuming that you have an open channel (`id: 0`) to this service:

```
$ snet client call 0 0.1 ?.naint.tech:? e2t samples/sample.txt

Read call params from the file: samples/sample.txt

text: "happy"
```

## What to expect from this service?

Input audio: samples/sample.wav

Response: text: "happy"
