# react_theory

1.) Every component in react takes in data from prop & returns an HTML DOM file
2.) Everything in return should be inside one component only
3.) OutSide return we can write normal js, inside return we have to use {} braces to add js varaiable & statements
4.) React components don't Re-render untill specifically done with help of useState or UseEffect Hook

***useState***

The value returned by useState() consists of an array with two values.
The first value is the initial (or starting) value of the state variable, while the second value is a reference to the function that can be used to update the variable.


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

**Pass data from Parent to child with props**
1.) use custom attributes in component tag when used inside parent & set it's value.
2.) Now access it in parent with props.attributeName or array destructuring {attributeName, attributeName2}


Use Props to send callback function to the child -> child use props to access that function -> child call it with data which parent need -> callback is executed on the parent so parent can use that data
