# Folder / File Conventions

## Application Structure

```text
|-- Application/
|   |-- pages/
|   |-- components/
|   | App.js
|   | store.js
|   | reducers.js
|   | actions.js
|   | selectors.js
|   | api.js
|   | sagas.js
|   | ...file.js
```

An Application is defined as anything sharing a single state (in this case, Redux Store).

The `App.js` is the highest level file for your Application, and can define anything up the level of a page.  This generally means nothing visual is defined here.
  
The main category is the idea of `pages`.  Each page should represent a URL.  (TODO for future - Nested Pages)

```text
|-- EmployerApplication
|   |-- pages/
|       |-- CoverageOptionsPage.js

The CoverageOptionsPage.js routed to by /employer-application/coverage-options
```

The secondary category is `components`.  These are generally visual components shared between pages, and can be "single use" (only used on one page) on occasion.

```text
|-- EmployerApplication
|   |-- components/
|       |-- ApplicationMenu.js
|       |-- QuoteInformationPanel.js
```

Every other file, from sagas to redux files to helpers, should all go into the main root folder.

## File Naming

The main `App` file, all Pages and Components should be `PascalCase`

```javascript
// good
CoverageOptionsPage.js
Button.js
```

Everything else should be `camelCase`

```javascript
// good
utils.js
reducers.js
sagas.js
```
