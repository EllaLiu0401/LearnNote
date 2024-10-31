## Vitest

## Testing Components Wrapped in a Provider

### Entering Text Input: Subtotals

- make sure total starts out at $0.00.
- update vanilla scoops to 1, and check subtotal.
- updata chocolate scoops to 2 and check subtotal

Tips: `async/await`, `user.clear()`, `user.type()`

```Js
import { render, screen } from "@testing-library/react";
import userEvent from "@testing-library/user-event";
import Options from "../Options";

test("uodate scoop subtotal when scoops change", async () => {
  const user = userEvent.setup();
  render(<Options optionType="scoopes" />);

  // make sure total starts out at $0.00
  const scoopsSubtotal = screen.getByText("Scoops total: $", { exact: false }); // exact: false: partial match
  expect(scoopsSubtotal).toHaveTextContent("0.00");
  // update vanilla scoops to 1, and check subtotal
  const vanillaInput = await screen.findByRole("spinbutton", {
    name: "Vanilla",
  }); // need to use await: not going to populate untill option get from server

  await user.clear(); // clear the value of an input field https://testing-library.com/docs/user-event/utility
  await user.type(vanillaInput, "1"); // type the new value
  expect(scoopsSubtotal).toHaveTextContent("2.00");
  // updata chocolate scoops to 2 and check subtotal
  const chocolateInput = await screen.findByRole("spinbutton", {
    name: "Chocoloate",
  });
  await user.clear();
  await user.type(chocolateInput, "2");
  expect(scoopsSubtotal).toHaveTextContent("6.00");
});

```

### React Code: Order Details Context

- Used `createContext()` to get the global data.
- Created `OrderDetailsProvider()` to update item, reset item and calculate value.

### React Code: Use Context to display scopps subtotal

- Added scoop options component.
- Implemented whole summary page component.

### Review of Tests

- `getByText` to find total.
  - `exact` option set to `false`.
- number inputs:
  - `await` and `findBy`.
  - `spinbutton` role.
  - `userEvent.clear` to clear existing text.
  - `userEvent.type` to enter number.
- `wrapper` option to `render` to apply context provider.
- Redefine Testing Library `render` to access universally.

### How to find element

- `*byRole` and regular expression for `name` option.
- `*byText` and `{exact: false}`
