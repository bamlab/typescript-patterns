# How to type a reducer

Previously on [typescript-patterns]('./actions.md').

## Example

```typescript
import { AuthActions } from "./actions"

const initialState = {
  loggedIn: false,
  userJWT: [] as string, // You can type the value directly here instead of in the IAuthState, an empty array cuould be typed e.g. Article[]
  complexObject: undefined as ComplexObject | undefined // You can specify the future type of a state property
};

const IAuthState = typeof initialState;

const reducer
(
  state = initialState,
  action: AuthActions
): IAuthState {switch (action.type) {
    case LOGIN_SUCCESS:
      return {
        ...state,
        userJWT: action.payload.userJWT, // Here, your IDE will know the payload is of type ILoginSuccessPayload
        hasLoginError: false
      };
    default:
      return state;}
```
