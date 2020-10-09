#content on react component/constructor credit in full to both sites linked below, noted here as it is dense material

<https://reactjs.org/docs/react-component.html#constructor>
constructor()

constructor(props)

If you don’t initialize state and you don’t bind methods, you don’t need to implement a constructor for your React component.

The constructor for a React component is called before it is mounted. When implementing the constructor for a React.Component subclass, you should call super(props) before any other statement. Otherwise, this.props will be undefined in the constructor, which can lead to bugs.

Typically, in React constructors are only used for two purposes:

    Initializing local state by assigning an object to this.state.
    Binding event handler methods to an instance.

You should not call setState() in the constructor(). Instead, if your component needs to use local state, assign the initial state to this.state directly in the constructor:

constructor(props) {
  super(props);
  // Don't call this.setState() here!
  this.state = { counter: 0 };
  this.handleClick = this.handleClick.bind(this);
}

Constructor is the only place where you should assign this.state directly. In all other methods, you need to use this.setState() instead.

Avoid introducing any side-effects or subscriptions in the constructor. For those use cases, use componentDidMount() instead.

    Note

    Avoid copying props into state! This is a common mistake:

    constructor(props) {
     super(props);
     // Don't do this!
     this.state = { color: props.color };
    }
    
    
<https://www.freecodecamp.org/learn/front-end-libraries/react/create-a-react-component>
This creates an ES6 class Kitten which extends the React.Component class. So the Kitten class now has access to many useful React features, such as local state and lifecycle hooks. Don't worry if you aren't familiar with these terms yet, they will be covered in greater detail in later challenges. Also notice the Kitten class has a constructor defined within it that calls super(). It uses super() to call the constructor of the parent class, in this case React.Component. The constructor is a special method used during the initialization of objects that are created with the class keyword. It is best practice to call a component's constructor with super, and pass props to both. This makes sure the component is initialized properly. For now, know that it is standard for this code to be included. Soon you will see other uses for the constructor as well as props.

