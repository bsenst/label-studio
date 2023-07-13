---
title: Audio Transcription Context
type: templates
category: Audio/Speech Processing
cat: audio-speech-processing
order: 307
meta_title: Audio Transcription Context 
meta_description: Template annotating transcriptions in their audio context.
---

<img src="/images/templates-misc/audio-transcription-context.png" alt="" class="gif-border" width="482px" height="282px" />

 The context scroll feature of paragraphs allows for playback synchronization between audio segments and corresponding paragraph segments, enabling users to control the audio player with the relevant paragraph segment and see which segment is related to which section of the audio file. 

## Interactive Template Preview

<div id="main-preview"></div>

## Labeling Configuration

```html
<View>
  <Audio name="audio" value="$url" sync="text"></Audio>
    <View>
    <Header value="Transcript"/>
    <Paragraphs audioUrl="$audio" contextScroll="true" sync="audio" name="text" value="$text" layout="dialogue" textKey="text" nameKey="author" granularity="paragraph"/>
  </View>  
    <View>
      <Header value="Sentiment Labels"/>
      <ParagraphLabels  name="label" toName="text">
        <Label value="Positive" background="#00ff00"/>
        <Label value="Negative" background="#ff0000"/>
      </ParagraphLabels>
    </View>
</View>
```

## About the labeling configuration

All labeling configurations must be wrapped in [View](/tags/view.html) tags.

You can add a [header](/tags/header.html) to provide instructions to the annotator:
```xml
<Header value="Listen to the audio:"></Header>
```

Use the [Audio](/tags/audio.html) object tag to specify the type and the location of the audio clip. In this case, the audio clip is stored with a `url` key. Audio paired with the [Paragraphs](/tags/paragraphs.html) with 'contextScroll' set to true and `sync` set to audio. Additionally `name` of the paragraph tag should have the `textKey` value from the audio tag:
```xml
<Audio name="audio" value="$url" sync="text"></Audio>
<Paragraphs audioUrl="$audio" contextScroll="true" sync="audio" name="text" value="$text" layout="dialogue" textKey="text" nameKey="author" granularity="paragraph"/>
```

Use the [Paragraph Lables](/tags/paragraphlabels.html) control tag with the [Label](/tags/label.html) tag to annotate sections of the paragraph transcriptions.
```xml
<ParagraphLabels  name="label" toName="text">
  <Label value="Positive" background="#00ff00"/>
  <Label value="Negative" background="#ff0000"/>
</ParagraphLabels>
```

## Enhance this template
This template can be enhanced in many ways.

### Add additional data points

A number of tags can be added to this template to add more data points to the annotation. Here we added [Choices](/tags/choices.html) and [TextArea](/tags/textarea.html) tags to give speaker context and a text responsce to the transcription:
```xml
<View>
  <Choices name="speakers" toName="audio" choice="multiple" showInline="true">
  <Choice value="speaker_1"/>
  <Choice value="speaker_2"/>
</Choices>
</View>
<View>
  <Header value="Provide your response:"/>  
  <TextArea name="response" toName="text"/>
</View>

```

<!-- md nested-classification.md -->

## Related tags

- [Audio](/tags/audio.html)
- [Paragraphs](/tags/paragraphs.html)
- [Choices](/tags/choices.html)
- [TextArea](/tags/textarea.html)

## Related templates

- [Audio Classification](audio_classification.html)
- [Audio Classification with Segments](audio_regions.html)