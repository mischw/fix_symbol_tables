# Results
All of the 3014 symbol tables in [windows.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip) were regenerated based on their filename, which consist of `GUID` and `Age`.
A symbol table is considered _bad_ if `base_types` or `types` are 0.
Pseudocode for building a new set of healthy symbol tables:
```python
for (old, new) in symbol_tables:
    if bad(new):
        if bad(old):
            # they are both bad, skip
        else:
            # use the old one
    else:
        # use the new one
```

From the original 3014 symbol tables:
- 82 cases where the *old* symbol table was used
- 2839 cases where the *new* symbol table was used
- 93 cases where *none* were used

This results in 2921 remaining symbols tables.

There might be cases where there are less `types`, `symbols` or `enums` in the new symbol table. This is not necessarily a bad thing and to be expected.
