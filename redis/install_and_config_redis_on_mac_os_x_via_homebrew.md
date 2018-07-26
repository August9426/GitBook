# Install and config Redis on Mac OS X via Homebrew

By using [Homebrew](http://brew.sh/), you greatly reduce the cost of setting up and configuring the development environment on Mac OS X.

## Install [Redis](http://redis.io/)

```text
brew install redis
```

> _After installation, you will see some notification about some caveats on configuring. Just leave it and continue to following some tasks on this article._

## Launch Redis on computer starts.

```text
ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
```

## Start Redis server via `launchctl`.

```text
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

## Start Redis server using configuration file.

```text
redis-server /usr/local/etc/redis.conf
```

## Stop Redis on autostart on computer start.

```text
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

## Location of Redis configuration file.

```text
/usr/local/etc/redis.conf
```

## Uninstall Redis and its files.

```text
brew uninstall redis
rm ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

## Get Redis package information.

```text
brew info redis
```

## Test if Redis server is running.

```text
redis-cli ping
```

> _If it replies_ `**PONG**`_, then it’s good to go!_

