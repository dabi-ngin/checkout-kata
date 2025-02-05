# Checkout Kata

Implement the code for a checkout system that handles pricing schemes such as "pineapples cost 50, three pineapples cost 130."

Implement the code for a supermarket checkout that calculates the total price of a number of items. In a normal supermarket, things are identified using Stock Keeping Units, or SKUs. In our store, we’ll use individual letters of the alphabet (A, B, C, and so on). Our goods are priced individually. In addition, some items are multi-priced: buy n of them, and they’ll cost you y pence. For example, item A might cost 50 individually, but this week we have a special offer: buy three As and they’ll cost you 130. In fact the prices are:

| SKU  | Unit Price | Special Price |
| ---- | ---------- | ------------- |
| A    | 50         | 3 for 130     |
| B    | 30         | 2 for 45      |
| C    | 20         |               |
| D    | 15         |               |

The checkout accepts items in any order, so that if we scan a B, an A, and another B, we’ll recognize the two Bs and price them at 45 (for a total price so far of 95). **The pricing changes frequently, so pricing should be independent of the checkout.**

The interface to the checkout could look like:

```cs
interface ICheckout
{
    void Scan(string item);
    int GetTotalPrice();
}
```



### My Implementation Notes

Hey, had fun doing this one, hope the implementation is clear and covers all bases. Small note to the reviewer, I decided to go ahead and make the pricing rules config driven via a JSON file even though it wasn't in scope as this would make this service a little more flexible given some pricing rule needed to be updated in prodcution, as it'd save the hassle of getting an entire new change through ci/cd, QA, test, and deployment if there were any issues. Though, of course, this would still need to be a change that was deployed alongside a new version once this live issues was resolved and we had the breathing room.

Could have hardcoded those values for the sake of this demo but preferred this option as gives a little more flexibility.
