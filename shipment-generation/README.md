

### Problem

When a seller sends inventory to Deliverr, we need to decide what warehouses will receive the inventory. Let's say we 
have a total of 16 warehouses, and we want each "inbound" to stock four warehouses. Ideally we choose four warehouses 
that are distributed geographically in such a way as to match up with the expected geographical demand for the product(s).

Write code to generate the inbound shipments. Input includes:
  - Sixteen warehouses and their zip codes:
    ```
    { [{ "warehouseId": "WH1", "zip": "01100" }, { "warehouseId": "WH2", "zip":  "34028" }, ...,
       { "warehouseId": "WH16", "zip": "94102" }] }
    ```
  - A shipping plan, consisting of products (identified by stock-keeping unit, aka SKU) and the quantities to be shipped:
    ```
    { "D11111": 500, "D11112": 300 }    
    ```
  - A "demand map" that for each product provides a geographic mapping of zip code to historical order quantity:
    ```
    { "D11111": { "01000":  190, "01001":  7, ..., "99999":  22}, ... }
    ``` 
  - A function to calculate the distance between zip codes
    ```typescript
     function distance(zip1: string, zip2: string): number
    ```
  
Your function needs to generate and output four shipments. Each shipment will be sent to one of the four
warehouses and will consist of the quantity of products to be sent to each warehouse.

  - Example output
    ```
    [{ "shipmentId": 1, "warehouseId": "WH1", "products": {"D11111": 100, "D11112": 50 } },
     ..., { "shipmentId": 4, "warehouseId": "WH12", "products": {"D11111": 200, "D11112": 60 } }]
    ```

Use any language of your choice to write the solution (internally we use Typescript/Javascript, Python, and some 
Java). 
