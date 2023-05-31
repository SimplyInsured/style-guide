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

### Application

An Application is defined as anything sharing a single state (in this case, Redux Store).

The `App.js` is the highest level file for your Application, and can define anything up the level of a page.

**Tips**

- Avoid putting any visual components in your App.js
- Define things like your Router structure and create your store inside App.js

### Pages

The main category is the idea of `pages`.  Each page should represent a URL.  (TODO for future - Nested Pages)

```text
|-- EmployerApplication
|   |-- pages/
|       |-- CoverageOptionsPage.js

The CoverageOptionsPage.js routed to by /employer-application/coverage-options
```

**Tips**

- Pages are the start of your visual components.
- Don't create configuration based on page location.

```javascript
// bad
<Widget page={page}>
  {page == 0 ? <Body/> : <ModfiedBody/>}
</Widget>

// good
const FirstPage = () => 
  <Page>
    <Widget>
      <Body/>
    </Widget>
  </Page>

const SecondPage = () => 
  <Page>
    <Widget>
      <ModifiedBody/>
    </Widget>
  </Page>
```

- Leave single use components inside the page files.  Large page files are better than pages decomposed into 10 different files.  Break out single use components into their own file only when they are sufficiently complex enough.  When in doubt, leave it in the page file.

> Gather together those things that change for the same reason, and separate those things that change for different reasons.

### Components

The secondary category is `components`.  These are generally visual components shared between pages.

```text
|-- EmployerApplication
|   |-- components/
|       |-- ApplicationMenu.js
|       |-- QuoteInformationPanel.js
```

### Everything Else

Every other file, from sagas to redux files to helpers, should all go into the main root folder.

### Visual Representation

![Abstract Layer](https://github.com/SimplyInsured/style-guide/assets/5034574/eaf0b8e0-4cb3-4f72-a275-24ea008e5da8)

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
