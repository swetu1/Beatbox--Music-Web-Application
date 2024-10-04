 # Supabase Music API

This repository contains several functions that interact with a music application using **Supabase** as the backend. The functions handle tasks such as retrieving songs, liked songs, and product prices for users. All functions use Supabase's `createServerComponentClient` for communication with the database.

## Functions Overview



### 1. **getActiveProductwithPrices**
This function fetches active products and their associated active prices from the Supabase database. It filters for products and prices that are marked as active and orders them based on the metadata's index and the unit amount.

### 2. **getLikedSongs**
This function retrieves a list of songs that the currently authenticated user has liked. It fetches data from the `liked_songs` table and joins it with the `songs` table to get detailed song information. The results are ordered by the creation date in descending order, showing the most recently liked songs first.

### 3. **getSongs**
This function fetches all songs available in the `songs` table. It orders the songs by their creation date, with the most recent songs appearing first. This function is useful for displaying all available songs in the application.

### 4. **getSongsbyTitle**
This function allows users to search for songs by title. If a title is provided, it retrieves songs that contain the specified title in a case-insensitive manner. If no title is given, it defaults to fetching all songs. The results are ordered by creation date, showing the most recently added songs first.

### 5. **getSongsbyUserID**
This function retrieves songs specifically associated with the currently authenticated user. It first fetches the user's session to obtain the user ID and then queries the `songs` table for songs that belong to that user. The results are ordered by creation date in descending order, ensuring that the most recently created songs are displayed first.
