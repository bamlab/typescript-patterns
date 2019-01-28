# How to type HOC with Compose from Recompose ?

In [this article](./how-to-type-container-with-compose.md) we learned how to type an container with compose. Containers use HOCs. So now, let's learn how to type them.

## 📝 Example

Let's say we want to create a component `MarketTicket` which display the total price and the list of articles that a client bought. The component `MarketTicket` has those props :

- `price`
- `articles`
  `

We probably have more than one component in our project that need those informations. So it's normal that you decide to create an HOC `withTicketInformations` to inject it to your components.

Here is how we type it:

```typescript
// withTicketInformations.ts

export interface IWithTicketInformationsProps {
  price: number;
  articles: string[];
}

export type IInjectedProps = IWithIsRecipeDetailsEnabledProps;
export type IHocProps<T> = Omit<T, keyof IInjectedProps>;

const withTicketInformations = <T extends IWithTicketInformationsProps>(
  Component: React.ComponentType<T>
): React.ComponentType<IHocProps<T>> => {
  return compose<T, IHocProps<T>>()(Component);
  // Take informations whenever you want: Apollo, Redux, etc...
};

export default withTicketInformations;
```

```typescript
// Ticket.tsx

import React, { PureComponent, ReactNode } from 'react';
import { Text, View } from 'react-native';

import withTicketsInformations { IWithTicketInformations } from './withTicketInformations';

export interface IProps extends IWithTicketInformations;

class Ticket extends PureComponent<IProps> {
	public render:ReactNode (){
		// You have access to :
		// * this.props.price
		// * this.props.articles
	}
}

export default withTicketsInformations(Ticket);
```

## ✅ Check

1. In `Ticket` you must have access to `prices` and `articles` with autocompletion;
2. If `IProps` from `Ticket` doesn't extends `IWithTicketInformations` you must have an error when using your HOC;
3. In `IWithTicketInformations` if you change `articles` by `articlesList` you must see an error in `Ticket` component that tell you `articles` doesn't exist anymore.
