# Installation

## The Basics

For your platform, you will need to install Postgres, Elixir, and NodeJS. I installed the following versions:

* Postgres 9.6.2
* Elixir 1.4.2
* Node 7.6.0

Note: installing Elixir will also install Erlang for your platform. Elixir runs on the Erlang VM.

Once Elixir is installed, you need to make sure that Hex is installed. You can do that with this command:

* `mix local.hex`

You also need to install phoenix with this rather esoteric command:

* `mix archive.install https://github.com/phoenixframework/archives/raw/master/phoenix_new.ez`

With that, you have all the pieces in place. Note: You will eventually need to make sure that postgres is running in the background
on your machine.

## Configuring postgres

Phoenix, by default, assumes that it can connect to a Postgres database on the localhost using the account name `postgres` with the password `postgres`. You can login to your running postgres server using the `psql` command. Once inside `psql`, you can type `\?` to get a list of commands that you can use to configure your postgres server. You can change the password for the `postgres` user with the command `\password postgres` and then entering the desired password.

I'm only using this set-up since the server and database we're using will both be located behind a firewall and used only internally. Our database's ports will not be exposed to the public internet.

