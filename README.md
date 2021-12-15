# dsf2flac.dop.dsd256
Updated conversion tool for DSD files

This tool is a fork from https://code.google.com/archive/p/dsf2flac/

AudioFile.h is a modified version from https://github.com/adamstark/AudioFile

I wish many thanks to all the authors involved in such tool. For me this is the only free way to play DSD256 files on my dac without getting mad.

Support conversion from dsf or dff to wav files via DoP. DSD256 is supported by converting source dsf or dff to a DoP stream encapsulated in a 2 channels wav file 705600hz, 24 bit as flac actually does not support sample rates above 655350.

# Dependencies
Make sure to install the following:
```
sudo apt install libboost-all-dev
sudo apt install libogg-dev
sudo apt install libflac-dev
sudo apt install libflac++-dev
sudo apt install libid3-3.8.3-dev
sudo apt install libz-dev
```

# Compiling

Clone the repository: `git clone https://github.com/dhalsimax/dsf2flac`.

Then run the following commands:

```
ds2flac/build # cmake ..
ds2flac/build # make
```

# Examples
## FFmpeg ADI-2 DAC pipe example

`dsf2flac -d -w -i "pathtofile" -o -  | ffmpeg -i - -c pcm_s32le -f alsa iec958:CARD=DAC57750571,DEV=0`

Well tested up to DSD256 dsf to DoP wav conversion with rme ADI 2 DAC.

Replace all after ffmpeg -f parameter with your alsa device name to try it out with your DAC. List of available alsa device names can be obtained with alsa command: `aplay -L`