# NLBayes Core Library

This repository contains the core C++ implementation of the NLBayes library, which provides Bayesian inference functionality. This core library is designed to be used as a submodule by language-specific packages (Python, R, etc.).

## Project Structure

- `include/`: Header files (.h)
- `src/`: Implementation files (.cpp)

## Building

This project uses CMake as its build system. To build:

```bash
mkdir build
cd build
cmake ..
make
```

## Components

The library implements several key components:

- Beta and Dirichlet distributions
- Graph-based models (Base and ORNOR variants)
- Hierarchical node system (HNode, HParentNode)
- Various node types (RVNode, SNode, TNode, XNode, YDataNode, YNoiseNode)
- Model implementations (Base and ORNOR variants)

## License

[Add appropriate license information]
