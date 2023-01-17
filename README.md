# Help Queue
name of this application is Help Queue
# Application demo:
https://www.dropbox.com/s/ma58v8tnbf9ef99/help-queue-light-dark-theme.gif?raw=1

![help-queue-light-dark-theme](https://user-images.githubusercontent.com/81636030/212867664-449f328e-db2a-44c1-812a-47bc5f4c4630.gif)

# Go live:
to go live you can use yarn start or npm start: http://localhost:3000/
# Passing Props
We can pass props down to a child component using JSX tags. Let's update the TicketList.js component so it can pass props to its child Ticket.js component:

# Accessing Props
Next, let's update our Ticket so that it uses the props from its parent TicketList component.

function Ticket(props){
  return (
    <React.Fragment>
      <h3>{props.location} - {props.names}</h3>
      <p><em>{props.issue}</em></p>
      <hr/>
    </React.Fragment>
  );

# Props Are Read-Only
React components aren't just functions — they are pure functions. As we know from our functional programming course section, pure functions don't have side effects and don't alter state.

We need to follow these same rules when we are working with props. We will never alter the value of props because this would alter the state of our application and break a cardinal rule of pure functions: no side effects.

For that reason, it's very important to remember that props are read-only.


# Declaring Prop Types
While our props are working correctly, in a more complex application they can become prone to bugs. For instance, we might find ourselves passing the wrong type of data to a child component. At that point, it can become difficult to trace where the bug is coming from — especially if data is passed down through many components. Many other languages feature strict typing, which forces developers to declare the data type of variables when they are declared. JavaScript, for better or worse, is a loosely typed language and does not enforce such declarations.

For this reason, it's a best practice to assign strict data types to props with a special propTypes property. When we assign strict data types, we are simply stating that a variable (in this case, a property) must be of a certain type. If they aren't, our application will throw an error. We will always assign strict data types to all of our properties. You will also be expected to use PropTypes for all properties on independent projects.

# import PropTypes from "prop-types";
function code () gose in here
# Ticket.propTypes = {
#  names: PropTypes.string,
#  location: PropTypes.string,
#  issue: PropTypes.string
};


# Looping in JSX
Currently, our application only has two hard-coded tickets. However, this isn't how our Help Queue should actually work. A functioning, production-ready application should contain a dynamic list of ticket.

First, let's create an array of tickets in TicketList.js:
const mainTicketList = [
  {
    names: 'Thato and Haley',
    location: '3A',
    issue: 'Firebase won\'t save record. Halp.'
  },
  {
    names: 'Sleater and Kinney',
    location: '4B',
    issue: 'Prop types are throwing an error.'
  },
  {
    names: 'Imani & Jacob',
    location: '9F',
    issue: 'Child component isn\'t rendering.'
  }
];


# In the future, this list will come from a database or a Redux store
For now, we'll store hard-coded tickets inside our TicketList component. Note that we use const, not let. Remember that props are read-only and that we can't change them.

Next, we'll add a loop to render a Ticket component for each entry in mainTicketList. In JSX, we use the map() function for loops.




#  State
As a quick reminder, state is anything in an application that we need to store and change. For instance, in our Help Queue, each time we add a new ticket, we need to update the application's state to hold the new ticket. Likewise, we'd need to update the application's state to edit or delete a ticket.


# Creating and Updating State in a React Application
As we discussed in the React Components lesson, class components have a constructor that looks like this:
constructor(props) {
  super(props);
  this.state = {};
}



# Conditional Rendering

Conditional rendering is exactly what it sounds like — using a conditional to determine what content should be rendered.

  render(){
    let currentlyVisibleState = null;
    if (this.state.formVisibleOnPage) {
      currentlyVisibleState = <NewTicketForm />
    } else {
      currentlyVisibleState = <TicketList />
    }
    return (
      <React.Fragment>
        {currentlyVisibleState}
      </React.Fragment>
    );
  }

  First, we create a variable called currentlyVisibleState and set it to null because we haven't determined which component should be rendered yet.

Next, we can access any property in this.state with dot notation just as we would with any other JavaScript object. If this.state.formVisibleOnPage is true, the currentlyVisibleState will be set to our NewTicketForm component. Otherwise, our currentlyVisibleState will be set to our TicketList component.

Note that this code is just JavaScript, not JSX. We can use plain old JavaScript outside of our return() statement. We only need to use JSX and curly braces for evaluation inside our return(). We do set the value of currentlyVisibleState to React components, but this is just like setting the value of a variable to any other HTML element.

Finally, in our return() statement, we use JSX curly braces to evaluate which component should be rendered.



# Updating State with Events

First, we add a click handler to an element (such as a button).
Next, that click handler will trigger some code, often a function. We need to write that function as well.

# Adding a Click Handler to JSX
Here's how our click handler will look:
<button onClick={this.handleClick}>Add ticket</button>
Here, we take a button element and add an onClick handler to it. We need to specify the function onClick will trigger. As always, we need to use curly braces to make sure that JSX properly evaluates any JS code to the right of our onClick handler.
Note that we don't use this with function components — just class components. But we won't worry about that right now. We will get a chance to add functions to function components soon enough.
  render(){
    let currentlyVisibleState = null;
    let addTicketButton = null; // new code
    if (this.state.formVisibleOnPage) {
      currentlyVisibleState = <NewTicketForm />
    } else {
      currentlyVisibleState = <TicketList />
      addTicketButton = <button onClick={this.handleClick}>Add ticket</button> // new code
    }

            <React.Fragment>
                { currentlyVisibleState }
                {addTicketButton}
            </React.Fragment>




# Binding Functions in React
we added a button with an event handler as well as a function that triggered a change in local state.












