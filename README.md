# Makeflow example: Parameterized sub-workflows

Note: This is a rough proof of concept. It demonstrates how to use Makeflow configuration variables to run different sub-workflows.

This workflow can take multiple kinds of input (GeoJSON, Shapefiles, and Bety remote database servers). The first step (a sub-workflow) converts whatever input was provided to a GeoJSON file (if it isn't already). The rest of the workflow operates on GeoJSON files only. 

This assumes you have [Makeflow installed](https://cctools.readthedocs.io/en/latest/install/)

## A. Run the workflow with an existing GeoJSON file

```bash
makeflow --jx --jx-args=jx-args-geojson.json workflow.jx
```

Inspect the following files:

- output_intermediate/input.geojson
- output_intermediate/plotclip.txt
- output_final/final-results.txt

Ensure that they all contain the following as the last line:

```
{'type': 'Provided'} 
```

Clean output files:

```bash
makeflow --jx --jx-args=jx-args-geojson.json --clean workflow.jx
``` 


## B. Run the same workflow with a Shapefile as input

```bash
makeflow --jx --jx-args=jx-args-shapefile.json workflow.jx
```

Inspect the following files:

- output_intermediate/input.geojson
- output_intermediate/plotclip.txt
- output_final/final-results.txt

Ensure that they all contain the following as the last line:

```
{'type': 'Shapefile'}
```

Clean output files:

```bash
makeflow --jx --jx-args=jx-args-shapefile.json --clean workflow.jx
``` 


## C. Run the same workflow using Bety as input

```bash
makeflow --jx --jx-args=jx-args-bety.json workflow.jx
```

Inspect the following files:

- output_intermediate/input.geojson
- output_intermediate/plotclip.txt
- output_final/final-results.txt

Ensure that they all contain the following as the last line:

```
{type: Bety} https://terraref.ncsa.illinois.edu/bety/:9999999999999999999999999999999999999999
```

Clean output files:

```bash
makeflow --jx --jx-args=jx-args-bety.json --clean workflow.jx
``` 
