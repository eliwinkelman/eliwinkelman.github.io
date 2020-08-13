---
layout: page
title: Sudoku Solver
---

This sudoku solver implements Donald Knuth's dancing links algorithm to solve sudoku puzzles quickly. Dancing links is an algorithm for solving [exact cover problems](https://en.wikipedia.org/wiki/Exact_cover), which include Sudoku and the N queens problem.

The implementation averaged about 1.5 ms on 15 high difficulty (human rated) sudoku puzzles I found online.

[Github](https://github.com/eliwinkelman/Dancing-Links)

## References

Knuth, D. E. (2000). Dancing links. *ArXiv:Cs/0011047*. http://arxiv.org/abs/cs/0011047

