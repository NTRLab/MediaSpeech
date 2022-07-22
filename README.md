# MediaSpeech
MediaSpeech is a media speech dataset (you might have guessed this) built with the purpose of testing Automated Speech Recognition (ASR) systems performance. The dataset consists of short speech segments automatically extracted from media videos available on YouTube and manually transcribed, with some pre- and post-processing.
The dataset contains 10 hours of speech for each language provided. This release contains audio datasets in French, Arabic, Turkish and Spanish, and is a part of a larger private dataset. The data is available courtesy of SLR: https://www.openslr.org/108/

Additional details can be found in the article: https://arxiv.org/abs/2103.16193

# Why
MediaSpeech can be used to test ASR models and systems that work well with real-world media speech data, or as a seed labelled dataset for semisupervised learning approaches. Baseline Quartznet models are provided for each language

# How
For the MediaSpeech dataset construction, we have selected a list of media with sufficient YouTube presence in each of the languages. For each of the channels , video recordings containing speech were selected. Audio tracks were loaded from the selected videos using the youtube_dl library. Each audio track was converted to single-channel 16 kHz 16-bit PCM encoded WAV files using FFmpeg.

Segmentation of audio data was performed using the Vosk speech recognition toolkit. Further, the resulting audio tracks were transferred to the VOSK speech recognition system to extract timestamps for each recognized word. Based on these timestamps, we sliced the audio track into segments less than 15 seconds long. Utterances that contain segments with no speech longer than 4 seconds were removed.

A system for manual transcription has been built specifically for the project. 

Each utterance has been first transcribed by an open-source ASR. The transcription was used as a prompt for human transcribers to speed up transcription. Later analysis revealed that some transcribers just copied the automated transcription for more complex audio fragments. These utterances have been removed on the post-processing stage.

For each human transcriber, a transcription pipeline is built by the transcription system. For the quality control purposes, 5% of the utterances were taken from an existing spoken corpus (Mozilla Common Voice)

Each utterance has been transcribed by two human transcribers. In the case where the relative WER of transcriptions was over 5%, the third transcriber resolved the conflict.

# Normalized Alphabets
The alphabets have been normalized as per the table below:
Language |	Alphabet
---------|----------
French	| azertyuiopqsdfghjklmùwxcvbné'èçàêôâûœ
Spanish	| abcdefghijklmnñopqrstuvwxyzáéíóúüé
Arabic |	أنت سيرإلىمحةاقثعهذفبئضودجصكخشزطءغظآؤ
Turkish	| abcçdefgğhıijklmnoöprsştuüvyz

# Citing

To cite the dataset, please use the following BibTeX entry:

<pre>
@misc{mediaspeech2021,
      title={MediaSpeech: Multilanguage ASR Benchmark and Dataset}, 
      author={Rostislav Kolobov and Olga Okhapkina and Olga Omelchishina, Andrey Platunov and Roman Bedyakin and Vyacheslav Moshkin and Dmitry Menshikov and Nikolay Mikhaylovskiy},
      year={2021},
      eprint={2103.16193},
      archivePrefix={arXiv},
      primaryClass={eess.AS}
}
</pre>

# License and copyright
The MediaSpeech dataset is distributed under the Creative Commons Attribution 4.0 International License. The copyright remains with the original owners of the video.

# Notice and take down policy
Notice: Should you consider that our data contains material that is owned by you and should therefore not be reproduced here, please:
- Clearly identify yourself, with detailed contact data such as an address, telephone number or email address at which you can be contacted.
- Clearly identify the copyrighted work claimed to be infringed.
- Clearly identify the material that is claimed to be infringing and information reasonably sufficient to allow us to locate the material.

Send the request to [Nick Mikhailovsky](mailto:nickm@ntr.ai)

Take down: We will comply to legitimate requests by removing the affected sources from the corpus.

# Commercial requests
Commercial requests related to larger datasets and other languages, as well as production quality ASR models, should be sent to info@ntr.ai
