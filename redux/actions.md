# How to type actions in redux

Always create a constant value ACTION for the string. Use minimum strings in redux.

## Example

```typescript
export const LOGIN = "LOGIN";

// The action name shall be declared only once here! In the reducer, action creator or saga, one should use this constant, not a string to avoid the magic number issue https://en.wikipedia.org/wiki/Magic_number_(programming)

export interface ILoginPayload {
  email: string;
  password: string;
}

export interface ILoginAction {
  type: "LOGIN";
  payload: LoginPayload;
  // Well there is a magic number issue here. We cannot use the const LOGIN because it is not in the type namespace. If we use typeof LOGIN, the type will be string instead of 'LOGIN'. We need the type to be "LOGIN", and not just a string, so in our reducer when we do the switch case, the IDE will know the form of the payload.
}

export const login = (payload: LoginPayload): ILoginAction => ({
  type: LOGIN,
  payload
});

export const LOGIN_SUCCESS = "LOGIN_SUCCESS";

export interface ILoginSuccessPaylaod {
  userJWT: string;
}
// Some tslint rules will ask to prefix your interfaces with a capital I, this is subject to change

export interface ILoginSuccessAction {
  type: "LOGIN_SUCCESS";
  payload: ILoginSuccessPaylaod;
}

export const loginSuccess = (payload: ILoginSuccessPaylaod): ILoginSuccessAction => ({
  type: LOGIN_SUCCESS,
  payload
});

export type AuthActions = ILoginAction | ILoginSuccessAction;
```
