# delly_workflow
`run_delly.cwl` is the module for working through delly call and filter across all SV types; makes a generic samples tsv pairing file that `delly filter` needs by using the CWL `create_tn_pair.cwl`.

## Tools used in this workflow

| Tools	| Version	| CWL Location	| Other Notes	|
|--|--|--|--|
| delly	| v0.8.1	| https://github.com/mskcc-cwl/delly_v0.8.1	| Uses `create_tn_pair.cwl`* to make a pairing file needed by `delly_filter.cwl`	|

*`create_tn_pair.cwl` currently uses a lightweight `alpine:3.8` image.

The workflow in brief:

For every SV Type in ['DUP', 'BND', 'INV', 'INS', 'DEL'], do:

`delly_call.cwl` -> `create_tn_pair.cwl` -> `delly_filter.cwl`

## Example Usage of CWL

- CWL specification 1.0
- Use the example input YAML as a template.
- Example Command using [toil](https://toil.readthedocs.io):

```bash
   > toil-cwl-runner run_delly.cwl inputs.yaml
```

