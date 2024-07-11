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

### Backend

The backend of the Mini Amazon system is implemented in Java and uses Gradle for build automation and project management. It handles core logic, database operations, and communication with both the simulated world and the mini UPS system via Sockets.

### Frontend

The frontend of the Mini Amazon system is built using the Django framework. It provides a web interface for customers to browse products, place orders, and track shipments.

### Database

We use PostgreSQL RDBMS and access it via JDBC.

### The “World”

Since we won’t have access to real warehouses and trucks, our code will interact with a simulated world provided for us. We will connect to the simulation server, and send commands and receive notifications.

The messages we can send and receive are in the .proto files (amazon.proto and ups.proto). Notice that all messages either start with A or U to indicate which part they belong to.

### Basic Workflow

1. Amazon and UPS connect to the same world
2. Amazon receives a purchase request
3. Amazon notifies UPS that a vehicle is needed and notifies the world to pack the goods
4. UPS informs Amazon when the vehicle arrives and the world informs Amazon when the goods are packed
5. Amazon notifies the world to start loading
6. The world informs Amazon that loading is complete
7. Amazon notifies UPS to start delivery
8. UPS informs Amazon that the delivery is complete

We independently designed the communication protocol between Amazon and UPS, which can be found in backend/app/src/main/resources/amazon_ups.proto.

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

## Conclusion

This project aims to develop a robust and functional online store system that can effectively interoperate with a shipping system, demonstrating skills in backend and frontend development, as well as system integration.

