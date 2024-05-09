Formats:

__________________________________________________
1) The single-learning case (PSP-SL)

% The instance files contain resource information which is not used in our models.

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
  
__________________________________________________
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

__________________________________________________
3) Solution format (both instance types)
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
