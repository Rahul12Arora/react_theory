# react_theory

1.) Every component in react takes in data from prop & returns an HTML DOM file</br>
        **Pass data from Parent to child with props**</br>
        i.) use custom attributes in component tag when used inside parent & set it's value.</br>
       ii.) Now access it in parent with props.attributeName or array destructuring {attributeName, attributeName2}</br>
2.) Everything in return should be inside one component only</br>
3.) OutSide return we can write normal js, inside return we have to use {} braces to add js varaiable & statements</br>
4.) React components don't Re-render untill specifically done with help of useState or UseEffect Hook</br>

***useState***

The useState Hook can be used to keep track of strings, numbers, booleans, arrays, objects, and any combination of these!</br>
A.) The value returned by useState() consists of an array with two values.</br>
B.) The first value is the initial (or starting) value of the state variable, while the second value is a reference to the function that can be used to update the variable.

Eg-1</br>
```
const [click, setClick] = useState(0);
return (
    <div>
        <p>You've clicked {click} times!</p>
        <p>The number of times you have clicked is {click%2==0?'even!':'odd!'}</p>
        <button onClick={() => setClick(click => click + 1)}> Click me </button>
    </div>
  );
```
Eg-2</br>

```
const [click, setClick] = useState([]);

  const addNumber = () => {
    setClick([
      ...click,
      {
        id: click.length,
        value: Math.random() * 10
      }
    ]);
  };
  
  return (
    <div>
      <ul>
       {click.map(item => (
          <li key={item.id}>{item.value}</li>
       ))}
      </ul>
      <button onClick={addNumber}>
        Click me
      </button>
    </div>
  );
```

How to send data from child to parent</br>

Use Props to send callback function to the child -> child use props to access that function -> child call it with data which parent need -> callback is executed on the parent so parent can use that data</br>
or</br>

1. parent file is NewExpense.js (as an example) and child is ExpenseForm.js</br>

2. we want expenseData from ExpenseForm.js to be available in NewExpense.js</br>

3. to do this, in our parent, NewExpense.js, we create 'saveExpenseDataHandler'</br>

4. this const has a param of enteredExpenseData, this is what it expects to be passed through (the values/arguments in our ExpenseForm.js that we will eventually pass back as a param to enteredExpenseData)</br>

5. this function of saveExpenseDataHandler, we save this as a custom prop that we call onSaveExpenseData, and because this is attached to ExpenseForm (inside NewExpense.js) now we can use this custom prop which points to the function of saveExpenseDataHandler, inside our ExpenseForm.js</br>

6. In our ExpenseForm.js, props has to be passed through at the top so we can access the custom prop of onSaveExpenseData that we made in NewEspense.js</br>

7. now i can call this custom prop, as props.onSaveExpenseData(expenseData). the portion that is passed through (expenseData) is our argument, these are all the values from the const expenseData inside our ExpenseForm.js.</br>

8.Automatically now, our argument of expenseData (title,amount,data), is passed back to our parent file (NewExpense.js) and is our parameter: enteredExpenseData.</br>

9. now that we have the data from expenseData (the expenseData from ExpenseForm.js) available in our NewExpense.js file, we give it an id, and also run ...enteredExpenseData, which essentially copies the data forwarded (title: something, amount: someamount, Date: someday).</br>

10. So now, we offically have this data available for use in NewExpense.js</br>

11. App.js is the parent now, and NewExpense.js is the child, so if you repeat the steps, (make a custom prop in App.js, pass it through to be used in NewExpense.js, then you will also have the data of expenseData available in App.js)</br>

12. You can tell who is the parent and child by the custom components we create</br>
