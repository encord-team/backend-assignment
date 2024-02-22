# Tetris programming challenge

## Instructions

1. Create a private github repository based on [this template](https://github.com/encord-team/backend-assignment), either on github.com or using the [Github CLI](https://cli.github.com/):

   ```
   gh repo create encord-be-assignment --clone --private --template encord-team/backend-assignment
   ```

1. Write a solution to the challenge described below in a language of your choice as long as it is reasonably common.

1. Once you are finished, compress your solution and send it by email to engineering-interviewers@encord.com.

## Problem description

You are to write a simplified Tetris engine.
The engine should model a grid that pieces enter from top and come to rest at the bottom, as if pulled down by gravity. Each piece is made up of four unit squares, and no two unit squares can occupy the same space in the grid at the same time.
The pieces are rigid, and come to rest as soon as any part of a piece contacts the bottom of the grid or any resting block. As in Tetris, whenever an entire row of the grid is filled, it disappears, and any higher rows drop into the vacated space without any change to the internal pattern of blocks in any row.

The requirements are as follows:
- Your program must process multiple lines each representing a sequence of pieces entering the grid. Each line of the input file is a comma-separated list of letters. Each entry in the list is a single letter and a single-digit integer, representing the shape and the left-most column index in which it enters the grid. For each line, your program should output the resulting height of the remaining blocks within the grid. 
- Your program will be invoked from a command line, taking its input from STDIN and writing its output to STDOUT, for example:

   ```bash
   $ ./tetris
   Q0,Q0
   4
   Q0,Q2
   2
   ```
- The letters used are Q, Z, S, T, I, L, and J. The shapes of the pieces they represent are shown in the table below:

   </td>
   </tr>
   </table>
   <table>
     <tr>
       <td>Letter</td>
       <td>Q</td>
       <td>Z</td>
       <td>S</td>
       <td>T</td>
       <td>I</td>
       <td>L</td>
       <td>J</td>
     </tr>
     <tr>
       <td>Shape</td>
       <td>
         <pre>
   ##
   ##
         </pre>
       </td>
       <td>
         <pre>
   ##
    ##
         </pre>
       </td>
       <td>
         <pre>
    ##
   ##
         </pre>
       </td>
       <td>
         <pre>
   ###
    #
         </pre>
       </td>
       <td>
         <pre>
   ####
         </pre>
       </td>
       <td>
         <pre>
   #
   #
   ##
         </pre>
       </td>
       <td>
         <pre>
    #
    #
   ##
         </pre>
       </td>
     </tr>
   </table>

The following assumptions are made:

- Your program does not need to validate its input and can assume that there will be no illegal characters. 
- The pieces will always have the orientations shown above.
- The grid of the game space is 10 units wide.
- The grid’s initial state is empty.

## Examples

### Example 1

A line in the input is `I0,I4,Q8` resulting in the following configuration:

```
  I0 │          │ I4  │          │ Q8  │          │
     │          │ ──► │          │ ──► │        ##│
     │####      │     │########  │     │##########│
     └──────────┘     └──────────┘     └──────────┘
      0123456789       0123456789       0123456789

```

The filled bottom row then disappears:

```
│          │
│          │
│        ##│
└──────────┘
 0123456789
```

Therefore, the output row for this sequence is “1”.

### Example 2

A line in the input contains `T1,Z3,I4`.

```

     │          │       │          │       │    ####  │
  T1 │          │  Z3   │   ##     │  I4   │   ##     │
     │ ###      │  ──►  │ #####    │  ──►  │ #####    │
     │  #       │       │  #       │       │  #       │
     └──────────┘       └──────────┘       └──────────┘
      0123456789         0123456789         0123456789

```

No rows are filled, so the output for this sequence is “4”.

More examples are available in file `input.txt`

## Evaluation criteria

The solution will be evaluated on the following criteria:

- **Correctness**: does the program produce the correct output
- **Clarity**: how easy it is for others to understand and work with your code
- **Extensibility**: how easy would it be to extend your program with additional functionality, e.g. additional movement, new pieces, etc.
- **Algorithmic complexity**: how does the performance of the submission scale with
  regards to its input
- **Efficiency**: how efficient is the solution. Our test suite includes test cases that might not fit entirely into memory. The solution is expected to handle multi-gigabyte inputs without running itself out of memory.
