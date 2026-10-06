# React Hooks: Real Use Cases, Interview Answers, and Examples

Hooks let React function components remember data, synchronize with external systems, access DOM elements, and control rendering.

For interviews, explain each hook in this order: **what it does → the problem it solves → a real example → an important limitation**.

This guide covers **all 18 built-in React hooks**, React DOM's `useFormStatus`, the related `use()` API, and custom hooks.

## How to use the examples

- Run each example separately in a React project with JSX support.
- Each example is a component or group of components, not a separate complete project.
- Pass appropriate props to components that accept employee lists, items, text, IDs, or Promises.
- Replace demonstration API endpoints with your backend endpoints.
- Timer-based requests simulate a backend; they do not save real data.
- `useActionState`, `useOptimistic`, `useFormStatus`, and `use()` require React 19.
- `useEffectEvent` requires React 19.2 or later.
- The `ref`-as-prop example uses React 19; React 18 needs `forwardRef`.
- In a React Server Components framework, interactive hook examples belong in Client Components.

## Contents

1. [useState](#1-usestate)
2. [useEffect](#2-useeffect)
3. [useContext](#3-usecontext)
4. [useRef](#4-useref)
5. [useReducer](#5-usereducer)
6. [useMemo](#6-usememo)
7. [useCallback](#7-usecallback)
8. [useLayoutEffect](#8-uselayouteffect)
9. [useImperativeHandle](#9-useimperativehandle)
10. [useId](#10-useid)
11. [useTransition](#11-usetransition)
12. [useDeferredValue](#12-usedeferredvalue)
13. [useSyncExternalStore](#13-usesyncexternalstore)
14. [useDebugValue](#14-usedebugvalue)
15. [useInsertionEffect](#15-useinsertioneffect)
16. [useActionState](#16-useactionstate)
17. [useOptimistic](#17-useoptimistic)
18. [useEffectEvent](#18-useeffectevent)
19. [useFormStatus](#19-useformstatus)
20. [use API](#20-use-api)
21. [Custom hooks](#21-custom-hooks)
22. [Interview comparisons](#interview-comparisons)
23. [Common interview questions](#common-interview-questions)

## 1. useState

**Purpose:** Store data that affects the screen.

**Real case:** Cart quantity, input text, selected tab, or modal visibility.

**Problem solved:** A normal local variable does not persist between renders or request a UI update when changed.

**Interview answer:** “`useState` adds local state to a function component. Its setter requests a render with the updated value. When the next value depends on the previous one, I use a functional updater.”

```jsx
import { useState } from "react";

export default function CartQuantity() {
  const [quantity, setQuantity] = useState(1);

  return (
    <div>
      <button
        disabled={quantity === 1}
        onClick={() => setQuantity(previous => previous - 1)}
      >
        −
      </button>
      <span> {quantity} </span>
      <button onClick={() => setQuantity(previous => previous + 1)}>
        +
      </button>
      <p>Total: ₹{quantity * 500}</p>
    </div>
  );
}
```

**Important:** State is a snapshot for the current render. Calling its setter does not change the value already captured by your running event handler. Update objects and arrays immutably.

## 2. useEffect

**Purpose:** Synchronize with an external system.

**Real case:** Fetch employee details when an ID changes, subscribe to a socket, or start a timer.

**Problem solved:** External work needs setup, synchronization when dependencies change, and cleanup.

**Interview answer:** “I use `useEffect` to synchronize a component with something outside React. Dependencies determine when synchronization repeats, and cleanup removes the previous subscription or cancels obsolete work.”

```jsx
import { useEffect, useState } from "react";

export default function Employee({ employeeId }) {
  const [result, setResult] = useState({
    data: null,
    loading: true,
    error: "",
  });

  useEffect(() => {
    const controller = new AbortController();
    let active = true;

    setResult({ data: null, loading: true, error: "" });

    async function load() {
      try {
        // Replace with your backend endpoint.
        const response = await fetch(`/api/employees/${employeeId}`, {
          signal: controller.signal,
        });

        if (!response.ok) throw new Error("Unable to load employee");
        const data = await response.json();

        if (active) {
          setResult({ data, loading: false, error: "" });
        }
      } catch (error) {
        if (active && error.name !== "AbortError") {
          setResult({ data: null, loading: false, error: error.message });
        }
      }
    }

    load();

    return () => {
      active = false;
      controller.abort();
    };
  }, [employeeId]);

  if (result.loading) return <p>Loading...</p>;
  if (result.error) return <p role="alert">{result.error}</p>;

  return <h2>{result.data.name}</h2>;
}
```

**Why cleanup matters:** If the employee changes quickly, an old request should not overwrite the new employee's data.

| Dependency array | When the Effect runs |
| --- | --- |
| Omitted | After every committed render |
| `[]` | On mounting |
| `[employeeId]` | On mounting and when that dependency changes |

**Important:** Development Strict Mode can perform an extra setup → cleanup → setup cycle. Derive values such as `quantity * price` during rendering instead of storing them through an Effect. Effects do not run during server rendering.

## 3. useContext

**Purpose:** Read shared information.

**Real case:** Theme, language, or authenticated user information.

**Problem solved:** Passing the same information through many intermediate components creates prop drilling.

**Interview answer:** “`useContext` reads and subscribes to the nearest matching provider. It makes shared data available deeply in the tree without passing it through every component.”

```jsx
import { createContext, useContext } from "react";

const UserContext = createContext(null);

function Profile() {
  const user = useContext(UserContext);
  return <p>Welcome, {user?.name ?? "Guest"}</p>;
}

export default function App() {
  return (
    <UserContext.Provider value={{ name: "Sakthi" }}>
      <Profile />
    </UserContext.Provider>
  );
}
```

**Important:** Context consumers update when the provider value changes. Context is not automatically a performance optimization or a complete state-management system.

## 4. useRef

**Purpose:** Preserve a value without requesting a render.

**Real case:** Focus an input, access a video element, or remember a timer ID.

**Problem solved:** Some values need to persist but should not drive UI rendering.

**Interview answer:** “`useRef` returns a persistent object with a `current` property. Updating it does not request a render. I use it for DOM access and mutable values that are not displayed.”

```jsx
import { useRef } from "react";

export default function SearchBox() {
  const inputRef = useRef(null);

  return (
    <div>
      <input ref={inputRef} placeholder="Search employees" />
      <button onClick={() => inputRef.current?.focus()}>
        Focus search
      </button>
    </div>
  );
}
```

**Important:** If a changing value must appear on screen, use state rather than only a ref. Avoid reading or writing refs during rendering except for supported initialization patterns.

## 5. useReducer

**Purpose:** Organize related state transitions.

**Real case:** A cart, multi-step form, or editor with several actions.

**Problem solved:** Many related state updates become difficult to maintain across event handlers.

**Interview answer:** “`useReducer` centralizes state transitions in a pure reducer. Components dispatch actions describing what happened, and the reducer calculates the next state.”

```jsx
import { useReducer } from "react";

function reducer(state, action) {
  switch (action.type) {
    case "add":
      return [...state, action.item];
    case "remove":
      return state.filter(item => item.id !== action.id);
    case "clear":
      return [];
    default:
      return state;
  }
}

export default function Cart() {
  const [items, dispatch] = useReducer(reducer, []);

  return (
    <div>
      <button
        onClick={() => dispatch({
          type: "add",
          item: { id: crypto.randomUUID(), name: "Shirt" },
        })}
      >
        Add shirt
      </button>
      {items.map(item => (
        <p key={item.id}>
          {item.name}
          <button
            onClick={() => dispatch({ type: "remove", id: item.id })}
          >
            Remove
          </button>
        </p>
      ))}
      <button onClick={() => dispatch({ type: "clear" })}>
        Clear cart
      </button>
    </div>
  );
}
```

**Important:** Do not make API calls or mutate existing state inside the reducer. Reducers should return the next state without side effects.

## 6. useMemo

**Purpose:** Reuse a calculated result.

**Real case:** Filtering a large employee list or calculating an expensive report.

**Problem solved:** An unrelated render would otherwise repeat the calculation.

**Interview answer:** “`useMemo` caches a calculation result while its dependencies remain unchanged. I use it for expensive calculations or when a stable calculated value benefits a memoized child.”

```jsx
import { useMemo, useState } from "react";

export default function Employees({ employees }) {
  const [query, setQuery] = useState("");
  const [showCount, setShowCount] = useState(false);

  const filtered = useMemo(() => {
    return employees.filter(employee =>
      employee.name.toLowerCase().includes(query.toLowerCase())
    );
  }, [employees, query]);

  return (
    <div>
      <input
        value={query}
        onChange={event => setQuery(event.target.value)}
      />
      <button onClick={() => setShowCount(value => !value)}>
        Toggle count
      </button>
      {showCount && <p>Matches: {filtered.length}</p>}
      {filtered.map(employee => (
        <p key={employee.id}>{employee.name}</p>
      ))}
    </div>
  );
}
```

**Important:** It does not prevent the component itself from rendering. Treat memoization as an optimization, not a requirement for correct behavior. A newly created `employees` array also changes this dependency.

## 7. useCallback

**Purpose:** Reuse a function reference.

**Real case:** Pass an event handler to a memoized child.

**Problem solved:** A newly created function prop can defeat the child's prop comparison.

**Interview answer:** “`useCallback` caches a function reference until dependencies change. It is useful when function identity matters, particularly with memoized children.”

```jsx
import { memo, useCallback, useState } from "react";

const AddButton = memo(function AddButton({ onAdd }) {
  return <button onClick={onAdd}>Add</button>;
});

export default function Dashboard() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState("");

  const handleAdd = useCallback(() => {
    setCount(previous => previous + 1);
  }, []);

  return (
    <div>
      <input
        value={text}
        onChange={event => setText(event.target.value)}
      />
      <p>{count}</p>
      <AddButton onAdd={handleAdd} />
    </div>
  );
}
```

**Important:** `useCallback` alone does not stop child rendering. In this example, `memo` also matters. Include reactive values used by the callback in its dependencies.

## 8. useLayoutEffect

**Purpose:** Measure layout before painting.

**Real case:** Measure a tooltip to position it without a visible jump.

**Problem solved:** Measuring and adjusting after painting can produce flicker.

**Interview answer:** “`useLayoutEffect` runs after DOM updates but before the browser paints. I use it when layout measurement or a visual correction must happen before the user sees the frame.”

```jsx
import { useLayoutEffect, useRef, useState } from "react";

export default function Tooltip({ text }) {
  const ref = useRef(null);
  const [height, setHeight] = useState(0);

  useLayoutEffect(() => {
    setHeight(ref.current.getBoundingClientRect().height);
  }, [text]);

  return (
    <span style={{ position: "relative", display: "inline-block" }}>
      Hover information
      <span
        ref={ref}
        style={{
          position: "absolute",
          top: -height - 8,
          left: 0,
          width: 180,
          padding: 8,
          background: "#222",
          color: "white",
        }}
      >
        {text}
      </span>
    </span>
  );
}
```

**Important:** It blocks painting. Prefer `useEffect` when the work does not require this timing. This simplified example demonstrates positioning, not full tooltip interaction or accessibility behavior.

## 9. useImperativeHandle

**Purpose:** Expose selected methods through a ref.

**Real case:** A parent needs to focus or select text in a reusable input.

**Problem solved:** The child exposes a small public interface instead of its entire internal DOM implementation.

**Interview answer:** “`useImperativeHandle` customizes what a parent receives through a ref. I use it for limited imperative operations such as focus, selection, or controlling a third-party widget.”

```jsx
import { useImperativeHandle, useRef } from "react";

// React 19: ref can be received as a prop.
function CustomInput({ ref }) {
  const inputRef = useRef(null);

  useImperativeHandle(ref, () => ({
    focus() {
      inputRef.current?.focus();
    },
    select() {
      inputRef.current?.select();
    },
  }), []);

  return <input ref={inputRef} defaultValue="Sakthi" />;
}

export default function Form() {
  const ref = useRef(null);

  return (
    <div>
      <CustomInput ref={ref} />
      <button onClick={() => ref.current?.select()}>
        Select name
      </button>
    </div>
  );
}
```

**Important:** React 18 requires `forwardRef` to receive the ref. Prefer ordinary props when the operation can be expressed declaratively.

## 10. useId

**Purpose:** Create IDs for accessibility relationships.

**Real case:** Reusable form fields need unique IDs for labels and descriptions.

**Problem solved:** Hardcoded IDs collide when multiple copies of a component appear.

**Interview answer:** “`useId` generates an ID suitable for connecting accessibility attributes, such as an input's ID with its label and help text. It also supports consistent server and client rendering.”

```jsx
import { useId } from "react";

export default function EmailField() {
  const id = useId();

  return (
    <div>
      <label htmlFor={`${id}-email`}>Email</label>
      <input
        id={`${id}-email`}
        type="email"
        aria-describedby={`${id}-help`}
      />
      <small id={`${id}-help`}>Enter your work email.</small>
    </div>
  );
}
```

**Important:** Do not use `useId` to generate list keys. Keys should come from stable data IDs.

## 11. useTransition

**Purpose:** Mark an update as non-urgent.

**Real case:** Keep an input responsive while rendering a large search result list.

**Problem solved:** An expensive UI update can compete with urgent updates such as typing.

**Interview answer:** “`useTransition` lets me mark state updates as non-blocking and provides a pending flag. React can prioritize urgent work and interrupt the transition's rendering.”

```jsx
import { memo, useState, useTransition } from "react";

const Results = memo(function Results({ items, query }) {
  const matches = items.filter(item =>
    item.name.toLowerCase().includes(query.toLowerCase())
  );

  return matches.map(item => <p key={item.id}>{item.name}</p>);
});

export default function Search({ items }) {
  const [input, setInput] = useState("");
  const [query, setQuery] = useState("");
  const [isPending, startTransition] = useTransition();

  function handleChange(event) {
    const value = event.target.value;
    setInput(value); // Urgent input update.

    startTransition(() => {
      setQuery(value); // Non-urgent results update.
    });
  }

  return (
    <div>
      <input value={input} onChange={handleChange} />
      {isPending && <p>Updating results...</p>}
      <Results items={items} query={query} />
    </div>
  );
}
```

**Important:** Keep the state controlling a text input outside the transition. Transitions do not move arbitrary JavaScript work to another thread. A single long calculation can still block the main thread.

## 12. useDeferredValue

**Purpose:** Defer an existing value.

**Real case:** A slow list or chart temporarily uses an older value while the input updates immediately.

**Problem solved:** You want to prioritize rendering without controlling the setter that produced the value.

**Interview answer:** “`useDeferredValue` gives a deferred version of a value. Urgent rendering can use the current value while an expensive subtree catches up in the background.”

```jsx
import { memo, useDeferredValue, useState } from "react";

const Results = memo(function Results({ items, query }) {
  return items
    .filter(item => item.name.includes(query))
    .map(item => <p key={item.id}>{item.name}</p>);
});

export default function Search({ items }) {
  const [query, setQuery] = useState("");
  const deferredQuery = useDeferredValue(query);

  return (
    <div>
      <input
        value={query}
        onChange={event => setQuery(event.target.value)}
      />
      <div style={{ opacity: query !== deferredQuery ? 0.5 : 1 }}>
        <Results items={items} query={deferredQuery} />
      </div>
    </div>
  );
}
```

**Important:** This is not debouncing. It has no fixed delay and does not automatically reduce network requests. Memoizing the slow child lets it skip urgent renders with unchanged deferred props.

## 13. useSyncExternalStore

**Purpose:** Subscribe to an external source.

**Real case:** Browser connectivity or a store maintained outside React.

**Problem solved:** React needs a reliable subscription and snapshot mechanism for external state.

**Interview answer:** “`useSyncExternalStore` subscribes to an external store and reads its current snapshot. It helps keep external data consistent with React rendering.”

```jsx
import { useSyncExternalStore } from "react";

function subscribe(callback) {
  window.addEventListener("online", callback);
  window.addEventListener("offline", callback);

  return () => {
    window.removeEventListener("online", callback);
    window.removeEventListener("offline", callback);
  };
}

function getSnapshot() {
  return navigator.onLine;
}

function getServerSnapshot() {
  return true;
}

export default function ConnectionStatus() {
  const online = useSyncExternalStore(
    subscribe,
    getSnapshot,
    getServerSnapshot
  );

  return <p>{online ? "Online" : "Offline"}</p>;
}
```

**Important:** Snapshots must remain stable while underlying data is unchanged. Browser online status does not guarantee that your API is reachable. The server snapshot must match the snapshot used during hydration.

## 14. useDebugValue

**Purpose:** Label a custom hook in React DevTools.

**Real case:** A shared authentication hook should show a useful debugging label.

**Problem solved:** Custom hooks can be difficult to inspect without meaningful labels.

**Interview answer:** “`useDebugValue` adds a label to a custom hook in React DevTools. It helps debugging and does not render anything in the application.”

```jsx
import { useDebugValue, useState } from "react";

function useAuthStatus() {
  const [loggedIn, setLoggedIn] = useState(false);
  useDebugValue(loggedIn ? "Logged in" : "Logged out");
  return { loggedIn, setLoggedIn };
}

export default function LoginDemo() {
  const { loggedIn, setLoggedIn } = useAuthStatus();

  return (
    <button onClick={() => setLoggedIn(value => !value)}>
      {loggedIn ? "Log out" : "Log in"}
    </button>
  );
}
```

**Important:** This illustrates UI state, not a real authentication system.

## 15. useInsertionEffect

**Purpose:** Insert styles for a styling library.

**Real case:** A CSS-in-JS library injects generated styles before layout Effects measure elements.

**Problem solved:** Layout measurements should not happen before required styles have been inserted.

**Interview answer:** “`useInsertionEffect` is mainly for CSS-in-JS library authors. It provides a place to insert styles before layout Effects run. I rarely need it in ordinary application components.”

```jsx
import { useInsertionEffect } from "react";

export default function StyledButton() {
  useInsertionEffect(() => {
    const style = document.createElement("style");

    style.textContent = `
      .demo-save-button {
        background: navy;
        color: white;
        padding: 10px;
      }
    `;

    document.head.appendChild(style);
    return () => style.remove();
  }, []);

  return <button className="demo-save-button">Save</button>;
}
```

**Important:** This is a small client-side illustration. Production styling libraries also handle deduplication and server rendering. Do not update state or rely on attached refs inside this hook.

## 16. useActionState

**Purpose:** Manage an action's result.

**Real case:** Submit an employee form and display validation or success messages.

**Problem solved:** Action results and pending status otherwise require manual coordination.

**Interview answer:** “`useActionState` connects an action to state. The action receives the previous state and its payload, and its returned value becomes the next state. The hook also exposes pending status.”

```jsx
import { useActionState } from "react";

async function saveEmployee(previousState, formData) {
  const name = String(formData.get("name") ?? "").trim();

  if (name.length < 2) {
    return { error: "Enter at least two characters.", message: "" };
  }

  // Simulated request.
  await new Promise(resolve => setTimeout(resolve, 1000));
  return { error: "", message: `${name} saved successfully.` };
}

export default function EmployeeForm() {
  const [state, formAction, pending] = useActionState(
    saveEmployee,
    { error: "", message: "" }
  );

  return (
    <form action={formAction}>
      <input name="name" placeholder="Employee name" required />
      <button disabled={pending}>
        {pending ? "Saving..." : "Save"}
      </button>
      {state.error && <p role="alert">{state.error}</p>}
      {state.message && <p role="status">{state.message}</p>}
    </form>
  );
}
```

**Important:** Requires React 19. Handle expected backend failures inside the action and return useful error state. The hook does not replace backend validation.

## 17. useOptimistic

**Purpose:** Show a temporary update before confirmation.

**Real case:** A like count or new comment appears immediately while saving.

**Problem solved:** Waiting for every server response can make interactions feel slow.

**Interview answer:** “`useOptimistic` derives temporary UI state while an Action is pending. The confirmed state remains the source of truth, and the optimistic state is reconciled when the Action completes.”

```jsx
import { useOptimistic, useState } from "react";
import { useFormStatus } from "react-dom";

async function saveLike(nextCount) {
  // Simulated successful response.
  await new Promise(resolve => setTimeout(resolve, 1000));
  return nextCount;
}

function LikeSubmit({ count }) {
  const { pending } = useFormStatus();

  return (
    <button disabled={pending}>
      👍 {count} {pending ? "(saving...)" : ""}
    </button>
  );
}

export default function Likes() {
  const [likes, setLikes] = useState(10);
  const [error, setError] = useState("");

  const [optimisticLikes, addOptimistic] = useOptimistic(
    likes,
    (current, amount) => current + amount
  );

  async function likeAction() {
    setError("");
    addOptimistic(1);

    try {
      const confirmed = await saveLike(likes + 1);
      setLikes(confirmed);
    } catch {
      setError("Unable to save your like.");
    }
  }

  return (
    <form action={likeAction}>
      <LikeSubmit count={optimisticLikes} />
      {error && <p role="alert">{error}</p>}
    </form>
  );
}
```

**What happens:** The count displays `11` immediately. Success confirms `11`. If saving fails, the confirmed count stays `10` and the temporary increment disappears after the Action finishes.

**Important:** Requires React 19. Optimistic updates must run inside an Action or transition. The hook does not perform the server request itself. Production counters need server-side concurrency handling; this demo disables repeated submissions.

## 18. useEffectEvent

**Purpose:** Read current values without restarting synchronization.

**Real case:** A timer logs the latest reminder text without restarting whenever the text changes.

**Problem solved:** Adding a value to Effect dependencies would restart the timer, while omitting it from an ordinary callback can leave a stale closure.

**Interview answer:** “`useEffectEvent` separates event-like logic from Effect synchronization. Its callback reads the latest committed props and state without making those reads trigger resynchronization.”

```jsx
import { useEffect, useEffectEvent, useState } from "react";

export default function Reminder() {
  const [message, setMessage] = useState("Practise React");

  const logReminder = useEffectEvent(() => {
    console.log(message);
  });

  useEffect(() => {
    const timer = setInterval(() => {
      logReminder();
    }, 5000);

    return () => clearInterval(timer);
  }, []);

  return (
    <input
      value={message}
      onChange={event => setMessage(event.target.value)}
    />
  );
}
```

**Important:** Requires React 19.2 or later. Call Effect Events from Effect logic, not button handlers. Do not pass them to other components or use them to hide dependencies that should restart synchronization. Exclude Effect Events from Effect dependency arrays.

## 19. useFormStatus

**Import:** `react-dom`.

**Purpose:** Read a parent form's submission status.

**Real case:** A reusable submit button displays “Saving…” for whichever Action form contains it.

**Problem solved:** The button does not need pending state passed through props.

**Interview answer:** “`useFormStatus` reads submission information from the nearest parent form. It must be used in a component rendered inside that form.”

```jsx
import { useFormStatus } from "react-dom";

function SubmitButton() {
  const { pending } = useFormStatus();

  return (
    <button disabled={pending}>
      {pending ? "Submitting..." : "Submit"}
    </button>
  );
}

export default function ContactForm() {
  async function submit(formData) {
    await new Promise(resolve => setTimeout(resolve, 1000));
    console.log(formData.get("email"));
  }

  return (
    <form action={submit}>
      <input name="email" type="email" required />
      <SubmitButton />
    </form>
  );
}
```

**Important:** Calling it in `ContactForm` itself would not track the form that `ContactForm` returns. The hook also exposes submission `data`, `method`, and `action`.

## 20. use API

React documents `use()` as an API rather than a Hook.

**Purpose:** Read a Promise or context during rendering.

**Real case:** Read a stable Promise provided by a framework or data layer and display a loading fallback while it is pending.

**Problem solved:** It integrates resource reading with Suspense during rendering.

**Interview answer:** “`use()` reads a resource during rendering. Reading a pending Promise suspends the component, so Suspense can display a fallback. Unlike ordinary hooks, `use()` can be called conditionally.”

```jsx
import { Suspense, use } from "react";

function EmployeeDetails({ employeePromise }) {
  const employee = use(employeePromise);
  return <h2>{employee.name}</h2>;
}

export default function Page({ employeePromise }) {
  return (
    <Suspense fallback={<p>Loading...</p>}>
      <EmployeeDetails employeePromise={employeePromise} />
    </Suspense>
  );
}
```

**Important:** The Promise must be stable across renders. Avoid creating a new fetch Promise each render. Use an Error Boundary for rejected Promises; do not wrap `use()` in `try...catch`. It must still be called inside a component or custom hook.

## 21. Custom hooks

**Purpose:** Reuse stateful logic.

**Real case:** Several search fields need debouncing.

**Problem solved:** Repeating the same state, timer, and cleanup logic across components creates duplication.

**Interview answer:** “A custom hook is a function whose name starts with `use` and which composes React hooks. It shares logic, but each call normally has independent state.”

```jsx
import { useEffect, useState } from "react";

function useDebounce(value, delay = 400) {
  const [debounced, setDebounced] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebounced(value);
    }, delay);

    return () => clearTimeout(timer);
  }, [value, delay]);

  return debounced;
}

export default function Search() {
  const [query, setQuery] = useState("");
  const debouncedQuery = useDebounce(query);

  return (
    <div>
      <input
        value={query}
        onChange={event => setQuery(event.target.value)}
      />
      <p>Query ready for searching: {debouncedQuery}</p>
    </div>
  );
}
```

**Important:** This debounces a value. If you use it for API requests, also handle cancellation and stale responses.

## Interview comparisons

| Comparison | Interview answer |
| --- | --- |
| `useState` vs `useRef` | State updates request rendering; ref updates do not. |
| `useState` vs `useReducer` | State is convenient for direct updates; a reducer organizes related transitions. |
| `useMemo` vs `useCallback` | Memo caches a calculation result; callback caches a function reference. |
| `useEffect` vs `useLayoutEffect` | Layout Effects run before paint and block it; prefer ordinary Effects unless that timing is necessary. |
| `useTransition` vs `useDeferredValue` | Transition marks updates; deferred value provides a lagging version of a value. |
| Debounce vs `useDeferredValue` | Debounce waits for a configured delay; deferred value adjusts rendering priority. |
| `useActionState` vs `useFormStatus` | Action state manages an action's result; form status reads a containing form's submission status. |
| `useOptimistic` vs `useState` | Optimistic state is temporary during an Action; state stores the confirmed application value. |

## Rules of Hooks

- Call ordinary hooks at the top level of a function component or custom hook.
- Call them before conditional early returns.
- Do not call ordinary hooks inside loops, conditions, event handlers, or nested functions.
- Keep render logic pure.
- Include reactive values used by Effects and memoized calculations/callbacks in their dependency arrays.
- Use the React hooks ESLint rules to catch ordering and dependency mistakes.
- `use()` has different ordering rules: it may be conditional, but still belongs inside a component or hook.

```jsx
// Incorrect: hook order changes depending on loggedIn.
function IncorrectProfile({ loggedIn }) {
  if (!loggedIn) return null;
  const [name, setName] = useState("");
  return <input value={name} onChange={e => setName(e.target.value)} />;
}

// Correct: the hook runs before the conditional return.
function CorrectProfile({ loggedIn }) {
  const [name, setName] = useState("");
  if (!loggedIn) return null;
  return <input value={name} onChange={e => setName(e.target.value)} />;
}
```

The rules example assumes `useState` is imported from `react`.

## Common interview questions

### 1. Why can't ordinary hooks be called conditionally?

React relies on a consistent hook order between renders to associate hooks with their stored state.

### 2. When does Effect cleanup run?

Before the Effect sets up again after changed dependencies, and when the component unmounts.

### 3. Why does an Effect sometimes run twice during development?

Strict Mode performs an extra setup and cleanup cycle to check whether cleanup is correct.

### 4. What causes an infinite Effect loop?

An Effect updates state that changes one of its dependencies, causing it to run again repeatedly.

### 5. Why does an object dependency trigger frequent Effect runs?

A newly created object has a different reference. React compares dependencies using `Object.is()`.

### 6. What is a stale closure?

A callback continues using values captured from an earlier render instead of the current values.

### 7. Should every function use useCallback?

No. Use it when stable identity has a concrete benefit; unnecessary memoization adds complexity.

### 8. Do custom hooks share state automatically?

No. Each call has independent hook state unless they deliberately subscribe to a shared source.

### 9. Can an Effect callback be async directly?

Avoid it: an async function returns a Promise, while React expects cleanup or no return. Define and call an async function inside the Effect.

### 10. Are memo and forwardRef hooks?

No. They are React APIs. React 19 allows function components to receive `ref` as a prop.

## Practice plan

1. Build an employee list with search and selection using `useState`.
2. Load employee details with `useEffect`, including cancellation and errors.
3. Add input focus with `useRef` and accessible labels with `useId`.
4. Share user or theme data through `useContext`.
5. Manage related cart or form actions with `useReducer`.
6. Measure unnecessary work before adding `useMemo` and `useCallback`.
7. Compare `useTransition`, `useDeferredValue`, and debouncing.
8. Build an Action-based form with `useActionState` and `useFormStatus`.
9. Add an optimistic interaction with failure handling.
10. Extract reusable logic into a custom hook.

## Official references

Use the individual hook reference pages for full caveats and version-specific details.

- [Built-in React hooks](https://react.dev/reference/react/hooks)
- [useState](https://react.dev/reference/react/useState)
- [useEffect](https://react.dev/reference/react/useEffect)
- [useContext](https://react.dev/reference/react/useContext)
- [useRef](https://react.dev/reference/react/useRef)
- [useReducer](https://react.dev/reference/react/useReducer)
- [useMemo](https://react.dev/reference/react/useMemo)
- [useCallback](https://react.dev/reference/react/useCallback)
- [useLayoutEffect](https://react.dev/reference/react/useLayoutEffect)
- [useImperativeHandle](https://react.dev/reference/react/useImperativeHandle)
- [useId](https://react.dev/reference/react/useId)
- [useTransition](https://react.dev/reference/react/useTransition)
- [useDeferredValue](https://react.dev/reference/react/useDeferredValue)
- [useSyncExternalStore](https://react.dev/reference/react/useSyncExternalStore)
- [useDebugValue](https://react.dev/reference/react/useDebugValue)
- [useInsertionEffect](https://react.dev/reference/react/useInsertionEffect)
- [useActionState](https://react.dev/reference/react/useActionState)
- [useOptimistic](https://react.dev/reference/react/useOptimistic)
- [useEffectEvent](https://react.dev/reference/react/useEffectEvent)
- [useFormStatus](https://react.dev/reference/react-dom/hooks/useFormStatus)
- [use API](https://react.dev/reference/react/use)
- [Rules of Hooks](https://react.dev/reference/rules/rules-of-hooks)
- [Reusing logic with custom hooks](https://react.dev/learn/reusing-logic-with-custom-hooks)
