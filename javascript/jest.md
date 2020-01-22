# Jest

## Spying in automaitc `node_module` mocks
When you want to spy on methods of a module that was automatically mocked (via a file in the `__mocks__` folder that was named after the module), jest will complain. To be able to do so, you can export the functions you want to spy on from said file.

Following is an exmple of a mock for `react-native-keychain`:

```js
// __mocks__/react-native-keychain.js
export const setInternetCredentials = jest.fn()
export const getInternetCredentials = jest.fn()
```

This would allow us to do something like `expect(Keychain.setInternetCredentials).toHaveBeenCalledTimes(1)`

__Note:__ `react-native-keychain` does not have a default export. This is why we are exporting seperate `const`s here. For a module with a default export, we would have to adapt accordingly.
