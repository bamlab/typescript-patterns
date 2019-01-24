# How to type a reducer

Previously on [typescript-patterns]('./actions.md').

## Example

```typescript
import { AuthActions } from "./actions"

const initialState = {
  loggedIn: false,
  userJWT: "" as tring
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
