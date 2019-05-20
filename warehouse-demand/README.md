

### Problem

When a seller sends inventory to Deliverr, we need to decide what warehouses will receive the inventory. Ideally we 
place the product near areas where customers will buy it. There are three inputs:
  - A mapping of zip code to historical order quantity
    ```
    { "01000":  190, "01001":  7, ..., "99999":  22}
    ``` 
  - Warehouse zip codes
    ```
    ["01100", "34028", ..., "94102"]
    ```
  - A function to calculate the distance between zip codes
    ```typescript
     function distance(zip1: string, zip2: string): number
    ```
  
Your function needs to calculate and output the percentage of demand to be met by each warehouse.

  - Example output
    ```
    { "01100": 33.333, "34028": 22.01, ..., "94102": 12.987 }
    ```

You can use any language of your choice to write the solution (internally we use Typescript/Javascript, Python, and some 
Java). 
