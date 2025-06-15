# Sequence Diagram: Car Rental Billing Process
![alt text](<Sequence Diagram.jpg>)
This sequence diagram illustrates the interactions between different components involved in a car rental billing process. The main actors and objects include:

- **Desk Officer**
- **Billing System**
- **FromRentCar**
- **RentCarController**
- **Car**
- **Customer**
- **RentalRecord**
- **BillingInterface**

## Flow Description

1. **Desk Officer → Billing System: EnterDetails**
   - The desk officer inputs the customer and rental details into the billing system.

2. **Billing System → FromRentCar: validate**
   - The system validates the entered rental details.

3. **FromRentCar → RentCarController: rentcar**
   - The system proceeds to initiate the car rental process.

4. **RentCarController → Car: findcar**
   - The controller attempts to locate an available car.

5. **RentCarController → Car: setStatus("rented")**
   - Once found, the car’s status is updated to `"rented"`.

6. **RentCarController → Customer: Message1**
   - A message is sent to the customer confirming the rental.

7. **RentCarController → RentalRecord: create**
   - A rental record is created for this transaction.

8. **RentCarController → BillingInterface: billCustomer**
   - The billing process is initiated.

9. **BillingInterface → Billing System: billCustomer**
   - The billing interface requests the billing system to bill the customer.

10. **Billing System → Desk Officer: displayCompletionMsg**
    - A completion message is displayed to the desk officer indicating successful billing.

11. **BillingInterface → Car: setStatus("Available")**
    - If necessary, the car’s status is reset to `"Available"` (e.g., if the rental is canceled or completed).

12. **BillingInterface → RentalRecord: Cancel**
    - The rental record may be canceled if an issue occurs.

13. **Billing System → Desk Officer: displayErrorMsg**
    - If any error occurs during the process, an error message is displayed to the desk officer.

## Summary

The diagram models the sequence of messages exchanged between the objects in a car rental system. It ensures that validation, rental, billing, and error handling are managed systematically. Each component plays a role in confirming that a car is successfully rented, billed, and its status is appropriately updated.
