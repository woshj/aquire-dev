# Aquire Digital Dev Test - Josh Wainwright

## Setup

1. After setting up the app run `php artisan app:catch-em-all $limit $offset` by default the `limit` is `151` and the `offset` is `0`.
2. Once this has been ran you should see the `pokemon` table has been populated by a list of pokemon which contain an `id` and a json `data` field which contains all the data related to the pokemon
3. After serving the application navigate to `http://localhost/api/pokemon` to view the list of pokemon
    - From here you can click on an individual pokemon to view and subsequently edit an individual record.
    - The table currently defaults to a pagination value of 6 but this could be increased by a drop down in a production environment

## Notes

- Unfortunately I ran out of time to create update and delete methods.
  - To create the update method I would've returned the edited fields as part of the `$request` and formatted the data to match the `JSON object` stored in the database before using an eloquent save method to save the record
  - As for the delete methods I would go back and add a soft delete column to the database migration file. this would allow me to delete records without removing data we may need later. The data could then be pruned on a scheduled task set at a suitable interval.
- I also ran a breeze starter kit command thinking it installs the necessary dependencies to use `Inertia` and such but it also created a default login system, I have done by best to remove this unwanted code but if you see anything weird lying around it's most likely from this hiccup.
- I also developed this on a windows machined so used `Docker` and `WSL2` (windows subsystem for linux) to create my local development environment. For some strange reason this means when you run your `migrations` you need to set your `DBHOST` environment variable to `localhost` to avoid an error related to not having access to the `DB`. Annoyingly this needs to be set back to `mysql` when viewing the application.
    ```

    LOCATION: \aquire-dev-test\.env

    # use localhost for running commands
    # use mysql for everything else
    DB_HOST=mysql
    ```
- I also used pages instead of components for this test as you noted the front end was less important but in a production environment I would have split these pages down into multiple components to create more concise code with better readability
- I chose to use `tailwindcss` for styling as i haven't used it before and actually really enjoyed the process although without an auto inline style collapse extension it really clutters up the code in the vue components