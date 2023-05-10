pip install pydub
import os
from pydub import AudioSegment

def mp3_to_wav(mp3_folder, wav_folder):
    for file in os.listdir(mp3_folder):
        if file.endswith('.mp3'):
            mp3_file = os.path.join(mp3_folder, file)
            wav_file = os.path.join(wav_folder, file.replace('.mp3', '.wav'))
            sound = AudioSegment.from_mp3(mp3_file)
            sound.export(wav_file, format='wav')

if __name__ == '__main__':
    import argparse
    parser = argparse.ArgumentParser(description='Convert a set of MP3 files to WAV format.')
    parser.add_argument('mp3_folder', help='The folder containing the MP3 files.')
    parser.add_argument('wav_folder', help='The folder to save the WAV files.')
    args = parser.parse_args()
    mp3_to_wav(args.mp3_folder, args.wav_folder)

