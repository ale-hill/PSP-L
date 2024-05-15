[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

# Project Scheduling with Autonomous Learning Opportunities Experiments

This archive is distributed in association with the [INFORMS Journal on
Computing](https://pubsonline.informs.org/journal/ijoc) under the [MIT License](LICENSE).

The software and data in this repository were used in the research reported on in the paper 
[This is a Template](https://doi.org/10.1287/ijoc.2023.0107) by A. Hill and T. V. M. Vossen.

## Cite

To cite the contents of this repository, please cite both the paper and this repo, using their respective DOIs.

https://doi.org/10.1287/ijoc.2023.0107

https://doi.org/10.1287/ijoc.2023.0107.cd

Below is the BibTex for citing this snapshot of the respoitory.

```
@misc{PSPLdata,
  author =        {A. Hill and T. W. M. Vossen},
  publisher =     {INFORMS Journal on Computing},
  title =         {{Project Scheduling with Autonomous Learning Opportunities Experiments}},
  year =          {2024},
  doi =           {10.1287/ijoc.2023.0107},
  url =           {https://github.com/INFORMSJoC/2023.0107},
  note =          {Available for download at https://github.com/INFORMSJoC/2023.0107},
}  
```

## Description

This repository contains the problem and solution data used for the experiments in the paper. Moreover, the algorithm MAPLE script is included.

## Problem Data Format

The problem instance files follow the following format. 

1) The single-learning case (PSP-SL)

(Note that the instance files contain resource information which is not used in our models.)

% (NbTasks) = (number of project jobs);
NbTasks = 32;

% (Tasks) = {<(job),(original duration),(Unused resource demands),{(successor1, sucessor2, ...),[(teacher job,reduced duration)]}>, ...};
% Note that teacher and alternative duration are set to zero if not a learning candidate.
Tasks = {
// < Task ID, Duration, [Resource Demands], {Successor(s) (optional)}, [Teacher, Alternate Duration] >
  < 1, 0, [0, 0, 0, 0], {2, 3, 4}, [0, 0] >,
  < 2, 3, [9, 0, 9, 0], {17, 25, 29}, [22, 2] >,
  < 3, 5, [0, 10, 3, 0], {9, 10, 16}, [0, 0] >,
  < 4, 9, [6, 2, 2, 0], {5, 6, 7}, [2, 8] >,
  < 5, 10, [0, 0, 10, 1], {17}, [0, 0] >,
  < 6, 1, [10, 1, 2, 0], {13, 16, 22}, [0, 0] >,
  ...
  
2) The multi-learning case (PSP-ML)

% (n) (number of jobs)
n 122
% (job) (duration) (reduced duration when learning)
j d dAlt
1 0 0
2 8 4
3 5 5
4 8 8
5 1 1
6 8 4
7 2 1
...

% (mA) (number of precendence arcs)
mA 183
% (arc tail job) (arc head job)
1 2
1 3
1 4
2 5
...

% (mL) (number of base learning opportunities)
mL 30
% (arc tail job) (arc head job)
2 44
5 31
10 101
17 36
...

% Multi-learning data
LL
% (L) (base learning opportunity; from above) (number of learning scenarios)
L 2 1
% (t) (number of teachers in this scenario) (teacher1) [(teacher2) ...]
 t 1 79
% (d) (learner duration in this scenario)
 d 4
L 6 1
 t 1 31
 d 4
 ...

## Solution Data Format

The solution (project schedule) format (both instance types) is as follows.
% (job),(start time),(end time)
1,0,0
2,0,6
3,0,5
4,0,9
5,9,10
6,10,13
7,6,13
8,10,13
9,6,9
10,13,20
...
