---
title: "Interesting (aka 'gonna check it out later') Repositories"
topic: interesting
update: 2019-07-16 12:00:00 +0200
collection: notes
date: 2019-07-16 12:00:00 +0200
permalink: /notes/repositories
---

A collection of interesting repositories and short descriptions.
Most repositories were either recommended by friends/acquiantances or posted on the [ML subreddit](www.reddit.com/r/MachineLearning).
I did not try all repositories listed below, many repositories are the usual <i>"I will check this out later"</i> ;).

## Experimental control

| Name     | Description | Aim | Further Info | Examples |
| -------- | ----------- | --- | ------------ | -------- |
| SacredML |             |     |              |          |

## Model sharing:

| Name                                      | Description                                                                   | Aim                                                        | Further Info                             | Examples                                                                                     |
| ----------------------------------------- | ----------------------------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------- | -------------------------------------------------------------------------------------------- |
| [Gradio](https://gradio.app)              | Library from Stanford aiming to easily share models.                          | Share model with non-coders, offer drag and drop interface | Hosting: [GradioHub](https://gradio.app) | [1](https://gradio.app/model?id=26) and [2](https://gradio.app/model?id=31), [code](#gradio) |
| [Bentoml](www.github.com/bentoml/bentoml) | Similar to Gradio but aiming at production: (could e.g. be backend of gradio) |
| [openml](https://www.openml.org/)         |                                                                               |                                                            |                                          |                                                                                              |
|                                           |                                                                               |                                                            |                                          |                                                                                              |

## (Re-) Implementations (usually of some paper)

| Name | Description | Aim | Further Info | Examples |
| ---- | ----------- | --- | ------------ | -------- |
|      |             |     |              |          |

## Code examples

### <a name="gradio"></a> Gradio

```python
import gradio, tensorflow as tf
image_mdl = tf.keras.models.Sequential()
# ...define and train model
io = gradio.Interface(inputs="imageupload", outputs="label", model_type="keras", model=image_mdl)
io.launch()
```
