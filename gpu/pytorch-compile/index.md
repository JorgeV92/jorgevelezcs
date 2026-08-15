---
layout: gpu-topic
title: PyTorch and torch.compile
subtitle: From eager Python to optimized GPU kernels
roadmap: PyTorch compiler track &mdash; ongoing alongside PMPP Parts II&ndash;IV
updated: August 15, 2026
---

<h3 id="goals">Learning goals</h3>

<p>
This page will document how PyTorch represents and executes machine-learning programs,
and how <code>torch.compile</code> transforms those programs into optimized code. My goal
is to connect the high-level model code I write in Python to the graphs, compiler passes,
and GPU kernels that execute it.
</p>

<ul>
  <li>Understand eager execution, tensors, autograd, modules, operators, and dispatch.</li>
  <li>Trace the compilation path through TorchDynamo, FX, AOTAutograd, and TorchInductor.</li>
  <li>Inspect the generated graphs and Triton or C++ kernels.</li>
  <li>Recognize graph breaks, guards, recompilations, and dynamic-shape behavior.</li>
  <li>Measure compilation overhead and steady-state training or inference performance correctly.</li>
  <li>Integrate a custom C++ or CUDA operator without breaking autograd or compilation.</li>
</ul>

<hr width="75%">

<h3 id="study-plan">Study plan</h3>

<h4>1. PyTorch execution fundamentals</h4>
<p>
I will begin with the eager execution model and follow an operation through tensors,
autograd, modules, the operator library, and device dispatch. This provides the baseline
for understanding what changes when compilation is enabled.
</p>

<h4>2. The <code>torch.compile</code> stack</h4>
<ul>
  <li><b>TorchDynamo:</b> capture Python execution into FX graphs.</li>
  <li><b>AOTAutograd:</b> capture and partition forward and backward graphs.</li>
  <li><b>TorchInductor:</b> schedule operations, fuse work, and generate optimized code.</li>
  <li><b>Triton:</b> generate and execute many of the GPU kernels emitted by Inductor.</li>
</ul>

<h4>3. The compiler programming model</h4>
<p>
I will study graph breaks, guards, cache behavior, recompilation, symbolic and dynamic
shapes, compilation modes, and the boundaries between compiled and eager execution.
</p>

<h4>4. Debugging and performance analysis</h4>
<p>
I will use compiler logs and the PyTorch profiler to inspect captured regions, generated
code, kernel launches, graph breaks, and CPU or GPU gaps. Benchmarks will separate initial
compilation cost from warm steady-state execution.
</p>

<h4>5. Extending the stack</h4>
<p>
The final stage will connect the compiler track to my CUDA work by registering and testing
a custom operator, integrating it into a compiled model, and comparing it against an eager
baseline and Inductor-generated kernels.
</p>

<hr width="75%">

<h3 id="experiments">Experiments</h3>

<ul>
  <li><b class="dammit">First experiment:</b> compare eager and compiled execution for a small model, including warm-up, compilation time, and steady-state latency.</li>
  <li>Introduce a graph break deliberately, locate it with compiler logs, and rewrite the code to remove it.</li>
  <li>Inspect an FX graph and the corresponding Inductor-generated Triton kernel.</li>
  <li>Test changing input shapes and explain when guards cause recompilation.</li>
  <li>Register a custom C++ or CUDA operator and verify correctness with eager execution, autograd, and <code>torch.compile</code>.</li>
</ul>

<hr width="75%">

<h3 id="notes">Notes and results</h3>

<p><i>Notes, profiler traces, generated code, benchmarks, and conclusions will be added here as I complete each experiment.</i></p>

<hr width="75%">

<h3 id="resources">Resources</h3>

<ul>
  <li><a href="https://docs.pytorch.org/tutorials/intermediate/torch_compile_tutorial">Introduction to <code>torch.compile</code></a>.</li>
  <li><a href="https://docs.pytorch.org/docs/stable/user_guide/torch_compiler/torch.compiler.html"><code>torch.compiler</code> overview and compiler-stack components</a>.</li>
  <li><a href="https://docs.pytorch.org/docs/stable/user_guide/torch_compiler/core_concepts.html"><code>torch.compile</code> core concepts and programming model</a>.</li>
  <li><a href="https://docs.pytorch.org/docs/stable/user_guide/torch_compiler/torch.compiler_troubleshooting.html"><code>torch.compile</code> troubleshooting and compiler logs</a>.</li>
  <li><a href="https://docs.pytorch.org/docs/stable/user_guide/torch_compiler/torch.compiler_profiling_torch_compile.html">Profiling <code>torch.compile</code> performance</a>.</li>
  <li><a href="https://docs.pytorch.org/tutorials/advanced/custom_ops_landing_page.html">PyTorch custom operators</a>.</li>
  <li><a href="https://github.com/gpu-mode/lectures">GPU MODE lecture materials</a>.</li>
</ul>
