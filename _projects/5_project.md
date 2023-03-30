---
layout: page
title: OMR Evaluator
description: Python Project (Image Processing)
img: assets/img/pythonlogo.png
importance: 3
category: study
---

𝐎ptical Mark Recognition (OMR) sheets are commonly used for grading purposes worldwide. This project offers a precise and cost-effective system for evaluating OMR sheets. The system accurately calculates the results and stores them in a CSV file based on the image and answers provided by the user. The user can choose to scan one sheet at a time or an entire folder as per their requirement.

OMR is a popular method for inputting data for censuses and surveys, especially for handling discrete data with limited values. In education, OMR is widely used to process objective questions in exams such as the Scholastic Aptitude Test-SAT and Graduate Record Examination-GRE. However, OMR has some limitations that restrict its applications. In the past, optical scanners were used to scan the paper as a bitmap image, and software was used to recognize the texts and images. This OCR method resulted in inaccuracies due to hit-and-miss pattern recognition when matching input images with stored bitmap images.

This system eliminates the need for heavy machinery and expensive scanners, thus saving time and cost. The proposed method involves an ordinary webcam and a computer/laptop for computation purposes.

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
