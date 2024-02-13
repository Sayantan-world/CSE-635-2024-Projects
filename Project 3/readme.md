# Project 1: LLMs in the Arts

### Overview
The project explores the intersection of AI and music, harnessing the power of LLMs to classify music into genres or moods and generate chord progressions that match given situational prompts. This initiative aims to democratize music composition, offering musicians, composers, and enthusiasts new tools to inspire creativity and innovation. By understanding and generating musical elements, the project showcases the potential of AI to complement human creativity, offering a new lens through which to explore the emotional and expressive capacities of music.


### Tasks
- Text Prompt to Lyrics Generation: Develop a Language model that can generate lyrics based on short text prompt
- Text-Based Music Genre Classification: Develop a system that can classify the likely music genre of a song based on its lyrics alone, identifying themes and emotions that align with specific musical genres.
    - Million Songs Dataset: http://millionsongdataset.com/index.html
    - Musixmatch Dataset: http://millionsongdataset.com/musixmatch/
    - Lyrics Dataset: https://www.cs.cornell.edu/~arb/data/genius-expertise/
- Chord Progression Generation: Create a model that suggests chord progressions fitting the lyrical content's emotional tone and thematic context, facilitating the music composition process for songwriters.
    - Create your custom dataset: https://www.hooktheory.com/theorytab

The system should have the following capabilities.
- Generate lyrics from a short prompt
- Classify the lyrics using NLP techniques to a song genre
- Generate chord progression for the song based on the identified genre



### Datasets
You are free to use any relevant dataset that you want. Here are some recommendations and one of them that you have to use. You need to create your own custom dataset

- Million Songs Dataset: http://millionsongdataset.com/index.html
- Musixmatch Dataset: http://millionsongdataset.com/musixmatch/
- Genius-expertise Dataset: https://www.cs.cornell.edu/~arb/data/genius-expertise/


### Evaluation Metrics:

Human evaluation will be conducted. A score will be assigned (scale 0-5) on different factors.
- Harmonic Coherence: How well do the chords fit together in a sequence? Do they form a pleasing progression, and are they appropriate for the genre?
- Lyric-to-Chord AlignmentHow well do the chords match the mood and content of the lyrics
- Genre Appropriateness: Are the chords and their progressions typical for the genre specified
- Melodic Compatibility: If there is a melody, how well do the chords support it
- Musicality: Overall, do the chords contribute to a musical piece that would be enjoyable and engaging to listen to


### Example

**Prompt**: A happy pig dancing in the sunny weather

**Generated Lyrics**:

```
In the field where the sunflowers sway,
A happy pig dances the day away.
With a twirl and a snort under skies so blue,
She waltzes in mud, without a shoe.

The sun beams down with a tender glow,
On her pink little nose, as she taps a toe.
Beneath the bright sun, her joy never withers,
She's the belle of the barnyard, as she happily shivers.
```

**Genre Classifier**: Country, Children's Music
**Suggested Key**: C 
**Chord Progression**: 
- I vi IV V
- I V vi IV

Chord Progression (I vi IV V): https://chordchord.com/preview/tC16ByQr


### Resources

##### Related papers:
- https://asmp-eurasipjournals.springeropen.com/articles/10.1186/s13636-023-00288-5
- https://aclanthology.org/2021.findings-acl.70/
