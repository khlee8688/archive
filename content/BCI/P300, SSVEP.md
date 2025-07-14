### EEG  
- an electrical signal measured from the scalp  
- Advantages: High time resolution, portability and affordability  
- Disadvantages: Low spatial resolution, noise sensitive  
  
## P300 Speller  
### Concepts  
- The P300 (or P3) waveform is an event-related potential (ERP) component caused by the decision-making process.  
- The ERP-based P300 Speller should improve the signal-to-noise ratio (SNR) through signal averaging in signals mixed with noise.  
- It is produced in response to stimuli that occur infrequently after 300 ms and is closely related to the timing of the stimulus.  
- The induced potential (EP) is temporally fixed by repetitive stimulation and has a constant composition.  
- On the other hand, the background noise occurs at random times and its shape continues to change.  
  
### Other Components  
### P1  
- Time of occurrence: approximately 65 to 90 ms  
- Visually Evoked Potentials (VEP) Related to Visual Stimulation Processing  
- Created in the Primary Visual Cortex  
### N1  
- Time of occurrence: approximately 80 to 120 ms  
- It mainly responds to auditory stimulation,  
- N1 visual stimulation  
- Responsive to olfactory, fever, pain, balance, respiratory block, somatosensory stimulation  
- Amplitude is sensitive to rising time, intensity, spacing between stimuli, frequency differences, etc. of sound  
### N2  
- Time of occurrence: approximately 200-350 ms  
- Observed in the central-front area  
- Related to cognitive control  
- Amplitude increases when stimulus is different or inconsistent from expectations  
### ERN / NE  
- Error-related Negativity (ERN) 또는 Error Negativity (NE)  
- Time of occurrence: approximately 50 to 100 ms  
- Occurs when you recognize your mistake  
- Again, cognitive control, responding to unexpected stimulus properties or inconsistencies  
  
---  
## SSVEP  
### Concepts  
- Steady-State Visually Evoked Potential (SSVEP) is a natural brain response to a specific frequency of visual stimulation (blinking light).  
- A signal of the same period as the flickering frequency of the stimulus occurs.  
- The frequency of the generated signal is directly connected to the stimulus frequency  
- Fast reaction rate, high information transfer rate, low learning burden.  
### Method of Analysis  
### Fourier Transformation  
- Basic conversion methods for analyzing components in the frequency domain  
### Power Spectrum Analysis  
- Visualize and analyze the strength of each frequency component of the signal  
### Pspectrum  
- Time-frequency domain analysis tool  
- Can analyze the temporal variation and frequency composition of the signal together  
### CCA (Canonical Correlation Analysis)  
- The correlation between multi-channel EEG signals and sinusoidal reference signals corresponding to the stimulation frequency is analyzed  
- For each stimulus frequency, a correlation value is calculated to select the frequency with the highest canonical correlation value (Nakanishi et al., 2015)