

### Problem

When a seller sends inventory to Deliverr, we need to decide what warehouses will receive the inventory. Ideally we 
place the product near areas where customers will buy it. There are three inputs:
  - For each product (identified by stock-keeping unit, aka SKU), a mapping of zip code to historical order quantity
    ```
    { "D12345": { "01000":  190, "01001":  7, ..., "99999":  22} }
    ``` 
  - Warehouse zip codes
    ```
    ["01100", "34028", "60491", "94102"]
    ```
  - A function to calculate the distance between zip codes
    ```typescript
     function distance(zip1: string, zip2: string): number
    ```
  
Your function needs to calculate and output the percentage of demand to be met by each warehouse.

  - Example output
    ```
    { "D12345": { "01100": 0.3333, "34028": 0.2201, "60491": 0.18, "94102": 0.27 } }
    ```

Use any language of your choice to write the solution (internally we use Typescript/Javascript, Python, and some 
Java). 
