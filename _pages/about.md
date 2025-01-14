---
layout: about
title: About
permalink: /
subtitle: A Benchmark for Matrix Reordering
description: "Matrix reordering permutes the rows and columns of a matrix to reveal meaningful visual patterns, such as blocks that represent clusters. A comprehensive collection of matrices, along with a scoring method for measuring the quality of visual patterns in these matrices, contributes to building a benchmark. This benchmark is essential for selecting or designing suitable reordering algorithms for revealing specific patterns. In this paper, we build a matrix-reordering benchmark, ReorderBench, with the goal of evaluating and improving matrix-reordering techniques. This is achieved by generating a large set of representative and diverse matrices and scoring these matrices with a convolution- and entropy-based method. Our benchmark contains 2,835,000 binary matrices and 5,670,000 continuous matrices, each generated to exhibit one of four visual patterns: block, off-diagonal block, star, or band, along with 450 real-world matrices featuring hybrid visual patterns. We demonstrate the usefulness of ReorderBench through three main applications in matrix reordering: 1) evaluating different reordering algorithms, 2) creating a unified scoring model to measure the visual patterns in any matrix, and 3) developing a deep learning model for matrix reordering."
# pretty_table: true
# profile:
#   align: right
#   image: prof_pic.jpg
#   image_circular: false # crops the image to make it circular
#   more_info: >
 
# news: false # includes a list of news items
# selected_papers: false # includes a list of papers marked as "selected={true}"
# social: false # includes social icons at the bottom of the page
---
<br />

<h4><span class="font-weight-bold">What is ReorderBench?</span></h4>

ReorderBench is a large-scale matrix benchmark built for matrix reordering. ReorderBench has the following features:

- [x] Visual pattern recognition
- [x] 2,835,000 binary matrices and 5,670,000 continuous matrices
- [x] 450 real-world matrices featuring hybrid visual patterns
- [x] 4 visual patterns: block, off-diagonal block, star, and band
- [x] 4 matrix sizes: 100x100, 200x200, 300x300, and 400x400
- [x] Scores to measure the quality of visual patterns

<br />

<h4><span class="font-weight-bold">Benchmark</span></h4>

We provide the ReorderBench test set with 1,701,000 matrices at [Hugging Face](https://huggingface.co/datasets/reorderbench/ReorderBench). 
Click <a href="http://166.111.80.25:5173">HERE</a> to explore more examples.

<div class="row justify-content-sm-center">
    <a href="http://166.111.80.25:5173">
        <div class="col-sm-12 mt-4 mt-md-0">
            {% include figure.liquid 
                path="assets/img/matrix_navigator.png" 
                class="img-fluid rounded z-depth-1" 
                zoomable=false
                caption="Click to explore the ReorderBench test set." 
            %}
        </div>
    </a>
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm mt-4 mt-md-0">
        {% include figure.liquid path="assets/img/examples_full.png" class="img-fluid rounded z-depth-1" zoomable=false %}
    </div>
</div>
<div class="caption">
    Examples of matrices in ReorderBench. 
</div>

<br />

<h4><span class="font-weight-bold">Benchmark generation pipiline</span></h4>

To ensure the representativeness and diversity of the ReorderBench, we first generate a set of representative matrix templates for each visual pattern. Then, based on these matrix templates, a large number of matrix variations with diverse degrees of degeneration are generated. The diversity is achieved by combining different variation methods, including index swapping and two types of typical anti-patterns: noise anti-patterns and noise-cluster anti-patterns. To accurately evaluate the quality of visual patterns in a matrix, we develop a scoring method by combining the matching capability of convolutional kernels and the disorder detection capability of entropy.

The code for generating the dataset is available at [Github](https://github.com/reorderbench/reorderbench_code/tree/main/generator).

<div class="row justify-content-sm-center">
    <div class="col-sm mt-4 mt-md-0">
        {% include figure.liquid path="assets/img/system_pipeline.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    The generation pipeline for the ReorderBench benchmark.
</div>


<br />

<h4><span class="font-weight-bold">Unified scoring model</span></h4>

We build a unified scoring model based on the ReorderBench. This model aligns with the convolution- and entropy-based scoring method across all four visual patterns in both binary and continuous matrices and can also measure matrices of varying sizes. 

The unified scoring model is available at [Hugging Face](https://huggingface.co/reorderbench/unified_scoring_model). The related code is available at [Github](https://github.com/reorderbench/reorderbench_code/tree/main/unified_scoring_model).

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-4 mt-md-0">
        {% include figure.liquid 
            path="assets/img/scoring_model.png" 
            class="img-fluid rounded z-depth-1" 
            zoomable=false 
        %}
    </div>
</div>
<figcaption class="caption">
    Scores generated by our unified scoring model, which measure the quality of block, off-diagonal block, star, and band patterns, respectively. The matrices are from 
    <a href="http://vlado.fmf.uni-lj.si/pub/networks/data/">
        the Pajek graph
    </a> 
    and 
    <a href="https://networkrepository.com/">
        the Network Repository
    </a>
    .
</figcaption>

<div class="row justify-content-sm-center">
    <div class="col-sm-11 mt-4 mt-md-0">
        {% include figure.liquid 
            path="assets/img/scoring_model_compare.png" 
            class="img-fluid rounded z-depth-0" 
            zoomable=false 
        %}
    </div>
</div>
<figcaption class="caption">
    The performance of deep neural networks as the unified scoring model. The best performance under each measure is  <span style="font-weight: 900;">bold</span>.
</figcaption>

<br />

<h4><span class="font-weight-bold">Deep reordering model</span></h4>

The extensive and diverse matrices in ReorderBench offer valuable supervision for training a deep reordering model. By treating the matrices with index swaps as negative samples and their ground-truth matrices as positive samples, we build a deep model for matrix reordering.

The models are available at [Hugging Face](https://huggingface.co/reorderbench/reordering_model). The related code is available at [Github](https://github.com/reorderbench/reorderbench_code/tree/main/reordering_model).

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-4 mt-md-0">
        {% include figure.liquid 
            path="assets/img/deep_reorder.png" 
            class="img-fluid rounded z-depth-1" 
            zoomable=false 
        %}
    </div>
</div>
<figcaption class="caption">
    The architecture of our deep reordering model.
</figcaption>

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-4 mt-md-0">
        {% include figure.liquid 
            path="assets/img/reorder.png" 
            class="img-fluid rounded z-depth-0" 
            zoomable=false 
        %}
    </div>
</div>
<figcaption class="caption">
    Evaluation results of existing matrix reordering algorithms and our matrix reordering model. The best one is <span style="font-weight: 900;">bold</span>, and the runner-up is <u>underlined</u>.
</figcaption>

<br />






