 # Supabase Music API

This repository contains several functions that interact with a music application using **Supabase** as the backend. The functions handle tasks such as retrieving songs, liked songs, and product prices for users. All functions use Supabase's `createServerComponentClient` for communication with the database.

## Functions Overview

### 1. **getActiveProductwithPrices**
   - Retrieves active products along with their associated active prices from the database.
   - Filters for products and prices that are marked as active and orders them by metadata and unit amount.
   
   ```typescript
   const getActiveProductwithPrices = async (): Promise<ProductWithPrice[]> => {
     const supabase = createServerComponentClient({ cookies });
     
     const { data, error } = await supabase
       .from('products')
       .select('*, prices(*)')
       .eq('active', true)
       .eq('prices.active', true)
       .order('metadata->index')
       .order('unit_amount', { foreignTable: 'prices' });

     if (error) {
       console.log(error);
     }

     return (data as any) || [];
   };
