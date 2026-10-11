# llama.cpp

llama.cpp is an open-source engine for running large language models (LLMs) efficiently on everyday hardware, from laptops to HPC clusters. It is written in C/C++, runs on both CPUs and GPUs, and is one of the most widely used tools for local AI inference. We will be using release **v0.6.0**.

Running an LLM means pushing billions of model weights through the processor for every token it generates. That makes performance mostly a question of memory bandwidth, how threads and memory are placed across your cores and sockets, and how well your nodes work together.

### What is quantization?

Model weights are normally stored as 16-bit numbers. Quantization stores them at lower precision (e.g. 4-bit) so the model takes up less memory and moves through the processor faster. The trade-off is quality: push it too far and the model gets worse. llama.cpp uses quantized models in the GGUF file format.

Note: the llama.cpp source code may **not** be modified. Build options and runtime flags are all fair game.

Links:
- Official GitHub repository: https://github.com/ggml-org/llama.cpp
- v0.6.0 release: https://github.com/ggml-org/llama.cpp/releases/tag/v0.6.0
- Build guide: https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md
- GGUF models: https://huggingface.co/models?library=gguf

# llama.cpp Challenge

### Getting started:
Set up a Linux environment, a C/C++ compiler and CMake. Build v0.6.0, download a small GGUF model (e.g. `Llama-3.2-1B-Instruct-Q4_K_M.gguf`) and try out `llama-bench`, `llama-batched-bench` and `llama-perplexity`. Run any tool with `--help` to see its flags. Full details of the challenge will be released in due time.
