# Function parameter handle or paremeter error control

- Example 1: Just checking if all arguments were passed / defined.

```

const required = (name) => {
  console.warn(`Parameter is required and its shuld be type of ${name}`);
};
// use of this
function add(a = required("number"), b = required("number")) {
  return a + b;
}

```

#### Or

```

function add(number1, number2) {
  if (arguments.length < 2) {
    console.warn("Missing arguments");
  }
  return number1 + number2;
}

```

#### Or

```

function add(number1, number2) {
  if (typeof number1 === "undefined") {
    console.warn("First argument is missing / not defined");
  }
  if (typeof number2 === "undefined") {
    console.warn("Second argument is missing / not defined");
  }
  return number1 + number2;
}

```

- Example 2: make sure each argument is correct type.

```

function add(number1, number2) {
  if (isNaN(number1)) {
    console.warn("First argument is not a number");
  }
  if (isNaN(number2)) {
    console.warn("Second argument is not a number");
  }
  return number1 + number2;
}

```

- Example 3: make sure each argument is defined and of correct type

```

function add(number1, number2) {
  if (typeof number1 === "undefined" || isNaN(number1)) {
    console.warn("First argument is missing / not defined");
  }
  if (typeof number2 === "undefined" || isNaN(number2)) {
    throw new TypeError("Second argument is missing / not defined");
  }

  return number1 + number2;
}

```

- Example 4: create extarnal function for make sure each argument is defined and of correct type

```

function handleError() {
  for (let i = 0; i < arguments.length || arguments.length == 0; i++) {
    if (arguments[i] === undefined) {
      return "No argument, This is required";
    } else if (typeof arguments[i] != "number") {
      return "Please Give me Number";
    } else if (arguments[i] < 0) {
      return "Please Give Positive Number";
    }
  }
  return "noError";
}

```
