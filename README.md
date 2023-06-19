# Overview

The purpose of this project was to create a machine-learning model that could detect the mating call ("kick-ee-doo" or "kick-kick-ee-doo") of black rails from .wav files.

## Background

The Eastern Black Rail (Laterallus jamaicensis jamaicensis) is a secretive marsh bird whose historic range extended throughout most of the eastern United States. Black Rails were recently listed by the US Fish & Wildlife Service as Threatened; Florida has them listed as state-endangered. Black Rails primarily breed in shallow, heavily vegetated coastal marsh habitat; however, increased sea-level rise and urban development have drastically reduced the breeding population. Florida boasts a wide variety of non-traditional Black Rail habitats: stormwater treatment areas, impoundments, and non-tidal, interior lake marshes. Because Black Rails are small, cryptic, and less vocal than other marsh birds, standard visual and audial surveys are often ineffective. Autonomous recording units (ARUs) are increasingly being utilized by scientists to monitor Black Rails because they are relatively cheap, easy to deploy, and can be programmed to record throughout the day and night. However, ARUs can easily accrue hundreds of hours of recordings, which are onerous and time-consuming to sift through.

![Black_Rail_Photo](https://github.com/CSoldo1/Black_Rail_Audio_Detection/assets/114112078/66edea3c-d8a0-4e43-ab23-d3550023e1b8)

A "lost" Black Rail photographed in a flooded farm field in Illinois.

![SM4_Audio_Recorder](https://github.com/CSoldo1/Black_Rail_Audio_Detection/assets/114112078/ad660552-94f1-49e4-8e08-01ac8c32bd49)

One of several audio recorders deployed in the marsh of Lake Okeechobee. 

## Resources
* Hundred of hour-long .wav files collected with Song Meter SM4 from Wildlife Acoustics
* Black Rail audio files from Xeno Canto
* Jupyter Notebook
* Python
* TensorFlow Package

## Analysis
* Code for model can be found in repo under "BLRA_DNN"
To detect Black Rail (BLRA) calls, I turned the audio detection problem into an image classification problem. Black Rails have a very unique mating call, and therefore, the waveform of the call would have a unique spectrogram. By converting the waveforms to a spectrogram, the model could then identify the appropriate "picture" of each BLRA call.

My first step was training the model. I downloaded, amplified, clipped, and edited BLRA mating calls from Xeno Canto. Essentially, I told the model: "THIS IS A BLACK RAIL CALL."

![BLRA_wave](https://github.com/CSoldo1/Black_Rail_Audio_Detection/assets/114112078/7093c312-f8fe-48a4-986e-e32a8b934bf2)

The waveform of a BLRA "kick-ee-doo" call.

BLRA mating calls are approximately 1 second long, and they can be depicted by the following spectrogram.

![BLRA_spectrogram](https://github.com/CSoldo1/Black_Rail_Audio_Detection/assets/114112078/1638dfbc-48d5-451a-9b0d-437ef1016821)

My next step was to have the model break down any audio file I passed through it into 1-second clips. A waveform was created for each audio clip and a spectrogram was created for each waveform. The model then went through each spectrogram and looked for ones that matched with the BLRA spectrogram. 

I tested the model by creating a 13-second practice audio file that I knew contained BLRA calls, along with one that did not. The model was able to correctly identify which audio file had the BLRA calls. 

## Future Work
Although the model can correctly identify BLRA calls, there is still a lot of work needed to make it usable. For instance, each recording I have from the SM4s is an hour long. Will the model be able to adequately run through such a large file? Can it do it quickly without blowing up my computer? If the audio file is 1 hour, I will have 3600 spectrograms. Should I randomly select half of them to run through the model? 

Furthermore, I want this model to be accessible to others. I am currently working on building a graphical user interface so that other biologists throughout the state can run their audio files through it. 

I will continue to update this repo as I make more progress. 
