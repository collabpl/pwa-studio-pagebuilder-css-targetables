# PWA Studio Pagebuilder CSS targetables

Allows override `*.modules.css` for `@magento/pagebuilder` components easily by
adding local css files (path is configurable but defaults to `src/pagebuilder`) as `localClasses` targetables.
merged with component's `defaultClasses` .

## Usage Example

Yours `local-intercept.js`
```javascript
const { ExtendPagebuilderCssIntercept } = require('@collabpl/pwa-studio-pagebuilder-css-targetables');
const { Targetables } = require('@magento/pwa-buildpack');

module.exports = targets => {
  const targetables = Targetables.using(targets);
  // Use @collab/pwa-studio-pagebuilder-css-targetables to allow easier overwrites of pagebuilder css files
  const extendPagebuilderCssIntercept = new ExtendPagebuilderCssIntercept(targetables);
  extendPagebuilderCssIntercept.allowPagebuilderCssOverwrites().then(() => console.log('Pagebuilder css overwrites added'));
}
```

*Big shoutout to [Lars Roettig](https://github.com/larsroettig) for [@larsroettig/component-targetables](https://github.com/larsroettig/component-targetables) - he basically did all the work, this package just references other than `venia-ui`, pagebuilder related package during build process.*

## Api Documentation
### allowPagebuilderCssOverwrites

**allowPagebuilderCssOverwrites**(`targetablesSearchPaths?`, `fileExtendsion?`, `magentoPath?`): `void`

#### Parameters

| Name | Type | Default value             |
| :------ | :------ |:--------------------------|
| `fileExtendsion` | `string` | `'*.module.css'`          |
| `targetablesSearchPaths` | `string[]`| `['src/pagebuilder']`     |
| `magentoPath` | `string` | `'node_modules/@magento'` |

#### Returns

`void`
