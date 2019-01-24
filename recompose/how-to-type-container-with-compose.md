# How to type Container with Compose from Recompose ?

Generally, we use `compose` in containers. Containers inject props in components. So it's important to type it correctly to only expose properties that developers really need to initialize.

## 📝 Example

Let's say we have one component `Car` which have the following props:

- `brand`;
- `registration`;
- `firstRegistrationDate`.

We also have two HOCs:

- `withRegistration` that inject `registration` in `Car`;
- `withFirstRegistrationDate` that inject `firstRegistrationDate` in `Car`;

Here if how we type it:

```typescript
// Car.container.ts

import Car, { IProps } from "./Car.component";
import withRegistration, {
  IWithRegistrationProps
} from "./withRegistration.ts";
import withFirstRegistrationDate, {
  IWithFirstRegistrationDateProps
} from "./withFirstRegistrationDate.ts";
import { compose } from "recompose";

// Which props are injected by our container
type IInjectedProps = IWithRegistrationProps & IWithFirstRegistrationDateProps;

// Which props define our new component : IProps - IInjectedProps
type IContainerProps = Omit<IProps, keyof IInjectedProps>;

const CarContainer = compose<IProps, IContainerProps>(
  withRegistration,
  withFirstRegistrationDate
)(Car);

export default CarContainer;
```

## ✅ Check

1. If you use `Car`, your IDE will verify that your initialize all of his props;
2. If you use `CarContainer`, your IDE will verify that you only initialize `brand` props. Otherwise, it will throw you an error.
