## Events Module

Events module allows us to work with events in NodeJs. An event is a action or an occurrence that has happened in our application that we can respond to. Using events module we can create and dispatch our custom events and respond to them.

Example of Pizza Ordering Scenario

```javascript
const EventEmitter = require("node:events");

const emitter = new EventEmitter();

emitter.on("order-pizza", (name, size) => {
  console.log(`Order received! baking a ${size} ${name} pizza`);
});

emitter.emit("order-pizza", "cheese", "large");
```

The Events module returns a emitter class that we can instantiate to create a emitter object. Using the emitter object we can dispatch and respond to events.

To dispatch a event we can use the `emit()`. First argument for emit is the name of the event and the following arguments are data that will be passed on to the listeners. When a event occurs node will automatically call the listener and pass the corresponding event listeners.

To respond to event a event we can use the `on()`. First argument for on is the name to the event and following is a callback function that will respond to the event.

### Building on top of the Event Emitter.

**pizzaShop.js**

```javascript
const EventEmitter = require("node:events");

export class PizzaShop extends EventEmitter {
  constructor() {
    super();
    this.orderNumber = 0;
  }

  order(name, size) {
    this.orderNumber++;
    this.emit("order", name, size);
  }

  displayOrderNumber() {
    console.log(`Current order number is ${this.orderNumber}`);
  }
}
```

**drink-machine.js**

```javascript
const EventEmitter = require("node:events");

export class DrinkMachine {
  serveDrink(size) {
    if (size === "large") {
      console.log("serving complementary drink");
    }
  }
}
```

**index.js**

```javascript
import { PizzaShop } from "./pizzaShop";
import { DrinkMachine } from "./drink-machine";

const shop = new PizzaShop();
const drinkMachine = new DrinkMachine();

shop.on("order", (name, size) => {
  console.log(`new order for ${size} ${name} pizza`);
  drinkMachine.serveDrink(size);
  shop.displayOrderNumber();
});

shop.order("cheese", "small");
```

> Take Away
>
> Using events we use different modules together without tightly coupling them.
> Our local modules can extend form Event emitter allowing them to emit and respond their own custom events.

