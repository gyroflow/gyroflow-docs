## Help with documentation

This site uses [MkDocs](https://www.mkdocs.org/) and [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/) and is formatted with Markdown. Here's how to serve a local version for editing purposes

1. Install MkDocs and Material for MkDocs: `pip install mkdocs-material`
2. Clone the repo: `git clone https://github.com/gyroflow/gyroflow-docs.git`
3. Run local server: `mkdocs serve`

Alternatively each page has an edit button which directly opens the GitHub online editor.

In general, create GitHub pull request to merge the edits.


## MkDocs/Markdown snippets


!!! note

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! note ""

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! warning "This is a warning"

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

Image with lightbox:
![!Image title](https://dummyimage.com/600x400/eee/aaa)


This is some text with a footnote[^samplefootnote].

[^samplefootnote]: Content of the footnote

Here's a LaTeX math block rendered using MathJax
$$ c = \sqrt{a^2 + b^2} $$

Here's a Python code block with line numbers

```py linenums="1"
# Generate 24 different (right handed) orientations using cross products
def generate_rotmats():
    basis = [[1,0,0], [0,1,0], [0,0,1], [-1,0,0], [0,-1,0], [0,0,-1]] # Six different unit vectors
    basis = [np.array(v) for v in basis]
    ORIENTATIONS = []


    for i in range(len(basis)):
        for j in range(len(basis)):
            if i != j and (i + 3) % 6 != j:
                ivec = basis[i]
                jvec = basis[j]
                kvec = np.cross(ivec,jvec)
                mat = np.vstack([ivec, jvec, kvec]).transpose()
                ORIENTATIONS.append(mat)
```