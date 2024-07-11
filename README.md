# Mini Amazon

## Project Overview

This is the final project for Duke University ECE 568: Engineering Robust Server Software course. The project involves developing an online store system called "Mini Amazon." The system needs to interoperate with UPS systems as part of the interoperability group (IG) consisting of two Amazon groups and two UPS groups.

## Authors

- **Haoyuan Geng** - Backend Development
- **Zichun Wang** - Frontend Development

## Contact Information

- Haoyuan Geng: [steven.h.geng@gmail.com](mailto:steven.h.geng@gmail.com)
- Zichun Wang: [zichunwang733@gmail.com](mailto:zichunwang733@gmail.com)

## Project Description

For this project, you will either be doing “mini-Amazon” (an online store) or “mini-UPS” (a shipping website). If you are doing Amazon, you will have to make your system work with the UPS systems in your interoperability group (IG)—2 groups doing Amazon and 2 groups doing UPS.

### The “World”

Since you won’t have access to real warehouses and trucks, your code will interact with a simulated world provided for you. You will connect to the simulation server (port 12345 for UPS, port 23456 for Amazon), and send commands and receive notifications.

The messages you can send and receive are in the .proto files (amazon.proto and ups.proto) that will be provided. Notice that all messages either start with A or U to indicate which part they belong to.

### Basic Workflow

The basic flow is that you send an A/UConnect message with the worldid that you want and receive an A/UConnected response. Note only ONE Amazon and ONE UPS is allowed to connect to a world at the same. Upon successful connection, the result string in A/UConnected will be “connected!”, otherwise it will be an error message starting with “error:”. Make sure your result string is “connected!” before proceeding to any further actions. Once you have received this response, you may send A/UCommands and receive A/Responses. You should not send any other message, nor expect to receive any – all of the details are embedded in the A/UCommands/Responses.

### Commands and Responses

#### Amazon Commands

- **buy**: Request more products to be delivered to a warehouse.
- **topack**: Pack a shipment for delivery.
- **load**: Load a shipment onto a truck.
- **queries**: Ask the status of a package.

#### Amazon Responses

- **arrived**: Notification that your orders have arrived.
- **ready**: Notification that packing is complete.
- **loaded**: Notification that a shipment is loaded onto a truck.
- **packagestatus**: Status of the package.
- **error**: Indicates a failure to meet command requirements.

#### UPS Commands

- **deliveries**: Send a truck to deliver a package.
- **pickups**: Send a truck to a warehouse to pick up a package.
- **queries**: Ask the status of a truck.

#### UPS Responses

- **completions**: Notification that a truck has reached its destination or completed deliveries.
- **delivered**: Notification that a package is delivered.
- **truckstatus**: Status of a truck.
- **error**: Indicates a failure to meet command requirements.

### Additional Information

- **Simulation Speed**: You can adjust the simulation speed for testing purposes.
- **Acknowledgement Mechanism**: Implement ack numbers to avoid losing in-flight messages.
- **Google Protocol Buffer Message Format**: Use GPB for message formatting and communication.

### Features to Implement

1. **Basic Functionality**: Purchase an item and ensure its delivery.
2. **Useful Features**:
   - Searchable catalog of products.
   - Order status checking.
   - Specify delivery address.
   - Provide tracking number.
3. **Product Differentiation**: Add unique features to make your product stand out.

### Running the Project

Ensure the project can be run with `docker-compose up`. Separate Docker stacks for Amazon and UPS should be used, with appropriate configurations for the world server connection.

## Conclusion

This project aims to develop a robust and functional online store system that can effectively interoperate with a shipping system, demonstrating skills in backend and frontend development, as well as system integration.

