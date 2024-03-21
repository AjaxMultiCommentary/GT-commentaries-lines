# GT-commentaries-lines

This dataset contains ground truth data for lines in AjMC commentaries. It is an addendum to the previously released PLA and OCR datasets, [GT4HistCommentLayout](https://github.com/AjaxMultiCommentary/GT-commentaries-layout) and [GT4HistComment](https://github.com/AjaxMultiCommentary/GT-commentaries-OCR). The dataset is released under the [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/) license.


# How-to

The dataset is released as a single [VIA 2](http://www.robots.ox.ac.uk/~vgg/software/via/) JSON file. The project can be open in VIA (`project/load`) or directly with JSON. Lines are annotated as rectangle regions, and can be very easily retrieved using: 

```python
import json

with open('GT-commentaries-lines.json') as f:
    data = json.load(f)

lines = {}
for page_id, page_dict in data['_via_img_metadata'].items():
    lines[page_id] = []
    for region in page_dict['regions']:
        lines[page_id].append(region['shape_attributes'])

# This outputs a dictionary in the form of: 
# {page_id: [line1, line2, ...], ...}
# where each line is a dictionary with the following keys:
# {'name': 'rect', 'x': x, 'y': y, 'width': w, 'height': h}
```

Notice that this dataset annotates the same images as [GT4HistCommentLayout](https://github.com/AjaxMultiCommentary/GT-commentaries-layout), so that images can be retrieved from there. This being said, copyrighted images are not included. 



