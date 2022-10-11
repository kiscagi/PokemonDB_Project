# PokemonDB_Project

Pokemon Database Project

My semester project is creating a database to explore the relationships between Pokémon in the Pokémon universe and Non-Player Characters (NPC). 
I used the following data sets and databases found on Kaggle:

https://www.kaggle.com/datasets/lrcusack/pokemontrainers

Includes Trainer ID no. and Name in table Trainer
Includes Pokémon, Trainer ID, Name, level, and type(s), hp, max hp, attack, defense
sqlite3 database converted to csv, then imported in to a pandas dataframe to insert into Tables

https://www.kaggle.com/datasets/rounakbanik/pokemon

Includes name, Japanese name, ID no., % male, type(s), height, weight, capture rate, egg steps, experience, happiness, hp, attack, defense, special attack, special defense, speed, generation, and islegendary.
csv format, imported to a pandas dataframe to insert into Tables

Platforms:

I am using the CSPB MySQL Database to host my data.
I am using a Jupyter Notebook with sql magic to create my queries, tables, and triggers. The existing data is in a csv file and sqlite database, downloaded locally.
I read and parse this data in order using a SQLAlchemy connection to populate my tables.

Tables, Relationships and Foreign Keys:

Types: 18 possible types
Generations 8
Trainer: ID, Name
memberOf relationship table: Trainer ID (foreign key), Pokemon name(foreign key) Because the relationship between Pokémon and Trainers is many-to-many, I created a table for this relationship
Pokémon: Pokedex #, Name, generation(foreign key), type 1 (foreign key), type 2(foreign key), hp, attack, defense, sp_attack, sp_defense, speed

Multiple Joins:

memberOf to Trainer
memberOf to Pokemon

Grouping:
grouping trainers by ID and name in order to count duplicate pokemon

Constraints:

Pokémon must have at minimum one type
Generation much be between 1 and 7
Type must be in the existing type list
Pokemon must have an existing, unique name and pokedex #
Pokemon must be part of a generation
Trainer ID is existing, not null

Triggers for updates and deletions:

if a Pokemon is deleted, the memberOf data pertaining to that Pokemon is deleted
If a Trainer is deleted, the memeberOf data pertaining to that Trainer is deleted
If a Pokémon type is deleted, all Pokémon of that type are deleted.
If a generation is deleted, Pokémon of those generations are deleted as well

Queries:

The motivation for this project is to conduct queries in order to see pokemon teams and fun information pertaining to those teams, such as trainers with duplicate pokemon on their team or trainers that have mostly one type of pokemon on their team.
