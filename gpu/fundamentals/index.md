---
layout: gpu-topic
title: Heterogeneous Parallel Computing
subtitle: Why GPUs trade latency for throughput
roadmap: Part I &mdash; Fundamental concepts, PMPP Chapters 1&ndash;3
updated: August 15, 2026
---

<h3 id="goals">Learning goals</h3>

<p>
This page will document my introduction to heterogeneous parallel computing and the
CUDA programming model. I want to understand the ideas well enough to explain not only
how to launch a kernel, but why a GPU executes the work differently from a CPU.
</p>

<ul>
  <li>Explain the roles of the host and device in a heterogeneous program.</li>
  <li>Distinguish latency-oriented CPU execution from throughput-oriented GPU execution.</li>
  <li>Describe data parallelism and identify problems that map well to a GPU.</li>
  <li>Understand CUDA threads, blocks, grids, kernel launches, and device memory.</li>
  <li>Implement and test vector addition as a first CUDA kernel.</li>
</ul>

<hr width="75%">

<h3 id="notes">Notes</h3>

<p>
My notes will go here as I work through the reading and lectures. I will use this
section for explanations, diagrams, code excerpts, and questions that need more study.
</p>

<h4>Heterogeneous computing</h4>
<p><i>Notes to come.</i></p>

<h4>Data parallelism</h4>
<p><i>Notes to come.</i></p>

<h4>The CUDA programming model</h4>
<p><i>Notes to come.</i></p>

<hr width="75%">

<h3 id="experiments">Experiments</h3>

<p>
For each experiment I will record the hardware and software environment, the question
being tested, the implementation, correctness checks, measurements, and takeaways.
</p>

<ul>
  <li><b class="dammit">First experiment:</b> CPU and CUDA implementations of vector addition.</li>
  <li><b>Follow-up:</b> map a two-dimensional data set onto a CUDA grid.</li>
</ul>

<hr width="75%">

<h3 id="takeaways">Takeaways and open questions</h3>

<p><i>This section will be updated after completing the reading and experiments.</i></p>

<hr width="75%">

<h3 id="resources">Resources</h3>

<ul>
  <li>
    <a href="https://www.oreilly.com/library/view/programming-massively-parallel/9780323984638/">
      <i>Programming Massively Parallel Processors</i>, Fourth Edition
    </a>, Chapters 1&ndash;3.
  </li>
  <li>
    <a href="https://github.com/gpu-mode/lectures/tree/main/lecture_002">
      GPU MODE Lecture 2: PMPP Chapters 1&ndash;3 recap
    </a>.
  </li>
  <li>
    <a href="https://github.com/gpu-mode/lectures/tree/main/lecture_003">
      GPU MODE Lecture 3: Getting Started With CUDA
    </a>.
  </li>
</ul>
