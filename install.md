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
