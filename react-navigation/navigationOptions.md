# How to type your custom navigation options in your component

In React-Navigation you can set a static NavigationScreenOptions, which is either an object or a function.

## Setting a constant navigation option

Here is an example of static navigation options.

```ts
interface Props {
  binUid: string;
  navigation: NavigationScreenProp<NavigationState>;
}

export class PickItem extends React.Component<Props> {
  static navigationOptions: NavigationScreenOptions = {
    title: "Pick Item"
  };

  public render() {
    return (
      <View>
        <Text>BinUid : {this.props.binUid}</Text>
        <Button onPress={this.props.navigation.goBack()}>Go Back !</Button>
      </View>
    );
  }
}
```

## Usin
