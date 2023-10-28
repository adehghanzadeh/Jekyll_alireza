---
layout: post
title: My Master Thesis
date: 2023-07-25
description: My Master degree thesis in University of Tehran
tags:
  - Thesis
  - Machine Learning
  - Electrical Capacitance Tomography
categories: education
giscus_comments: true
toc:
  sidebar: right
featured: false
related_posts: false
datatable: true
#redirect: /assets/pdf/example_pdf.pdf
---

Hi there


Several days ago, I decided to create a new post here on my website to write share my thesis advancement.


First, I would like to share some terms of thoughts that going around in my mind.


If you would like to read the main section → [#Thesis](#Thesis)


## My Background


In Iran, there is entrance named Konkour ([Persian](https://en.wikipedia.org/wiki/Persian_language): کنکور; from the [French](https://en.wikipedia.org/wiki/French_language) [_Concours_](https://en.wiktionary.org/wiki/concours#Noun)) ([**read from wikipedia**](https://en.wikipedia.org/wiki/Iranian_University_Entrance_Exam)). I was studying in a public school (as named in wikipedia) and got accepted to enter University of Tabriz in 2016.


I’m that type of guys which focus on subjects that I like, so because of that, I studied only some specific courses during high school very well, so I couldn’t get a great score. (in Konkour, we have to study lots of courses. for example: Persian literature, Islamic education, Arabic and English in general section and Mathematics, Physics and Chemistry in specialized section) so, I liked math and physics in high school and I studied them very well, so the lack of other courses, lowered my scores


## Bachelor


In university, it took time for me to get comfortable with new situation (I lived in Meymeh, a small town a hundred kilometers away from Esfahan).


In forth semester, [Dr. Hossein Behfar](https://www.researchgate.net/profile/Hossein-Behfar) invited interested students to go further in Electronics and have one/two groups and work constantly under his supervises. That was my first step in applied electronics and fundamental of my future projects.


In sixth semester, our electronic groups broke up and I was looking for ways to earn back my interactions with projects and team works. Short while after, I met [Dr. Hossein Navid](https://www.researchgate.net/profile/Hossein-Navid) who help me to find my way and introduced me to [Precision Agriculture group](http://infoag.ir/en/). I worked on two project under name of this group. meanwhile, I was working on a class project for course “Mechanical Engineering Design” with four great students from our class.


You can check [project section for more details](https://alerezaa.ir/projects/).


Maybe one day, I’ll write a brief post about my bachelor degree but for now It time to write about Master degree.


## Master


My Master degree journey started in 2020, several month after Corona Virus lockdown, just after I finished my bachelor. First two semesters were lecture based, and due to lockdown, I had no interaction with university environment.


Finally, we could stay in dormitories with cautions and I got in touch with academic environment. I met my supervisor (who I talked to him before, during lockdown) and he told me about several topics which were not my mindset.


Clearance: in Iran, supervisor professor has more power that anywhere else in the world when it comes to leading subjects and topics, so students in Iran must have approval from supervisor (for any thing) even if they have a great project to work on, they can not work on that till supervisor approve. This system has lots of disadvantages, while the only way to get into university is Konkour (bachelor, master and PhD), so supervisor can get things in hand and put pressure on students as much as they can so students do what they want (no matter students like fields or not)


My professor had a project which was not even close to my background or field of interest, so I had to convince them to integrate my field of interests with his field of study, and after lots of sessions, the result was my master thesis:


## Thesis


_**Developing a machine learning algorithm to enhance image reconstruction in Electrical Capacitance Tomography (case study: bulk solid flow measurement)**_


I had a mixture feeling at first days but a little after, I end up with this idea: “I’m working on Machine Learning subject, professor said he will help me with ECT fundamentals (cause it takes lots of month to learn) and I have little interaction with ECT part”


So, I started to expand my knowledge about Machine Learning. We had a course which taught by Prof. Mahmoud Omid, I really enjoyed that lecture.


I knew about ML and I had some small information about it, but, by taking that course, I got familiar with machine learning concepts and worked practically on it. It was a set small, in-class homeworks, but useful for acquiring knowledge.


Due to coronavirus lock down, I couldn't get into university (dormitory) till start of 4th semester and soon after, I submited my proposal because I had to submit it, but the fact is, due to some problem with the instrument which I use its data, I had to wait a little bit.


It was a good rime to expand my knowledge about ML, Python programming and Cybersecurity.


I requested for financial aid of Coursera on Machine Learning course by Andrew Ng, and thankfully, I could get it. (Certification in my [CV](https://cv.alerezaa.ir/))


First, in March 31th, my supervisor sent a database of data. 56 set of data. I started working on that. I use `scikit-learn` to work on data. `LogisticRegression` , `LogisticRegressionCV` , `SVM` and `k-nearest neighbot` models are used to train a model for enhancement, but, as I expected, they did not work properly because numbers are not seperatable linearly or based on any classical ML model.


There are two pair of data:

- Simulator ↔ LBP (Linear Back Projection)
- Simulator ↔ TekhonoV

These two reconstruction methods are among fastest with lower computational cost.


### Classic Machine Learning models


NOTE: I include only some key sections in my writing.


#### Logistic Regression


Its the simplest model any starter can involve with.


No regularization, No tweak.


```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import cross_validate

scoring_method = ['neg_root_mean_squared_error', 'r2']
model = LogisticRegression()
lr_noparam_cv_result = cross_validate(model, 
                        X, y,
                        scoring=scoring_method ,
                        cv=10, return_estimator=True)
```


result was:


```text
For LBP:
'test_neg_root_mean_squared_error': array([-0.42988679, -0.43964373, -0.38889035, -0.40696627, -0.37984266,
        -0.37347476, -0.40294122, -0.40522419, -0.3484282 , -0.22566016]),
 'test_r2': array([-0.2081578 , -0.26362213,  0.01128803, -0.08276019,  0.05560606,
         0.08700535, -0.0627451 , -0.0732062 ,  0.20655092,  0.66718549])}

For Tkh:
'test_neg_root_mean_squared_error': array([-0.4520538 , -0.45853519, -0.40378146, -0.40877501, -0.36396748,
        -0.35937625, -0.39038254, -0.39414535, -0.34523643, -0.26961774]),
 'test_r2': array([-0.33596691, -0.37455079, -0.06587974, -0.09240616,  0.13289661,
         0.15463458,  0.00246881, -0.01532541,  0.22102112,  0.52489523])}
```


> In `Scikit-learn` negative $R^2$ is possible because as they mentioned “because the model can be arbitrarily worse”
{: .prompt-info }


results in a Whisker-Box chart:


![](https://prod-files-secure.s3.us-west-2.amazonaws.com/7d351b26-b47a-4bbb-a79f-df12e4cb1aad/b93a340e-f847-4100-a2be-3006601d461c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20231028%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20231028T134700Z&X-Amz-Expires=3600&X-Amz-Signature=57d51484e182a471327c746dade4acf54b6ebe8110851822e5bcf864437eff98&X-Amz-SignedHeaders=host&x-id=GetObject)


with `LogisticRegressionCV` function results were looks like this


![](https://prod-files-secure.s3.us-west-2.amazonaws.com/7d351b26-b47a-4bbb-a79f-df12e4cb1aad/1d92f057-2d7f-4828-b53e-add1c223c5e0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20231028%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20231028T134700Z&X-Amz-Expires=3600&X-Amz-Signature=4e5a291f5b0f9cdc3a2ea936915b06a319bd3c706700af9774af1153f7e7f08b&X-Amz-SignedHeaders=host&x-id=GetObject)


#### K-Nearest-Neighbor


After tunning model, results acquired as below:


![](https://prod-files-secure.s3.us-west-2.amazonaws.com/7d351b26-b47a-4bbb-a79f-df12e4cb1aad/c787c505-ceca-4542-b681-764356d91668/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20231028%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20231028T134700Z&X-Amz-Expires=3600&X-Amz-Signature=da07710bbd6c67b5598ec3674a169561ae191b9045cbd5f23f6696ad810c85b2&X-Amz-SignedHeaders=host&x-id=GetObject)


#### Histogram Gradient Boosting


In this scenario, model tuning was not so effective and final results was as below chart:


![](https://prod-files-secure.s3.us-west-2.amazonaws.com/7d351b26-b47a-4bbb-a79f-df12e4cb1aad/de725fc7-8954-4600-8951-6841d382b4b1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20231028%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20231028T134700Z&X-Amz-Expires=3600&X-Amz-Signature=875f2224ef1bead95ba40ecaaaf5dffc0345c995cb1049961749dc214d86e081&X-Amz-SignedHeaders=host&x-id=GetObject)


#### Conclusion on above models


These models have a large range of $R^2$ and based other tests, they showed very different results, by that I can conclude that generalization is not enough.


### Multilayer Perceptron


In this case, after testing different scenarios, I realized that different combination of “number of neurons in each layer” lead to different error results. so I tested different combinations based on a repeat rule.


#### 2 layers


![](https://prod-files-secure.s3.us-west-2.amazonaws.com/7d351b26-b47a-4bbb-a79f-df12e4cb1aad/4e53e63c-bc47-410c-b8cf-2b9f375aebe2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20231028%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20231028T134700Z&X-Amz-Expires=3600&X-Amz-Signature=c93e3296e85d542200915b6f8274301022de3c044b48a7ed818bb19c3703fd62&X-Amz-SignedHeaders=host&x-id=GetObject)


Vertical column: layers and neurons (number on neurons in each layer)


Horizontal columns: $R^2$ results


results are good, and generalization is much better than previous models.


#### 3 layers


In three layers, same method repeated. Results were better and generalization was better, too.


#### 4 layers


In four layer, improvement was good but it was not very noticeable.


#### 5 and 6 and 7 layers


It was more than required but I test it and result did not changed significantly.


After that, I talked to my supervisor and they said, they will send a simulator which matches the real instrument.


An image of mentioned software.


![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f6d26606-cce0-49eb-8430-a174eb4de3f8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20231028%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20231028T134700Z&X-Amz-Expires=3600&X-Amz-Signature=4b837949479c20da343e41791fc05cc9f2ff39ae034fd74c6936c7ee79b4e12f&X-Amz-SignedHeaders=host&x-id=GetObject)


(not related to me, but) this software is written in `C#` (why? because my supervisor had decided to use  for development), I did not even see its code (or any code from my supervisor)


## My thesis done, I defensed


Due to some problem, I had to defense sooner than I expected, its okay but I must change my plan and work on CNN out of thesis scope, so I decided to do it and write my scientific paper based on that.


### Get ready for CNN


… will be continued


