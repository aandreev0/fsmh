# Designing microscopy experiments

When considering microscopy imaging as a tool to uncover new biology or verify another experiment or test a hypothesis, the first question we always have to ask is:

*What is that you are trying to see?*

That simple question requires specificity and microscopy professionals will appreciate if you can come up with concrete details. That include:

- how small are objects that you care about?
- what is the environment for these objects: other cells, gel, water, lipids?
- what is the field of view / how sparse are these objects?
- are they moving and if so, how fast, or more specifically what amount of movement you care about and what can be ignored
- how are the objects labeled / how can we tell them from other objects (shape? fluorescent marker? intrinsic reflectance?)
- do you need to use sample after the imaging is done?

For each specific type of experiment we might ask more questions. For example for optogenetics and calcium imaging experiments we have come up with example questions [here](https://focalplane.biologists.com/2021/04/12/a-biologists-checklist-for-calcium-imaging-and-optogenetic-analysis/)

## What are you trying to see?



## Picking the right technique

Usually, we see biologists approaching engineers with specific problem, often trying to use existing imaging system. In that case it is very efficient to provide information mentioned about (*What are you trying to see?*) and also supply examples of imaging or analysis performed by someone else in published literature that most closely parallels your vision. In other words: show don't tell to the engineer what you want to achieve. Keep in mind the [Pyramid of tradeoffs](https://www.nature.com/articles/s42003-023-04857-4):

## Considering limitation and pyramid of trade-offs

```{image} ../../static/pyramid-of-tradeoffs.png
:alt: pyramid of tradeoff
:width: 400px
:align: center
```

(From [The rise of data-driven microscopy powered by machine learning](https://onlinelibrary.wiley.com/doi/10.1111/jmi.13282))

Pyramid of tradeoffs in microscopy is a visual tool that helps users and engineers to understand limitations of specific system or feasibility of a specific experiment. "Cheap-Fast-Good: pick any two" rule teaches us that we can't have it all. Same in microscopy, we can't achieve high resolution long-term imaging with large field of view *in vivo*. Unless you are willing to put significant constraints of each of these adjectives, the specific system doesn't exist, but we can   find something as suitable as possible within the pyramid if you specify margins (how fast? how large is good enough? can we fix the sample? and so on).
