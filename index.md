---
layout: default
---
{::options parse_block_html="true" /}
<h1 id="name-header"><a href="{{ site.url }}">{{ site.title }}</a></h1>

# Table of Contents {#toc}
<nav class="toc">
- [Contact](#contact)
- [About me](#about)
- [Software development](#software-development)
- [Writing](#writing)
- [News](#news)
- [Research](#research)
  - [Publications](#publications)
</nav>

<!--CV is at ./cv.pdf but is out of date  -->
<section id="contact-section">
# Contact {#contact}
Email
:    [krzysdrewniak@gmail.com](mailto:krzysdrewniak@gmail.com)

Work Email
:    [Krzysztof.Drewniak@amd.com](mailto:Krzysztof.Drewniak@amd.com)

Github
:    [krzysz00](https://github.com/krzysz00/)

Resume
:   [pdf](/resume.pdf)

PGP
:    [837E 880C 11FF 99D9 F0C0  9BA1 2A14 2308 2388 E924](/pubkey.asc)

Ham radio
:    KF5SOQ
</section>

# About me {#about}
I am a senior engineer working on compilers for AI at AMD.
There, I am primarily working on the [IREE project](https://github.com/iree-org/iree/) and making substantial contributions to [MLIR](https://mlir.llvm.org/) and some work on LLVM.
Before late 2024, I was a tech lead on [rocMLIR, a MLIR-based generator for high performance machine lerning kernels.](https://github.com/ROCm/rocMLIR).
See [Software development](#software-development) for more details on my work.

I'm not looking for new work right now.

Previously, I was a PhD student at the University of Washington, as detailed in [Research](#research).

In addition to my software development work, I have written several published short stories in the [Post-Self setting](https://post-self.ink/) as detailed in [Writing](#writing).

# Software development {#software-development}

My main role at AMD is working on low-level kernel optimizations and new hardware in a senior capacity (handling planning and implementation strategy)
as part of the IREE project (which is an end-to-end graph compiler for AI models).
I played a key role in RDNA4 and MI-350 support.
I also deepened my involvement in upstream MLIR and LLVM, such as by becoming a dialect maintainer for AMD-related dialects.

Previously, I grew from joining the company to late 2024, I grew from a new engineer on the rocMLIR kernel generator project to one of its tech leads.
for high-performance implementations of matrix multiplication and convolution on AMD GPUs,
primarily for use in machine learning.

My work on rocMLIR has spanned from overseeing our integration into the MIGraphX graph inference engine to substantial performance improvements to critical refactorings.
For example, I made our existing [coordinate transformations](https://mlir.llvm.org/OpenMeetings/2022-10-06-Rocm-affine.pdf) concept a first-class IR object, which allowed for powerful analyses such as the ability to determine how accesses to the memory underlying a tensor could be best vectorized.

I have made various substantial contributions to the wider MLIR and LLVM community, including:
- Maintaining the AMD-related dialects (AMDGPU and ROCDL)
- Providing ergonomic wrappers around our matrix multiplication instructions
- Adding support for `gpu.printf`
- Integer range analysis for MLIR
- The `ptr addrspace(8)` (buffer resource) and `ptr addrspace(7)` (buffer fat pointer) representations for AMD buffer resources in LLVM
- Substantially expanding how the new properties system in MLIR could be used in declarative operation specifications
- Extending GPU barrier semantics to represent fine-grained memory fencing

<section id="writing-section">
# Writing {#writing}
In addition to working in software, I have taken up science fiction writing.

My published work mainly consists of works in the [Post-Self](https://post-self.ink/) setting.

My 12,000-word short story "Sentences" is included in [*Marsh*](https://marsh.post-self.ink/), and I am the primary author of two sections of the upcoming [*Idumea*](https://idumea.post-self.ink/), namely those about The Dog and The Rabbit-Chaser.

I have written other short stories in the setting, including (but not limited to)

- ["Coffee Leak"](https://post-self.ink/stories/coffee-leak/), where we see the consequences of physics being less fixed in the System
- ["The Party"](https://post-self.ink/stories/the-party), where there is a dog at The Party that never ends
- ["Arise to Oath And Office"](https://archiveofourown.org/works/53807779), showing another angle of the inciting incident of *Marsh* (and used as promotional material)
</section>

# News {#news}
{% for post in site.posts %}
<div class="news-item">
<span class="date"> {{ post.date | date: "%Y-%m-%d" }} </span>
<span class="content"> {{ post.content | remove: "<p>" | remove: "</p>" }}</span>
</div>
{% endfor %}

# Research {#research}

I was a PhD student  at the University of Washington Paul G. Allen School of Computer Science & Engineering for three years from 2018 to 2021.
I worked in the [Programming Languages and Software Engineering](http://uwplse.org/) group, and am advised by [Rastislav Bodik](https://homes.cs.washington.edu/~bodik/). My research focus is on using program synthesis to improve the performance of numerical computations, such as matrix multiplication and convolution, that are used in machine learning and scientific computing.

I have developed a new synthesis technique for fixed-sized mathematical operators on accelerators (such as GPUs) that reduces the problem to synthesis over functional array programs and uses an abstract reachability analysis to quickly prune most incorrect partial candidates.
This has the added advantage of reducing a large amount of the computation to Boolean matrix multiplication, enabling synthesis over larger spaces of functions as compared to previous work.
In the future, this work will be integrated into a larger framework for synthesizing efficient code for machine learning models on accelerators.

{::options parse_block_html="false" /}
<section id="publictaions-section">
<h2 id="publications">Publications</h2>

Also listed at <a href="https://orcid.org/0000-0002-7054-1238">ORCID 0000-0002-7054-1238</a>.

{%- assign bibs-newest-first = site.bib | reverse -%}
{% for paper in bibs-newest-first %}
  {% include paper.html paper=paper %}
{% endfor %}
</section>
