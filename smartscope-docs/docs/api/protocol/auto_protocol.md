# Automatic protocol selection

When setting up a SmartScope run, a protocol can be selected for each grid to screen. There is also an `'auto'` option. 
The behavior of this option can be managed from the `config/smartscope/default_protocols.yaml`.

At the moment, the synthax for the automated selection is quite limited and will improve over time.

First, here's how the file looks like:

```yaml
##Use this file to design rules for how to automatically set default protocol for a grid.
- conditions:
    - [holeType.name, NegativeStain]
    - [holeType.name, Lacey]
    - [holeType.name, MultiA]
  mode: any
  protocol: NegativeStain
- conditions:
    - [params_id.bis_max_distance, 0]
    - [params_id.tilt_angle, '!__0']
  mode: any
  protocol: SPA
- conditions:
    - [holeType.hole_size, '!__None']
    - [params_id.bis_max_distance, '!__0']
    - [params_id.tilt_angle, 0]
  mode: all
  protocol: SPA-Ptolemy
```


It contains a list of conditions that will yield to the selection of a given protocol.

## Synthax


Each entry in the file has 3 sections:

### conditions


A list of conditions that need to be met for a protocol to be selected.

Each condition contains a `key` and a `value`. If the condition needs to be evaluating on a false response, the valued can be prefixed with `!__`

### mode

Can have two values: `any` or `all` whether any or all conditions specified in the conditions needs to be met

### protocol

The protocol that will be used if the conditions are met.