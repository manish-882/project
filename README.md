# project
ai
import pyttsx3  # pip install pyttsx3
import speech_recognition as sr  # pip install speechrecognition
import datetime  # pip install datetime
import wikipedia  # pip install wiikipedia
import webbrowser  # pip install Webbrowser
import os  # pip install os
import pywhatkit as kit  # pip installpywhatkit
import pyjokes  # pip install pyjokes
import requests

engine = pyttsx3.init('sapi5')  # it converts speech to text.
voices = engine.getProperty('voices')
# print(voices[1].id)
engine.setProperty('voice', voices[1].id)


def speak(audio):
    engine.say(audio)
    engine.runAndWait()


def wishme():
    '''hour = int(datetime.datetime.now().hour)
    if hour >= 0 and hour <=12:
        speak('good morning sir!')
        print('good morning sir!')
    elif hour >=12 and hour < 18:
        speak('good afternoon sir!')
        print('good afternoon sir!')
    else:
        speak('good evening choooew!')
        print('good evening sir!')'''
    speak(" hi sir . how may i help you")
    print("hi sir , how may i help you")


def takeCommand():
    # it takes microphone input from user and returns string output.

    r = sr.Recognizer()
    with sr.Microphone() as source:
        print('listening......')
        speak('listening....!')
        r.pause_threshold = 0.5
        audio = r.listen(source)

    try:
        print("recognizing...")
        query = r.recognize_google(audio, language='en-in')
        print("user said: ", query)

    except Exception as e:
        print(e)

        print("sorry , please say that again")
        speak("sorry , please say that again")
        return "none"
    return query


'''def Alarm(query):

    alarmtime = open("D:\Assistant\\alarm.txt", "a")
    alarmtime.write(query)
    alarmtime.close()
    os.startfile("")
Alarm("set alarm for 10:00")'''

if __name__ == "__main__":
    wishme()
    # while True:
    if 1:
        query = takeCommand().lower()

        # logic for executing tasks based on query
        if 'wikipedia' in query:
            speak("searching wikipedia ....")
            print("searching...")
            query = query.replace("wikipeia", "")
            results = wikipedia.summary(query, sentences=2)
            speak("aaccprding to wikipedia")
            print(results)
            speak(results)
        elif 'what is ' in query:
            speak("searching wikipedia ....")
            print("searching")
            query = query.replace("what is ", "")
            results = wikipedia.summary(query, sentences=2)
            speak("according to wikipedia...")
            print(results)
            speak(results)
        elif 'who is ' in query:
            speak("searching wikipedia ....")
            print("searching")
            query = query.replace("who is ", "")
            results = wikipedia.summary(query, sentences=2)
            speak("according to wikipedia...")
            print(results)
            speak(results)

        elif 'youtube' in query:
            webbrowser.open("youtube.com")
            speak("opened youtube")


        elif 'google' in query:
            webbrowser.open("www.google.com")

        elif 'open github' in query:
            webbrowser.open("github.com")

        elif 'open bing' in query:
            webbrowser.open("bing.com")

        elif 'facebook' in query:
            webbrowser.open("www.facebook.com")

        elif 'instagram' in query:
            webbrowser.open("www.instagram.com")

        elif 'music' in query:
            music = 'C:\\Users\\manis\\Desktop\\songs'
            song = os.listdir(music)
            print(song)
            os.startfile(os.path.join(music, song[1]))

        elif 'time' in query:
            # nowtime = datetime.datetime.now().strftime("%H:%M:%S")
            nowtime = datetime.datetime.now().strftime("%I:%M %p")
            speak(f"chooow , time is {nowtime}")
            print(f"chow ,time is {nowtime}")

        elif 'open code' in query:
            codepath = "C:\\Users\\manis\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"
            os.startfile(codepath)
            speak("opened v s code")
        elif 'close code' in query:
            os.system("taskkill /f /im code.exe")

        elif 'open whatsapp' in query:
            webbrowser.open("web.whatsapp.com")

        elif 'play' in query:
            video = query.replace("play", "")
            speak(f"playing {video}")
            kit.playonyt(video)

        elif 'message' in query:
            kit.sendwhatmsg_instantly("+916305695302", "this is python generated message")

        elif 'search' in query:
            browse = query.replace("search", "")
            kit.search(browse)

        elif 'joke' in query:
            joke = pyjokes.get_joke()
            print(joke)
            speak(joke)

        elif 'my website' in query:
            my_web = ("manish12.me")
            kit.search(my_web)
            speak("opened website")

        elif 'open downloads' in query:
            route = "C:\\Users\\manis"
            os.startfile(route)
            print('opened downloads')
            speak('opened downloads')

        elif 'open meeting' in query:
            zoom = "C:\\Users\\manis\\AppData\\Roaming\\Zoom\\bin\\Zoom.exe"
            os.startfile(zoom)

        elif 'close meeting' in query:
            os.system("taskkill /f /im Zoom.exe")


        elif 'open chrome' in query:
            chrome_browser = "C:\\Program Files\\Google\\Chrome\\Application\\chrome.exe"
            os.startfile(chrome_browser)
            speak("opened chrome")

        elif 'close chrome' in query:
            os.system("taskkill /f /im chrome.exe")
            speak("closed chrome")




        elif 'quit' in query:
            print("bye sir")
            speak("bye sir")
            exit()














                    


            



    #speak('Manish is a good boy')'''
