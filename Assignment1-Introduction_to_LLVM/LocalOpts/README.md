if i try to `make` with the FunctionInfo/tests

result:

```
env LD_LIBRARY_PATH=. opt-6.0 -load LocalOpts.so -algebraic-identity -strength-reduction -multi-inst-opt tests/loop-m2r.bc -o tests/loop-opt.bc
opt-6.0: Unknown command line argument '-algebraic-identity'.  Try: 'opt-6.0 -help'
opt-6.0: Did you mean '-guard-widening'?
opt-6.0: Unknown command line argument '-strength-reduction'.  Try: 'opt-6.0 -help'
opt-6.0: Did you mean '-expand-reductions'?
opt-6.0: Unknown command line argument '-multi-inst-opt'.  Try: 'opt-6.0 -help'
opt-6.0: Did you mean '-jump-inst-cost'?
Makefile:25: recipe for target 'tests/loop-opt.bc' failed
make: *** [tests/loop-opt.bc] Error 1
rm tests/loop-m2r.bc
```

Dont know what to do QAQ

