# ChemAxon's MarvinJS integrated into Angular Forms
![marvinjsangular](https://user-images.githubusercontent.com/4075651/151230720-83c44bca-0d30-4436-98c4-13090e88e6c2.gif)

### Changes to `package.json`
Add MarvinJs package from Chemaxon
https://github.com/marcwittke/AngularFormsMarvinJs/blob/a6d84bdbf11ad2c7b25df46271fd55c656007758/package.json#L21

You'll need an `.npmrc` file to contain the [package source and authentication](https://docs.chemaxon.com/display/docs/public-repository.md#src-1806243-publicrepository-npm). it should looks like this:

```
@chemaxon:registry=https://hub.chemaxon.com/artifactory/api/npm/npm/
//hub.chemaxon.com/artifactory/api/npm/npm/:_password=base64encodedPassword
//hub.chemaxon.com/artifactory/api/npm/npm/:username=me@company.com
//hub.chemaxon.com/artifactory/api/npm/npm/:email=me@company.com
//hub.chemaxon.com/artifactory/api/npm/npm/:always-auth=true
```

### Changes to `angular.json`
Configure the angular compiler to integrate the MarvinJS bits:
https://github.com/marcwittke/AngularFormsMarvinJs/blob/a6d84bdbf11ad2c7b25df46271fd55c656007758/angular.json#L29-L47

For the sake of completeness you should do so for the test compilation also:
https://github.com/marcwittke/AngularFormsMarvinJs/blob/a6d84bdbf11ad2c7b25df46271fd55c656007758/angular.json#L107-L124


### Stuff the MarvinJS iframe into an Angular Component
See https://github.com/marcwittke/AngularFormsMarvinJs/blob/master/src/app/marvin-js/marvin-js-editor.component.ts

The template consists only of the iframe that loads `editor.html`. Also note, that this component implements `ControlValueAccessor`. Details on how this is done can be found at [angular-university](https://blog.angular-university.io/angular-custom-form-controls/).

### Integrate the `MarvinJsEditorComponent` into a form
This is straight forward how angular forms are working. Think of MarvinJS just as a input textbox on steroids that manipulates your structure string value with a little bit more knowledge about the semantics of this specific string.
See https://github.com/marcwittke/AngularFormsMarvinJs/blob/master/src/app/app.component.html
and https://github.com/marcwittke/AngularFormsMarvinJs/blob/master/src/app/app.component.ts
