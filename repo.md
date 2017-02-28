# Working with the Database

When applying changes that will effect the database, you will typically follow a process like this:

1. Make a change to a model
2. Use `mix ecto.gen.migration <name_of_migration>` to create a migration file.
3. Edit the migration file to reflect the change.
4. Apply the migration by using `mix ecto.migrate`

## Example

### Create a model

```
defmodule Jade.Project do
  use Jade.Web, :model

  schema "projects" do
    field :faculty_name, :string
    field :faculty_phone, :string
    field :faculty_email, :string
    timestamps
  end
end
```

### Create a migration

```
$ mix ecto.gen.migration create_project

* creating priv/repo/migrations
* creating priv/repo/migrations/20170228165458_create_project.exs
```

Note: the file that is generated here is empty.

### Edit the migration file

Now, we add code to the migration file that implements the change made in the model. In this case, we are simply creating
the Project model from scratch and so our migration reflects that. (In future migrations, we might add, delete,
or alter columns in the Project model and so then our migration file would have to issue the commands that make those
changes at the database level.)

```
defmodule Jade.Repo.Migrations.CreateProject do
  use Ecto.Migration

  def change do
    create table(:projects) do
      add :faculty_name, :string
      add :faculty_phone, :string
      add :faculty_email, :string

      timestamps
    end
  end
end
```

### Apply the Migration

Note: this step requires that your database server is running.

```
$ mix ecto.migrate

10:50:37.121 [info]  == Running Jade.Repo.Migrations.CreateProject.change/0 forward
10:50:37.121 [info]  create table projects
10:50:37.127 [info]  == Migrated in 0.0s
```

If you made a mistake and you need to go back and change something, you can use:

```
$ mix ecto.rollback

10:49:42.883 [info]  == Running Jade.Repo.Migrations.CreateProject.change/0 backward
10:49:42.884 [info]  drop table projects
10:49:42.888 [info]  == Migrated in 0.0s
```
ecto.rollback will do what it can to reverse the changes of the most recent migration.

This is very handy, since you can prototype and test a new model, migrating up and down, until you have the whole thing
the way you like and end with a single migration that includes everything the model was supposed to have from the start.
