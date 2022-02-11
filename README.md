# Sections Modern Lib

## Prerequisites

- Node JS @latest (Preferable)
- Yarn @latest (Preferable) OR npm @latest
  > Stick to one package manager to prevent lock file conflicts

## Run Locally

**Clone the project**

```bash
  git clone https://github.com/bs-production/sections-modern.git project-name
```

**Go to the project directory**

```bash
  cd project-name
```

**Start the dev server**

```bash
  yarn dev
```

**Reset cache**

```bash
  yarn run clean
```

## Folders and files

Having a structured approach to template developement is key to a great and maintainable template.

### Root folders

- `./dist`
  - Used by the dev server and hot reloading
- `./prod`
  - Files that are meant to be consumed by the CMS
- `./src`
  - The bread and butter of the template.

### The `./src` folder

- `./src/globals`
  - Styles and HTML 'templates' that are used on all pages. These are guaranteed to be present regardless of the page or type
- `./src/pages`
  - For the purposes of this project, this folders is meant for quickly iterating the designs of sections and their flexibility. Each `.html` file inside this folders should relate to the design that is being tested.
- `./src/sections`
  - For ease of use pages are split internally into reusable and swappable sections. Each section has a high level function that it serves. For instance:
    - Hero -> To attract attention and promote the vistor's curiousity
    - Testimonials -> To instil trust into the vistor
    - CTA -> to entice the vistor to perform an action (In this case, to get a free estimate)
- `./src/components`
  - Like `./src/globals` components are used throughout the site, but they are not guaranteed to be used across all pages. Components need to be small and flexible to reduce size and increase usability
- `./src/tokens`
  - Tokens are static strings and/or raw html snippets. They come from the cms (Most of the time) and declaring them as such should be sufficient for template development
- `./src/themes`
  - These are files that are used inside the pages directory to test and alter the default section styles.

## Notes on importing css and js resources

When importing assets always import from the perspective of the pages directory.
For example, when a section imports its stylesheet it should **NOT** be relative to the section (`./styles.css`). Instead import it as if the section is inside the pages direcory (`../sections/[section]/styles.css`)

This is a limitation of caused by `posthtml-extends`. Files are first created through file reads (ending up in side the page directory) then Parcel tries to read the dependancies (which now points to the `./src/pages` direcory).

## Notes on HTML templates/modules

To import/use a html template use the `<use src="[path_to_template]">` tag. The path should be used from the perspective of the `./src` folder. For example, to use the page base template, the src attribute should be `./src/globals/page_base.html`

## Tech Stack

**Client:** ParcelJS, Tailwind CSS, Sass

### Viewing the designs

Generic styles

- localhost:1234

Design specific:

- localhost:1234/badger.html
- localhost:1234/buck.html
- localhost:1234/cantey.html
- localhost:1234/woods.html

### Generating Colors

https://tailwindcolorgenerator.com/
