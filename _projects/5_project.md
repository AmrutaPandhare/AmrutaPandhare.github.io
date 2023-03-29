---
layout: page
title: OMR Evaluator
description: Image Processing using Python
img: assets/img/pythonlogo.png
importance: 3
category: study
---

𝐎ptical Mark Recognition (OMR) sheets have been widely used across the
globe for grading purposes. This project suggests
an accurate and cost efficient system for the
evaluation of the OMR sheet. Based on the image
and answers provided by the user the system
successfully calculates the results and stores the
result in a CSV file. The user can scan one sheet
at a time or can scan the entire folder according
to his/her needs

OMR is generally used as direct input for data of censuses and surveys and is perfect for discrete
data handling, whose values are limited set. In the field of education widely uses OMR technique
can process objective questions in exams, as Scholastic Aptitude Test-SAT, Graduate Record
Examination-GRE. However, there are a few drawbacks limiting the application of OMR
technology.
Earlier OCR used an optical scanner to scan the paper as bitmap image and the software was used
to realize the texts and the images. These OCRs matched these input images with the stored bitmap
images which resulted in inaccuracy due to its hit-and-miss pattern recognition

This system eliminate the installation of heavy machinery, and expensive scanners in return saving
time and cost. The proposed work consist of an ordinary webcam, and a computer/laptop
for computation purpose.

<!-- 
    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    --- -->
    
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gui.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The main GUI was divided into two parts, 𝗹𝗲𝗳𝘁 to evaluate one test at a time and 𝗿𝗶𝗴𝗵𝘁 to evaluate multiple tests at once.
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/helpmenuforscanningonesheet.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/helpmenuforscanninganentirefolder.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    We provided 𝗛𝗲𝗹𝗽 menus for effective user interaction.
</div>

We covered below mentioned conditions for the most accuracy.

{% raw %}
```html
1. All questions are marked
2. Few questions are left unmarked
3. Half circle is marked
4. Two options are marked
```
{% endraw %}

<!-- You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, *bled* for your project, and then... you reveal its glory in the next row of images. -->

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/whenallquestionsaremarked.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/whenfewquestionsareleftunmarked.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/whenhalfoptionismaked.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/whentwooptionsaremarked.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    1. All questions are marked 2. Few questions are left unmarked 3. Half circle is marked 4. Two options are marked.
</div>

The result gets stored in a CSV file which examiner can refer to later on. 
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/result.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<h3> Summary </h3>

1. The OMR Evaluator system can greatly benefit organizations and individuals who still rely on paper-based methods for data collection, such as surveys, feedback forms, and multiple-choice tests. Its versatility makes it particularly useful in remote areas like villages, as well as educational institutions for faculty feedback evaluation and MCQ answer-sheet evaluations.

2. By eliminating the need for manual grading of questionnaires, the OMR Evaluator system can quickly and accurately recognize the opinions of test-takers. Furthermore, the system has the potential to provide extensive statistical evaluation of the collected data, including pie-charts, bubble plots, and other relevant visual representations.

3. The OMR Evaluator project has been designed with the future needs of users in mind. As such, the system can be extended and further developed to include additional features and functionalities. Its flexibility and adaptability make it an ideal solution for organizations and individuals looking to transition from paper-based data collection methods to a more efficient and streamlined approach.
