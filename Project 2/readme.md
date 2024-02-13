# Project 1: LLMs in the Social Sciences

### Overview
Imagine you're in a world where images paired with catchy text, known as memes, are not just for laughs but can also sway people's opinions and spread misinformation. These memes can be powerful on social media, reaching and influencing countless users with simple yet impactful messages. Some memes use sneaky tactics to persuade or mislead, such as making things seem simpler than they are, calling people names to discredit them, or using emotional appeals to bypass rational thinking.

### Technical Description
We refer to propaganda whenever information is purposefully shaped to foster a predetermined agenda. Propaganda uses psychological and rhetorical techniques to reach its purpose. Such techniques include the use of logical fallacies and appealing to the emotions of the audience. Logical fallacies are usually hard to spot since the argumentation, at first sight, might seem correct and objective. However, a careful analysis shows that the conclusion cannot be drawn from the premise without the misuse of logical rules. Another set of techniques makes use of emotional language to induce the audience to agree with the speaker only on the basis of the emotional bond that is being created, provoking the suspension of any rational analysis of the argumentation.

Memes consist of an image superimposed with text. The role of the image in a deceptive meme is either to reinforce/complement a technique in the text or to convey itself one or more persuasion techniques.



### Tasks

- Subtask 1 - Given only the “textual content” of a meme, identify which of the 20 persuasion techniques, organized in a hierarchy, it uses. If the ancestor node of a technique is selected, only a partial reward is given. This is a hierarchical multilabel classification problem. 
- Subtask 2 - Given a meme, identify which of the 22 persuasion techniques, organized in a hierarchy, are used both in the textual and in the visual content of the meme (multimodal task). If the ancestor node of a technique is selected, only a partial reward will be given. This is a hierarchical multilabel classification problem. You can find info on the hierarchy below.

Please refer to this image for better understanding of the labels
Link: https://propaganda.math.unipd.it/semeval2024task4/images/hierarchy2.jpg


### Datasets
It will be released after Feb 19th. A sample dataset structure is give for your understanding of the two tasks. 

For subtask 1 the JSON data looks as follows
```
		{
			"id": "125",
			"text": "I HATE TRUMP\n\nMOST TERRORIST DO",
			"labels": [
				"Loaded Language",
				"Name calling/Labeling"
		],
		"link": "https://..."
		},
```
where
- id is the unique identifier of the example across all three subtasks
- text is the textual content of the meme, as a single UTF-8 string. While the text is first extracted automatically from the meme, we manually post-process it to remove errors and to format it in such a way that each sentence is on a single row and blocks of text in different areas of the image are separated by a blank row. Note that task 1 is an NLP task since the image is not provided as an input.
- labels is a list of valid technique names (the full list is available in your team page after registration) used in the text. Since these are the gold labels, they will be provided for the training set only. In this case two techniques were spotted: Loaded Language and Name calling/Labeling.


For subtask 2, the JSON data looks as follows
```
		{
			"id": "125",
			"text": "I HATE TRUMP\n\nMOST TERRORIST DO",
			"labels": [
            				"Reductio ad hitlerum",
            				"Smears",
            				"Loaded Language",
            				"Name calling/Labeling"
        			],
            	"image": "125_image.png",
		"link": "https://..."
		},
```
where image is the name of the file with the image of the meme in the folder. The meaning of id, text and labels is the same as for task 1. However, the list of technique names is different (the full list is available in your team page after registration). Note that the field labels will be provided for the training set only, since it corresponds to the gold labels. Notice, however, that now we are able to see the image of the meme, hence we might be able to spot more techniques. In this example smears and Reductio ad hitlerum become evident only after we are able to understand who the two sentences are attributed to. There are other cases in which a technique is conveyed by the image only (see example with id 189 in the training set).
A submission for task 2 consists in a single json file with the same format as the input file, but where only the fields id, labels, for each example, are required.

### Evaluation Metrics:

##### Subtask 1
Subtask 1 is a hierarchical multilabel classification problem. Taking the figure above with the hierarchy as an example, any node of the DAG can be a predicted label. The gold label is always a leaf node of the DAG. If the prediction is the correct label, We use hierarchical-F1 as the official evaluation measure. 

##### Subtask 2
Subtask 2 is a hierarchical multilabel classification problem. We use hierarchical-F1 as the official evaluation measure. 

### Submission Details
It will be shared later on, according to the milestones.


### Resources
##### Read More:
- https://propaganda.math.unipd.it/semeval2024task4/
- Note: Subtask 2b has been removed from the original challenge for this course project.
