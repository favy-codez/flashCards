### Here are some of the things I learnt during the course of this project

- **The 3 steps of using state are**
1. define the state
2. Use the state variable
3. Update the state

```
function Flashcards() {
  // step 1
  const [selectedId, setSelectedId] = useState(null)

  return (
    <div className="flashcards">
      {questions.map((question) => (
        <div key={question.id}>
          <p>{question.question}</p>
        </div>
      ))}
    </div>
  );
}
```
- we set our state to null we want nothing to be selected by default
- **Difference between onClick={handleClick(question.id)} and onClick={() =>handleClick(question.id)}** - the difference lies in how they handle event propagation and function invocation.
```
onClick={handleClick(question.id)}
```
- In this approach, the handleClick function is invoked immediately when the component renders, not when the onClick event occurs. This is because you're invoking handleClick and passing its return value (undefined unless handleClick itself returns a function) as the event handler.
- This is generally not the intended behavior. Instead of waiting for the onClick event, the handleClick function would be invoked as soon as the component renders.
- This approach might be useful if handleClick returns a function that you want to use as the event handler. For example, onClick={handleClickGenerator(question.id)} where handleClickGenerator returns a function based on question.id.
- This is more suitable,If you want to avoid unnecessary re-renders and don't need to pass additional parameters to the event handler.

**and**
```
onClick={() =>handleClick(question.id)}
```
- In this approach, an arrow function is used as the event handler. When the onClick event occurs, this arrow function is called, and it, in turn, invokes the handleClick function with question.id as an argument.
- One consequence of this approach is that a new function instance is created every time the component re-renders. If this component is rendered frequently or is part of a large list, this can lead to performance issues due to unnecessary re-renders.
- If you need to pass additional parameters or want to ensure fresh data when the event occurs, this can be used.