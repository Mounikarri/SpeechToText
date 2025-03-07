# SpeechToText
import speech_recognition as sr
recognizer = sr.Recognizer()
with sr.Microphone() as source:
    print("Adjusting the noise... Please wait.")
    recognizer.adjust_for_ambient_noise(source)
    print("Start speaking!!!")
    audio = recognizer.listen(source)
    print("Analyzing the speech, Thank you!!")
try:
    print("Recognizing...")
    text = recognizer.recognize_google(audio)
    print("You said: " + text)
except sr.UnknownValueError:
    print("Sorry, I could not understand the audio")
except sr.RequestError as e:
    print("Could not request results from Google Speech Recognition service; {0}".format(e))
