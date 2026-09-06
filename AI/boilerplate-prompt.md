# AI TIL: Explicit Scope and Negative Constraints

## What I learned

When asking AI to create a simple scaffold or boilerplate, the word **"boilerplate"** can be interpreted more broadly than intended.

For example, asking:

> Create an HTML boilerplate with JavaScript and CSS files attached.

may cause AI to generate example UI, styling, content, or other unnecessary code.

If the goal is a **bare-bones scaffold**, explicitly state both what should be created and what should **not** be created.

## Better approach

Define:

- Exact files to create
- What each file should contain
- What should remain empty
- What should not be added
- Whether additional files are allowed

Example:

> Create exactly these files:
> - `index.html`
> - `style.css`
> - `script.js`
>
> `index.html` should contain only the minimum HTML5 structure and links to the CSS and JavaScript files.
>
> `style.css` and `script.js` must be empty.
>
> Do not add UI, sample content, styling, comments, libraries, frameworks, dependencies, or additional files.

## Key takeaway

**When minimal output is required, don't only describe what AI should create. Explicitly describe what AI should not create.**

### AI Development Guideline

> **AI must respect the requested scope and must not introduce unsolicited implementation, content, dependencies, or files.**
