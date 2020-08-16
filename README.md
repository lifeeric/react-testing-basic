# React Testing Basic

Dependencies to be installed:

```bash
yarn add enzyme @types/enzyme react-test-renderer \
enzyme-adapter-react-16 @types/enzyme-adapter-react-16 jest \
@types/jest ts-jest enzyme-to-json --dev
```

### Configure Jest
Add the following jest.config.js file to the root of your project:
```ts
module.exports = {
  roots: ['<rootDir>/src'],
  testMatch: [
    '**/__tests__/**/*.+(ts|tsx|js)',
    '**/?(*.)+(spec|test).+(ts|tsx|js)'
  ],
  transform: {
    '^.+\\.(ts|tsx)$': 'ts-jest'
  },
  // Setup Enzyme
  snapshotSerializers: ['enzyme-to-json/serializer'],
  setupFilesAfterEnv: ['<rootDir>/src/setupEnzyme.ts'],
  moduleNameMapper: {
    '\\css|less|sass|scss$': 'identity-obj-proxy'
  }
}

```


### Enzyme configuration
Create src/setupEnzyme.ts file.
```ts
 import { configure } from 'enzyme';
 import EnzymeAdapter from 'enzyme-adapter-react-16';
 configure({ adapter: new EnzymeAdapter() });
 ```

##### Usage

create a same file with `*.test.js` in component directory like: `NavigationItems.test.js`

```ts
import React from 'react';
import { shallow } from 'enzyme';


// Import Components
import NavigationItems from './NavigationItems';
import NavigationItem from './NavigationItem/NavigationItem';

const clickFn: any = jest.fn();

// Start writing test
describe('First Test', () => {
  
  it('should render two <NavigationItem /> element if not authenicated', () => {
     const component = shallow(<DarkToggler isDark={false} onClick={clickFn} />)
     component.find('input#checkbox').simulate('click')
     expect(component).toMatchSnapshot()
  })
  
});
```
