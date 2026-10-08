# POCSAG SDR — FSK Decoder & Transmitter

A Python-based implementation of **POCSAG (Post Office Code Standardisation Advisory Group)** paging signals using IQ data and digital signal processing.

## What is POCSAG?

POCSAG is a digital paging protocol used to transmit messages to pagers. It uses **FSK modulation** and organizes data into 32-bit codewords containing synchronization, address, message, BCH error correction, and parity information.

## What I Implemented

### RX — POCSAG Decoder

* Read complex IQ samples from a `.wav` file
* Converted I/Q samples into complex baseband
* Performed phase-difference detection for FSK demodulation
* Smoothed and sampled the recovered signal
* Automatically searched different baud rates, sampling offsets, and bit polarity
* Detected POCSAG synchronization words
* Implemented BCH error checking using XOR polynomial division
* Verified parity bits
* Extracted pager addresses and message payloads
* Converted 7-bit character data into readable text

### TX — POCSAG Signal Generator

* Converted a custom message into 7-bit characters
* Generated POCSAG message codewords
* Added BCH error-correction bits
* Added parity bits
* Generated address and idle codewords
* Constructed batches, frames, synchronization words, and preamble
* Generated a **1200-baud FSK baseband signal**
* Generated complex I/Q samples and saved them as an `.iq` file

## Concepts Learned

This project helped me understand the complete digital communication chain:

**Message → Encoding → BCH → Parity → POCSAG framing → FSK modulation → IQ samples**

and the reverse:

**IQ samples → FSK demodulation → Bit recovery → Synchronization → BCH/Parity → POCSAG decoding → Message**

### DSP / Communication Concepts

* I/Q signals
* Complex baseband
* Phase-difference FSK demodulation
* Symbol/bit timing
* Sampling offsets
* Signal smoothing
* Bit polarity
* Digital modulation
* Frequency deviation
* Sampling rate and samples/bit

### Error Correction & Protocol Concepts

* BCH error correction
* XOR polynomial division
* Parity checking
* Bit ordering / LSB-first transmission
* Codewords
* Synchronization words
* Addresses and message payloads
* POCSAG batches and frames

## Files

* `POCSAG_RX.ipynb` — POCSAG IQ signal decoder
* `POCSAG_TX.ipynb` — POCSAG signal generator
* `POCSAG_IQ.wav` — IQ recording used for decoding
