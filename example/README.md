# A simple two-node architecture

File `qpa.zls` contains ZSy source code of a simple two-node
architecture where each node is triggered by its own jittery clock.

```
let hybrid clock(t_min, t_max) = c where
  rec timer t init 0 reset c() -> 0
  and emit c when { t >= t_min }
  and always { t <= t_max }

let hybrid scheduler(t_min, t_max) = c1, c2 where
  rec c1 = clock(t_min, t_max)
  and c2 = clock(t_min, t_max)
```

To compile and run the symbolic simulation, type the following
command:

```
make
./qpa.byte
```

This will launch an OCaml graphics window.

To start the simulation, focus on the terminal again an press enter.

At each step, the graphics window shows a visualization of the current
zone. The active guards are listed in the terminal.

To execute an action type its name on the terminal and press enter:
- `wait` for the wait transition
- `c1` to emit signal c1
- `c2` to emit signal c2
- `c1c2` to emit signals c1 and c2 simultaneously
