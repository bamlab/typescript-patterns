# How to type a reducer

Previously on [typescript-patterns]('./actions.md').

## Example

```typescript
import { AuthActions, LOGIN_SUCCESS } from "./actions";

const initialState = {
  loggedIn: false,
  hasLoginError: false,
  userJWT: [] as string[] // You can type the value directly here instead of in the IAuthState, an empty array cuould be typed e.g. Article[]
};

export type IAuthState = typeof initialState;

export const reducer = (
  state = initialState,
  action: AuthActions
): IAuthState => {
  switch (action.type) {
    case LOGIN_SUCCESS:
      return {
        ...state,
        userJWT: action.payload.userJWT, // Here, your IDE will know the payload is of type ILoginSuccessPayload
        hasLoginError: false
      };
    default:
      return state;
  }
};
```
