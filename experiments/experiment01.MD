# Experiment 01: Filtering and Adding Noise

## Question

How do simple modifications to audio affect transcription results and also the sound of the recording

## Setup

- Audio: One forty second recording of an excerpt from *The Brothers Karamazov* produced by yours truly. Mono 16-bit PCM. 16khz.
- Model: facebook/wav2vec2-base-960h
- Metric of Comparison: WER from werpy, applying normalization before transcription
- Noise: Gaussian noise
- SNR: calculated over the entire duration of teh recording

## Results

- Low Pass Filter: (Cutoff: Original, WER: 0.178571), (Cutoff: 7000Hz, WER: 0.190476), (Cutoff: 5000Hz, WER: 0.202381), (Cutoff: 3000Hz, WER: 0.261905)
- High Pass Filter: (Cutoff: Original, WER: 0.178571), (Cutoff: 200Hz, WER: 0.250), (Cutoff: 500Hz, WER: 0.404762), (Cutoff: 700Hz, WER: 0.607143)
- SNR: (SNR: Original, WER: 0.178571), (SNR: 10, WER: 0.940476), (SNR: 20, WER: 0.511905), (SNR: 22, WER: 0.41667), (SNR: 25, WER: 0.309524), (SNR: 30, WER: 0.238095),(SNR: 35, WER:0.178571)

## Listening Observations

- Low Pass:
  - No huge difference between how the audio sounded and the transcription error.
  - Cutoffs of 7000 and 5000hz didn't have a big difference in the audio quality or the error.
  - When lowered to 3000hz both the error and the distortion jump significantly.
- High Pass:
  - More or less consistent with the low-pass results. Perceived sound quality correlates with the WER.
- SNR:
  - After crossing a certain threshold, increasing SNR stops affecting WER. There is also this weird sort of limbo zone at
    SNR 30 and 35 where I can't really hear a big difference in terms of the amount of noise in the audio, but SNR of 35 has the same WER as the original recording, whereas SNR of 30 is still 5% off.

## Limitations

- One recording, one listener, one model

## Next question

Instead of applying perturbations to the entire recording, can we identify moments/frequencies where perturbations are more effective?
