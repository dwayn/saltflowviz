# saltstatevis
Just a simple python script to generate graphs of salt state requisites.

## Installation Requirements
You will need to install `graphviz` to render the dot files into images. Apt, Yum and Homebrew should all have versions that will work.


## Usage
This script processes the json output from `salt-call state.show_sls MYSTATE --out json` and it will output graphviz dot language that you can then process through `dot` into an image, svg, or any other format that graphviz supports

### Processing a json file
```
saltstatevis show_sls_file.json > show_sls_file.dot
# generate a png image of the graph
dot -Tpng show_sls_file.dot -o show_sls_file.png
```

### One liner salt to svg file
SVG files are handy because you can open them natively in Chrome and they are rendered with actual text fields, allowing you to search for text in the page
```
salt-call state.show_sls some-salt-state --out json | saltstateviz | dot -Tsvg -o some-salt-stat.svg
```