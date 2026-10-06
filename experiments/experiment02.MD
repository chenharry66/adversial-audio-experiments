# Question

Are there certain frequency bands where adding noise is not only less noticeable but also results in higher transcription error?


## Setup

- Audio: Two forty second recordings of an excerpt from The Brothers Karamazov produced by me. Mono 16-bit PCM. 16khz.
- Model: facebook/wav2vec2-base-960h
- Metric of Comparison: WER from werpy, applying normalization before transcription
- Noise: Gaussian noise
- SNR: calculated over the entire duration of the recording


## Results

Across different snr values and the two different audios, I found that applying noise to the 1000-2000 Hz band gave the best balance of increasing WER and keeping the noise less noticeable.

While adding perturbations in the 2000-3000hz and 3000-4000hz regions increased WER more, the noise was quite noticeable. 

## Limitations

Two recordings, one model, and my own listening impressions. Results suggests a useful band to investigate, but doesn't establish that it's necessarily the best band.

## Next question

Given an audio and transcription model, can we generate an optimized perturbation that produce a higher WER (with the same snr budget) than random noise and band-passed noise. 
