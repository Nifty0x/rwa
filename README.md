# Real-World Assets (RWAs)
This dashboard is built to track and analyze the development of tokenization on public blockchains.

### Setup

Run `pull_from_dune.py` to bring in all queries into `/query_{id}.sql` files within the `/queries` folder. Directions to setup and run this python script are below.

### Updating Queries or CSV Tables

1. Make any changes you need to directly in the repo. Any time you push a commit to MAIN branch, `push_to_dune.py` will save your changes into Dune directly. You can run this manually too if you want.

2. For CSVs, update the files in the `/uploads` folder. `upload_to_dune.py` will run on commit, or can be run manually. The table name in Dune will be `dune.team_name.dataset_<filename>`.

---

### Query Management Scripts

You'll need python and pip installed to run the script commands. If you don't have a package manager set up, then use either [conda](https://www.anaconda.com/download) or [poetry](https://python-poetry.org/) . Then install the required packages:

```
pip install -r requirements.txt
```

| Script | Action | Command |
|---|-----------------------------------------------------------------------------------------------------------------------------------------------------------|---|
| `pull_from_dune.py` | updates/adds queries to repo based on ids in `queries.yml` | `python scripts/pull_from_dune.py` |
| `push_to_dune.py` | updates queries to Dune based on files in `/queries` folder | `python scripts/push_to_dune.py` |
| `preview_query.py` | gives the first 20 rows of results by running a query from your `/queries` folder. Specify the id. This uses Dune API credits | `python scripts/preview_query.py 2615782` |
| `upload_to_dune.py` | uploads/updates any tables from your `/uploads` folder. Must be in CSV format, and under 200MB. | `python scripts/upload_to_dune.py` |

---

### Things to be aware of

💡: Names of queries are pulled into the file name the first time `pull_from_dune.py` is run. Changing the file name in app or in folder will not affect each other (they aren't synced). **Make sure you leave the `___id.sql` at the end of the file, otherwise the scripts will break!**

🟧: Make sure to leave in the comment `-- already part of a query repo` at the top of your file. This will hopefully help prevent others from using it in more than one repo.

🔒: Queries must be owned by the team the API key was created under - otherwise you won't be able to update them from the repo.

➕: If you want to add a query, add it in Dune app first then pull the query id (from URL `dune.com/queries/{id}/other_stuff`) into `queries.yml`

🛑: If you accidently merge a PR or push a commit that messes up your query in Dune, you can roll back any changes using [query version history](https://dune.com/docs/app/query-editor/version-history).

---

### For Contributors

I've set up four types of issues right now:
- `bugs`: This is for data quality issues like miscalculations or broken queries.
- `chart improvements`: This is for suggesting improvements to the visualizations.
- `query improvements`: This is for suggesting improvements to the query itself, such as adding an extra column or table that enhances the results.
- `generic questions`: This is a catch all for other questions or suggestions you may have about the dashboard.

If you want to contribute, either start an issue or go directly into making a PR (using the same labels as above). Once the PR is merged, the queries will get updated in the frontend.

### Acknowledgments

The data is based on collab with @fillif, @sqrr-research and the dedicated members of the 21.co research team Eli, Adrian, Karim, Carlos, and Tom, whose unwavering commitment and insights were crucial in the creation of this dashboard.

