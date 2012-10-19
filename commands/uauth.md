Request for authentication in a password-protected Redis server.
Redis can be instructed to require a password before allowing clients to execute
commands. This is done using one or more `requireupass` directive in the
configuration file.

After authenticating with this command, the session is placed in their own
database and may not SELECT a different database. The session is also not able
to execute admin or other destructive commands (i.e.: FLUSHALL, INFO, and
SLOWLOG).

If `password` matches the password in the configuration file, the server replies
with the `OK` status code and starts accepting commands.
Otherwise, an error is returned and the clients needs to try a new password.

**Note**: because of the high performance nature of Redis, it is possible to try
a lot of passwords in parallel in very short time, so make sure to generate a
strong and very long password so that this attack is infeasible.

@return

@status-reply
