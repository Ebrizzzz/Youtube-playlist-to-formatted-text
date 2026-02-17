# YouTube Playlist Processor
<br>
<br>

![Alt text for the image](Images/image.jpg)<br><br>



✅ Added several Refinement styles to choose from based on your specific needs.
> The "Refinement Style" dropdown allows you to choose how AI will process the YouTube transcript. Here's a description of each style:
    
>> ⚖️ **Balanced and Detailed**: This is the default style, providing a comprehensive refinement of the transcript. It focuses on organizing the text into a well-structured, readable format with headings, bullet points, and bold text, while preserving every detail, context, and nuance of the original content. Ideal if you want a thoroughly enhanced transcript without any information loss.
    
>> 📝 **Summary**:  This style generates a concise and informative summary of the video transcript. It extracts the core message, main arguments, and key information, providing a quick and easily digestible overview of the video's content. Best for when you need to quickly grasp the main points without reading the entire transcript.
    
>> 📚 **Educational**: This style transforms the transcript into a structured educational text, similar to a textbook chapter. It uses headings, subheadings, and bullet points for clarity and organization, making it ideal for learning.  **Crucially, it also identifies and defines technical terms and jargon within blockquotes, enhancing understanding and acting as a built-in glossary. (Example Image Below)**
    
>> ✍️ **Narrative Rewriting**:  This style creatively rewrites the transcript into an engaging narrative or story format. It transforms the factual or conversational content into a more captivating and readable piece, like a short story or narrative article.  While storytelling is applied, it stays closely aligned with the original video's subjects and information, making the content more accessible and enjoyable.
    
>> ❓ **Q&A Generation**:  This style generates a set of questions and answers based on the transcript, formatted for self-assessment or review. Each question is presented as a foldable header (using Markdown), with the answer hidden beneath.  This format is perfect for creating study guides or quizzes to test your understanding of the video content.(Example Image Below)<br><br>


✅ Added Language Support, now the output file is in the language of user's input. Also, the video can be in any language, as long as a transcript exists, it will work. <br>
✅ Added single video url support, no need to put it in a playlist.<br>
✅ Added configurable Chunk Size for API calls.<br>

>> Users can now control the chunk size used when processing transcripts with the Gemini API via a slider in the UI. This allows for customization of processing behavior:
>>- Larger chunk sizes: Reduce the number of API calls, potentially speeding up execution and suitable for summarizing longer videos with less emphasis on fine details.
>>- Smaller chunk sizes: Increase API calls but may preserve more detail and nuance, potentially beneficial for tasks requiring high fidelity output.<br><br>
>> ❓ What is **Chunk Size**?<br>
>>  A video, is divided into chunks to be given to AI, so if you set chunk size to 3000 words, and the video has 8000 words, the API workflow would be like this :
>>  > - First 3000 words ➡➡processed by AI➡➡ Refined part 1
>>  > - Second 3000 words +  Refined part 1 as context ➡➡processed by AI➡➡ Refinde part 2
>>  > - final 2000 words +  Refined part 1  + 2 as context ➡➡processed by AI➡➡ Refinde part 3
>>  > - Refined part 1 + Refined part 2 + Refined part 3 = Final Formatted Text of the video!

<br>
<br>
This Python application extracts transcripts from YouTube playlists and refines them using the Google Gemini API(which is free). It takes a YouTube playlist URL as input, extracts transcripts for each video, and then uses Gemini to reformat and improve the readability of the combined transcript. The output is saved as a text file.
<br><br>
So you can have a neatly formatted book out of a YouTube playlist!<br>
I personally use it to convert large YouTube playlists containing dozens of long videos into a very large organized markdown file to give it as input to NotebookLM as one source.<br>
Works Great with Obsidian too!<br><br>

Read more about it in this [Medium Article](https://medium.com/@ebrahimgolriz444/a-tool-to-turn-entire-youtube-playlists-to-markdown-formatted-and-refined-text-books-in-any-3e8742f5d0d3)
<br><br>

*   Batch processing of entire playlists
*   Refine transcripts using Google Gemini API for improved formatting and readability.
*   User-friendly PyQt5 graphical interface.
*   Selectable Gemini models.
*   Output to markdown file.
<br><br><br><br>


![Alt text for the image](Images/image2.png)<br><br>



## Features
- 🎥 Automatic transcript extraction from YouTube playlists
- 🧠 AI-powered text refinement using Gemini models
- 📁 Configurable output file paths
- ⏳ Progress tracking for both extraction and refinement
- 📄 Output to formatted markdown file.

## Requirements
- Python 3.9+
- Google Gemini API key
- YouTube playlist URL

## Installation
```bash
pip install -r requirements.txt
```
## How does it work?
* First, the transcript of every video in the playlist is fetched.
* since gemini api doesnt have unlimited context window for input and output, the text for each video gets divided into chunks(right now, chunk size is set to 3000 after testing, but it can be changed via the added slider)
* Each text chunk is then sent to the Gemini API, along with a context prompt that includes the previously refined text. This helps maintain consistency and coherence across chunks.
* The refined output from Gemini for each chunk is appended to the final output file.
* This process is repeated for every video in the playlist, resulting in a single, refined transcript output file for the entire playlist.
    
## Usage

1.  **Get a Gemini API Key:** You need a Google Gemini API key. Obtain one from [Google AI Studio](https://ai.google.dev/gemini-api/docs/api-key).
2.  **Run the Application:**
    ```bash
    python main.py
    ```
3.  **In the GUI:**
    *   Enter the YouTube Playlist URL or Video link.
    *   Type the Output Language.
    *   choose the style of output.
    *   Specify chunk size.
    *   Choose output file locations for the transcript and Gemini refined text using the "Choose File" buttons.
    *   Enter your Gemini API key in the "Gemini API Key" field.
    *   Click "Start Processing".
    *   You can select a Gemini model.
    *   Wait for the processing to complete. Progress will be shown in the progress bar and status display.
    *   The output files will be saved to the locations you specified.
  
![Alt text for the image](Images/ED.png)
_Example of Educational Style with added definition of technical terms_
<br><br>
![Alt text for the image](Images/QA.png)
_Example of Q&A Style, Questions are headers so they can be folded/unfolded_
<br><br>

> YouTube playlist used for example files : https://www.youtube.com/playlist?list=PLmHVyfmcRKyx1KSoobwukzf1Nf-Y97Rw0
