
# `gradio_imageslider`
<a href="https://pypi.org/project/gradio_imageslider/" target="_blank"><img alt="PyPI - Version" src="https://img.shields.io/pypi/v/gradio_imageslider"></a>  

Python library for easily interacting with trained machine learning models

## Installation
    
```bash 
pip install gradio_imageslider
```

## Usage

```python
import gradio as gr
from gradio_imageslider import ImageSlider
from PIL import ImageFilter


def fn(im):
    print(f"fn: {im}")
    if not im or not im[0]:
        return im
    print(f"fn not none: {im}")
    return (im[0], im[0].filter(filter=ImageFilter.GaussianBlur(radius=10)))


with gr.Blocks() as demo:
    img1 = ImageSlider(upload_count=1, type="pil")
    img1.upload(fn, inputs=img1, outputs=img1)

if __name__ == "__main__":
    demo.launch()

```

## `ImageSlider`

### Initialization

<table>
<thead>
<tr>
<th align="left">name</th>
<th align="left" style="width: 25%;">type</th>
<th align="left">default</th>
<th align="left">description</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><code>value</code></td>
<td align="left" style="width: 25%;">

```python
tuple[str, str]
    | tuple[PIL.Image.Image, PIL.Image.Image]
    | tuple[numpy.ndarray, numpy.ndarray]
    | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">A PIL Image, numpy array, path or URL for the default value that Image component is going to take. If callable, the function will be called whenever the app loads to set the initial value of the component.</td>
</tr>

<tr>
<td align="left"><code>position</code></td>
<td align="left" style="width: 25%;">

```python
int
```

</td>
<td align="left"><code>0.5</code></td>
<td align="left">The position of the slider, between 0 and 1.</td>
</tr>

<tr>
<td align="left"><code>upload_count</code></td>
<td align="left" style="width: 25%;">

```python
int
```

</td>
<td align="left"><code>2</code></td>
<td align="left">The number of images that can be uploaded to the component. 1 or 2.</td>
</tr>

<tr>
<td align="left"><code>height</code></td>
<td align="left" style="width: 25%;">

```python
int | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">Height of the displayed image in pixels.</td>
</tr>

<tr>
<td align="left"><code>width</code></td>
<td align="left" style="width: 25%;">

```python
int | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">Width of the displayed image in pixels.</td>
</tr>

<tr>
<td align="left"><code>type</code></td>
<td align="left" style="width: 25%;">

```python
"numpy" | "pil" | "filepath"
```

</td>
<td align="left"><code>"numpy"</code></td>
<td align="left">The format the image is converted to before being passed into the prediction function. "numpy" converts the image to a numpy array with shape (height, width, 3) and values from 0 to 255, "pil" converts the image to a PIL image object, "filepath" passes a str path to a temporary file containing the image.</td>
</tr>

<tr>
<td align="left"><code>label</code></td>
<td align="left" style="width: 25%;">

```python
str | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">component name in interface.</td>
</tr>

<tr>
<td align="left"><code>every</code></td>
<td align="left" style="width: 25%;">

```python
float | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">If `value` is a callable, run the function 'every' number of seconds while the client connection is open. Has no effect otherwise. Queue must be enabled. The event can be accessed (e.g. to cancel it) via this component's .load_event attribute.</td>
</tr>

<tr>
<td align="left"><code>show_label</code></td>
<td align="left" style="width: 25%;">

```python
bool | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">if True, will display label.</td>
</tr>

<tr>
<td align="left"><code>show_download_button</code></td>
<td align="left" style="width: 25%;">

```python
bool
```

</td>
<td align="left"><code>True</code></td>
<td align="left">If True, will display button to download image.</td>
</tr>

<tr>
<td align="left"><code>container</code></td>
<td align="left" style="width: 25%;">

```python
bool
```

</td>
<td align="left"><code>True</code></td>
<td align="left">If True, will place the component in a container - providing some extra padding around the border.</td>
</tr>

<tr>
<td align="left"><code>scale</code></td>
<td align="left" style="width: 25%;">

```python
int | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">relative width compared to adjacent Components in a Row. For example, if Component A has scale=2, and Component B has scale=1, A will be twice as wide as B. Should be an integer.</td>
</tr>

<tr>
<td align="left"><code>min_width</code></td>
<td align="left" style="width: 25%;">

```python
int
```

</td>
<td align="left"><code>160</code></td>
<td align="left">minimum pixel width, will wrap if not sufficient screen space to satisfy this value. If a certain scale value results in this Component being narrower than min_width, the min_width parameter will be respected first.</td>
</tr>

<tr>
<td align="left"><code>interactive</code></td>
<td align="left" style="width: 25%;">

```python
bool | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">if True, will allow users to upload and edit an image; if False, can only be used to display images. If not provided, this is inferred based on whether the component is used as an input or output.</td>
</tr>

<tr>
<td align="left"><code>visible</code></td>
<td align="left" style="width: 25%;">

```python
bool
```

</td>
<td align="left"><code>True</code></td>
<td align="left">If False, component will be hidden.</td>
</tr>

<tr>
<td align="left"><code>elem_id</code></td>
<td align="left" style="width: 25%;">

```python
str | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">An optional string that is assigned as the id of this component in the HTML DOM. Can be used for targeting CSS styles.</td>
</tr>

<tr>
<td align="left"><code>elem_classes</code></td>
<td align="left" style="width: 25%;">

```python
list[str] | str | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">An optional list of strings that are assigned as the classes of this component in the HTML DOM. Can be used for targeting CSS styles.</td>
</tr>

<tr>
<td align="left"><code>show_share_button</code></td>
<td align="left" style="width: 25%;">

```python
bool | None
```

</td>
<td align="left"><code>None</code></td>
<td align="left">If True, will show a share icon in the corner of the component that allows user to share outputs to Hugging Face Spaces Discussions. If False, icon does not appear. If set to None (default behavior), then the icon appears if this Gradio app is launched on Spaces, but not otherwise.</td>
</tr>
</tbody></table>


### Events

| name | description |
|:-----|:------------|
| `change` | Triggered when the value of the ImageSlider changes either because of user input (e.g. a user types in a textbox) OR because of a function update (e.g. an image receives a value from the output of an event trigger). See `.input()` for a listener that is only triggered by user input. |
| `upload` | This listener is triggered when the user uploads a file into the ImageSlider. |



### User function

The impact on the users predict function varies depending on whether the component is used as an input or output for an event (or both).

- When used as an Input, the component only impacts the input signature of the user function. 
- When used as an output, the component only impacts the return signature of the user function. 

The code snippet below is accurate in cases where the component is used as both an input and an output.

- **As output:** Is passed, tuple of images in the requested format.
- **As input:** Should return, image as a numpy array, PIL Image, string/Path filepath, or string URL.

 ```python
 def predict(
     value: tuple[str, str]
    | tuple[PIL.Image.Image, PIL.Image.Image]
    | tuple[numpy.ndarray, numpy.ndarray]
    | None
 ) -> tuple[str, str]
    | tuple[PIL.Image.Image, PIL.Image.Image]
    | tuple[numpy.ndarray, numpy.ndarray]
    | None:
     return value
 ```
 