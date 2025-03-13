# Reservation Web Application



## PostgreSQL Database

Open-source object-relational database system that offers high performance, scalability, and robust data management features. Almost too robust for my project, but I want to try this database and learn how it works. I used it also because of:

- Support for both relational and object-oriented data – efficiently handles complex data structures
- Transactional integrity (ACID-compliant) – atomicity, consistency, isolation, and durability
- Strong indexing support – enables fast searches
- JSON & JSONB support – for storing metadata about reservations
- Scalability – allows the application to grow without performance bottlenecks

So PostgreSQL should be fast, stable and secure.

## Database Structure  

### Rooms Table (Conference rooms)  

| Parameter   | Type         | Description                        |
|------------|-------------|--------------------------------------|
| `id`       | `BIGSERIAL`  | **Primary Key**. Unique room ID     |
| `name`     | `VARCHAR(255)` | Room name                         |
| `capacity` | `INT`        | Maximum number of people            |
| `equipment`| `TEXT[]`     | List of available equipment         |

### Reservations Table (Room reservations)  

| Parameter   | Type         | Description                           |
|------------|-------------|-----------------------------------------|
| `id`       | `BIGSERIAL`  | **Primary Key**. Unique reservation ID |
| `room_id`  | `BIGINT`     | **Foreign Key**. Linked to `rooms.id`  |
| `user_id`  | `BIGINT`     | **Foreign Key**. Linked to `users.id`  |
| `date`     | `DATE`       | Date of the reservation                |
| `start_time` | `TIME`     | Start time of the reservation          |
| `end_time` | `TIME`       | End time of the reservation            |
| `status`   | `VARCHAR(50)` | Reservation status (`pending`, `confirmed`, `canceled`) |

### Users Table (System users)  

| Parameter   | Type         | Description                          |
|------------|-------------|----------------------------------------|
| `id`       | `BIGSERIAL`  | **Primary Key**. Unique user ID       |
| `email`    | `VARCHAR(255) UNIQUE` | User email (login)           |
| `password` | `TEXT`       | Hashed password                       |
| `role`     | `VARCHAR(50)` | User role (`admin`, `user`)          |

- Future extensibility (e.g., notifications (when, how), pricing, AI recommendations)
