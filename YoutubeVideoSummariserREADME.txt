# Video Summarizer 

Open Colab.research.google

here's the code:
1.!pip install -q transformers
-RUN
2.!pip install -q youtube_transcript_api
-RUN
3.from transformers import pipeline
-RUN
from youtube_transcript_api import YouTubeTranscriptApi
-RUN
4.youtube_video = "https://www.youtube.com/watch?v=qHdZQjlq1-Q"
-RUN
If you want new Youtube Video summarizer,then change the Video Id 
-RUN
5.video_id = youtube_video.split("=")[1]
-RUN
6.video_id
-RUN
7.from IPython.display import YouTubeVideo
YouTubeVideo(video_id)
-RUN
8.YouTubeTranscriptApi.get_transcript(video_id)
transcript = YouTubeTranscriptApi.get_transcript(video_id)
-RUN
9.transcript[0:5]
-RUN
10.result = ""
for i in transcript:
    result += ' ' + i['text']
#print(result)
print(len(result))
-RUN
11.summarizer = pipeline('summarization')
-RUN
12.num_iters = int(len(result)/1000)
summarized_text = []
for i in range(0, num_iters + 1):
  start = 0
  start = i * 1000
  end = (i + 1) * 1000
  print("input text \n" + result[start:end])
  out = summarizer(result[start:end])
  out = out[0]
  out = out['summary_text']
  print("Summarized text\n"+out)
  summarized_text.append(out)

#print(summarized_text)
-RUN
