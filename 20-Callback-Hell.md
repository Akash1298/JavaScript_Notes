# Callback

  1. Good Part of callback - Callback are super important while writing asynchronous code in JS
  2. Bad Part of Callback - Using callback we can face issue:
     - Callback Hell
     - Inversion of control

## Callback Hell

### 🛒 e-Commerce web app situation

Assume a scenario of e-Commerce web, where one user is placing order, he has added items like, shoes, pants and kurta in cart and now he is placing order. So in backend the situation could look something like this.

- When a user creates an order, the system first verifies and completes the order creation.
- On successful order creation, the system then proceeds to the payment process.
- After payment is completed, it moves forward to display the order summary to the user.
- Finally, once everything is done, the system updates the user's wallet (e.g., deducting balance or applying rewards).

```js
api.createOrder(cart, function () {
  api.proceedToPayment(function () {
    api.showOrderSummary(function () {
      api.updateWallet();
    });
  });
});
// 💡 Callback Hell
```

When we have a large codebase and multiple apis and have dependency on each other, then we fall into callback hell.
These codes are tough to maintain.
These callback hell structure is also known as **Pyramid of Doom**.

## Inversion of Control

  - Inversion of control is like that you lose the control of code when we are using callback.

Let's understand with the help of example code and comments:

```js
api.createOrder(cart, function () {
  api.proceedToPayment();
});
```
- So over here, we are creating a order and then we are blindly trusting `createOrder` to call `proceedToPayment`.
- It is risky, as `proceedToPayment` is important part of code and we are blindly trusting `createOrder` to call it and handle it.
- When we pass a function as a callback, basically we are dependant on our parent function that it is his responsibility to run that function. This is called `inversion of control` because we are dependant on that function. What if parent function stopped working, what if it was developed by another programmer or callback runs two times or never run at all.
- In next session, we will see how we can fix such problems.
- Async programming in JavaScript exists because callback exits.
