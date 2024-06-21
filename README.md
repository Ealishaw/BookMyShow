# Book My Show

The tables you created represent a schema for a movie ticket booking system. Here's how these tables would be used in a typical flow:

### Flow Explanation:

1. **Movie Table**:
   - This table stores information about movies available in the system. Each movie has an ID, name, IMDb rating, category, genre, release date, duration, actor names, actress names, and a theme photo path.
   - When a new movie is released, an entry is made in this table.

2. **Theatre Table**:
   - This table stores information about theatres. Each theatre has an ID, name, and city.
   - When a new theatre is added to the system, an entry is made in this table.

3. **Show Table**:
   - This table links movies to theatres and specifies the show times.
   - Each entry includes a time, theatre ID, and movie ID, forming a composite primary key.
   - When a theatre schedules a new show for a movie, an entry is made in this table.

4. **Ticket Table**:
   - This table stores information about tickets purchased by users. Each ticket has an ID, username, number of seats, show time, theatre ID, and movie ID.
   - When a user books a ticket, an entry is made in this table.

5. **Seat Table**:
   - This table stores information about individual seats for each show. Each seat has a unique number, show time, theatre ID, movie ID, ticket ID (nullable), and availability status.
   - When a seat is booked as part of a ticket purchase, the ticket ID and availability status are updated in this table.

6. **ShowMovieModel Table**:
   - This table stores combined information from the Show and Movie tables, useful for querying and displaying show information alongside movie details.
   - Each entry includes a unique ID, show time, theatre ID, movie ID, and movie name.

### Example Flow:

1. **Admin Adds a Movie**:
   - The admin adds a new movie to the `Movie` table.

2. **Admin Adds a Theatre**:
   - The admin adds a new theatre to the `Theatre` table.

3. **Admin Schedules a Show**:
   - The admin schedules a new show by inserting a record into the `Show` table, linking a movie to a theatre with a specific show time.

4. **User Browses Shows**:
   - The user queries the `ShowMovieModel` table to see all available shows along with movie names.
   - The system joins the `Show` and `Movie` tables to provide this information.

5. **User Books a Ticket**:
   - The user selects a show and books a ticket.
   - The system inserts a new record into the `Ticket` table with the user's information and the selected show details.

6. **System Updates Seats**:
   - When a ticket is booked, the system updates the `Seat` table, linking the booked seats to the ticket ID and marking them as "Booked".
   - For example, if the user books 2 seats for a show, two corresponding entries in the `Seat` table are updated with the ticket ID and availability status.

### Practical Example:

1. **Adding Data**:
   - A new movie "Inception" is added to the `Movie` table.
   - A new theatre "Regal Cinemas" is added to the `Theatre` table.
   - A new show for "Inception" at "Regal Cinemas" at 6 PM is scheduled in the `Show` table.

2. **Querying Shows**:
   - A user queries the `ShowMovieModel` table to find shows. The system displays "Inception" at "Regal Cinemas" at 6 PM.

3. **Booking a Ticket**:
   - The user books 2 seats for the 6 PM show of "Inception".
   - The system inserts a record in the `Ticket` table with the user's name, number of seats, show time, theatre ID, and movie ID.
   - The system updates the `Seat` table, marking two seats as "Booked" and linking them to the new ticket ID.

By maintaining this relational structure, the system ensures data integrity and allows efficient querying and management of movie shows, theatres, tickets, and seats.
