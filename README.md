# React Testing Basic

Dependencies to be installed:

```
yarn add enzyme react-test-renderer enzyme-adapter-react-16
```

##### Usage

create a same file with `*.test.js` in component directory like: `NavigationItems.test.js`

```
import React from 'react';
import { configure, shallow } from 'enzyme';
import Adapter from 'enzyme-adapter-react-16';

// Import Components
import NavigationItems from './NavigationItems';
import NavigationItem from './NavigationItem/NavigationItem';

configure({ adapter: new Adapter() });


// Start writing test
describe('First Test', () => {
  
  it('should render two <NavigationItem /> element if not authenicated', () => {
    const wrapper = shallow(<NavigationItems />);
    expect(wrapper.find(NavigationItem)).toHaveLength(2);
  })
  
});
```
