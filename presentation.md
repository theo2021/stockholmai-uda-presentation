---
theme : "night"
transition: "slide"
highlightTheme: "monokai"
slideNumber: false
title: "Online Unsupervised Domain Adaptation"
backgroundColor: "rgb(52, 53, 48)"
autoPlayMedia: true
---

::: block
## Online Unsupervised Domain Adaptation

What is it and our research so far
::: 

---

<!-- .slide: data-background="rgb(52, 53, 48)" -->
### We have reached a state of superhuman perception

::: {.container}
:::: {.col}
![perception](perception.jpg)
::::
:::

---

<!-- .slide: data-background="rgb(52, 53, 48)" -->

### But when the unexpected happens

![Alt text](image-2.png)

---

### How do we solve this?

1. **Domain Generalization**: Building models to work across varied domains.

2. **Domain Adaptation**: Focus on the Target Domain (deployment)

---

### Domain Generalization is Scale

![Alt text](image-3.png)

---

### Problems

1. Costly
2. Is it even posible?
3. Performance vs Complexity


---

### Unsupervised Domain Adaptation (UDA)

<span style="color: #EED971">**Perform well only in the Domain that matters!**</span> {.fragment .fade-in-then-out}

<span style="color: #EED971">**Unsupervised: No labels**</span> {.fragment .fade-in}


---

### The two Eras

* <span style="color: blue">Old</span> Find the common information between labeled (Source) and deployment (Target) Domain

* <span style="color: red">Now</span> Train on the Target reguralized on Source


---

### GTA &rarr; CityScapes

::: container
:::: column
![Alt text](gtatocity.png)
::::
:::: column
<div style="height:300px; width:400px">
<canvas class="stretch" data-chart="bar" width="400" height="300">
<!--
{ "options": {
        "scales": {
            "y": {
                "beginAtZero": true,
                "title": {
                    "display": true,
                    "text": "mIoU"
                }
            }
        }
    }
}
-->
,GTA &rarr; CityScapes
CyCADA (2018), 39.5
ILM-ASSL (2023), 76.1
Oracle (Segformer), 82.4
</canvas>
</div>
::::
:::

---

### History of UDA


![Alt text](ganin.png)

Create a domain agnostic feature representation {style="color: #EED971"}

Domain-Adversarial Training of Neural Networks, Ganin et al 2016. {style="font-size:30px"}

---

### Improvements


* Per class discriminators (Chen et al)
* Move the discriminator to the prediction
* Use multiple discriminators (Tsai et al)
* Use the entropy of the prediction instead (Advent)

---

### New SoTAs: DaFormer

<div class="r-stack">

![Daformer](daformer.png) {style="width: 80%"}

</div>

Self-Train on target:

* Avoid Collapse through Source Loss
* Avoid Overfitting to Source with Dist loss

---

### DACS: An easy trick that works

![DACS](dacs.png)

Take objects from the Source Image and put them into the target sample. Train using those ground truths.

---

### Online UDA

<span style="color: #EED971">Can we adapt to new domains as they appear? </span>

Why?

<span style="color: #EED971">Environment changes **unpredictably**, do we have it in our dataset? </span> {.fragment .fade-in}


---

### Online UDA experiment

* Synthetic rain
* Move steadily from low to high rain

![Alt text](image-5.png)

---

<!-- .slide: data-background="rgb(0, 0, 0)" -->
### 🌊  Onda - ECCV22

<video loop muted autoplay controls>
  <source src="200m_demo.mp4" type="video/mp4">
</video>

---

### Challenges

* Catastrophic forgetting
* Speed of Adapting
* Self-Training confidence not calibrated

---

<!-- .slide: style="text-align: left;" -->
# <span style='color: green'>THE END</span> 

Whats next? 

How can we make it real-time?
