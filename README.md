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

Notice that a balanced version of this dataset is also available, where lines are balanced across commentaries with a maximum of 40 pages and a minimum of 35 pages per commentaries. This is useful for training purposes, as it avoids biases towards commentaries with more lines. The balanced version is available in the file `GT-commentaries-lines-balanced.json`. It was generated using `ajmc.olr.line_detection.data_processing.balance_dataset` from the [ajmc](https://github.com/ajaxMultiCommentary/ajmc) package. 



