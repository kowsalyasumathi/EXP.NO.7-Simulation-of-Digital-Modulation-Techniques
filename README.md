# EXP.NO.7-Simulation-of-Digital-Modulation-Techniques
7. Simulation of Digital Modulation Techniques Such as
   i) Amplitude Shift Keying (ASK)
   ii) Frequency Shift Keying (FSK)
   iii) Phase Shift Keying (PSK)
   
# AIM:
To simulate digital modulation techniques such as:
1. Amplitude Shift Keying (ASK)
2. Frequency Shift Keying (FSK)
3. Phase Shift Keying (PSK).

# SOFTWARE REQUIRED:
Google Colab (python).

### ALGORITHM
## Amplitude Shift Keying (ASK) Algorithm
Input:

Digital bit stream

Carrier frequency fc

Bit duration Tb

Sampling frequency fs

Steps:

Start

Define bit stream (e.g., [1, 0, 1, 1, 0])

For each bit in the stream:

Generate time vector t for one bit duration

If bit is 1:

Generate carrier signal: A * cos(2πfct)

If bit is 0:

Generate signal with amplitude = 0 (i.e., 0)

Append the result to the ASK signal

Plot the ASK modulated signal

End

## Frequency Shift Keying (FSK) Algorithm
Input:

Digital bit stream

Frequencies f1 and f2

Bit duration Tb

Sampling frequency fs

Steps:

Start

Define bit stream

For each bit in the stream:

Generate time vector t for one bit duration

If bit is 1:

Generate signal: cos(2πf1t)

If bit is 0:

Generate signal: cos(2πf2t)

Append the result to the FSK signal

Plot the FSK modulated signal

End

## Phase Shift Keying (PSK) Algorithm (BPSK)
Input:

Digital bit stream

Carrier frequency fc

Bit duration Tb

Sampling frequency fs

Steps:

Start

Define bit stream

For each bit in the stream:

Generate time vector t for one bit duration

If bit is 1:

Generate signal: cos(2πfct + 0°)

If bit is 0:

Generate signal: cos(2πfct + 180°) → i.e., -cos(2πfct)

Append the result to the PSK signal

Plot the PSK modulated signal

End



## PROGRAM:
```
# Import necessary libraries
import numpy as np
import matplotlib.pyplot as plt

# Digital input bit stream
bit_stream = [1, 0, 1, 1, 0, 0, 1]
bit_duration = 1  # in seconds
fs = 1000  # Sampling frequency in Hz
t = np.linspace(0, bit_duration, int(fs * bit_duration), endpoint=False)

# Carrier properties
fc = 5  # Carrier frequency for ASK/PSK
f1 = 5  # FSK frequency for bit 1
f2 = 2  # FSK frequency for bit 0

# Generate digital signal for visualization
digital_signal = np.array([])
for bit in bit_stream:
    digital_signal = np.concatenate((digital_signal, bit * np.ones_like(t)))

# Generate ASK signal
ask_signal = np.array([])
for bit in bit_stream:
    if bit == 1:
        ask_signal = np.concatenate((ask_signal, np.cos(2 * np.pi * fc * t)))
    else:
        ask_signal = np.concatenate((ask_signal, np.zeros_like(t)))

# Generate FSK signal
fsk_signal = np.array([])
for bit in bit_stream:
    freq = f1 if bit == 1 else f2
    fsk_signal = np.concatenate((fsk_signal, np.cos(2 * np.pi * freq * t)))

# Generate PSK signal (BPSK)
psk_signal = np.array([])
for bit in bit_stream:
    phase = 0 if bit == 1 else np.pi
    psk_signal = np.concatenate((psk_signal, np.cos(2 * np.pi * fc * t + phase)))

# Time axis
full_time = np.linspace(0, bit_duration * len(bit_stream), len(digital_signal), endpoint=False)

# Plotting all signals
plt.figure(figsize=(15, 12))

plt.subplot(4, 1, 1)
plt.plot(full_time, digital_signal, color='black')
plt.title("Digital Input Signal")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.subplot(4, 1, 2)
plt.plot(full_time, ask_signal, color='blue')
plt.title("Amplitude Shift Keying (ASK)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.subplot(4, 1, 3)
plt.plot(full_time, fsk_signal, color='green')
plt.title("Frequency Shift Keying (FSK)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.subplot(4, 1, 4)
plt.plot(full_time, psk_signal, color='red')
plt.title("Phase Shift Keying (PSK)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.tight_layout()
plt.show()

```

## OUTPUT:

![image](https://github.com/user-attachments/assets/ad310f26-9622-41cd-9ad8-683223e1f774)
 
## RESULT:
Thus the simulation of digital modulation techniques using ASK, FSK, and PSK were successfully simulated and the output is obtained.


