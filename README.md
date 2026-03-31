# AutoEIT-Transcription

## Objectives

- Transcribe L2 learner audio using state-of-the-art ASR
- Preserve disfluencies (e.g., "uh", "este", pauses)
- Align output to fixed EIT structure (30 sentences)
- Evaluate performance using WER and CER
- Generate structured output for further scoring

## Methodology

### 1. Audio Preprocessing

- Resampled to 16kHz
- Noise reduction using spectral gating
- Amplitude normalization
- Silence trimming

### 2. Automatic Speech Recognition

- Model: **Whisper large-v3**
- Language forced to Spanish (`language="es"`)
- Deterministic decoding (`temperature=0`)
- No context carryover (`condition_on_previous_text=False`)

### 3. Segmentation

- Whisper outputs variable segments (~30–40)
- Converted into fixed **30 EIT responses**
- Missing responses filled with `[no_response]`

### 4. Post-processing

- Removed ASR artifacts (e.g., `[Music]`)
- Lowercased output
- Preserved disfluencies

### 5. Evaluation

- **Word Error Rate (WER)**
- **Character Error Rate (CER)**

## Results

| Participant | WER | Agreement |
|------------|-----|----------|
| 038015 | XX% | XX% |
| 038012 | XX% | XX% |
| 038011 | XX% | XX% |
| 038010 | XX% | XX% |

> Agreement = (1 - WER)

## Key Insights

- Whisper produces **variable segmentation (~30–40 segments)** instead of fixed 30 responses
- Non-native speech significantly impacts ASR confidence
- Noise reduction improves transcription quality
- Forced language decoding reduces incorrect language switching

## Challenges

- Mapping ASR segments to fixed EIT responses
- Distinguishing disfluency vs ASR error
- Handling low-proficiency learner speech
- Variability in audio quality

## Future Improvements

- Forced alignment (e.g., WhisperX)
- Fine-tuning on L2 learner data
- Confidence-based filtering
- LLM-based transcription refinement
