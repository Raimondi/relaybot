**About**

RelayBot is a python IRC bot written using the Twisted framework. A Relay-bot is a IRC bot that is designed to relay messages from one network to another, allowing two users in different channels on different networks to talk (Providing the bot is in both channels).

**Features**

**Multiple server connections**

  * RelayBot can join any number of external IRC servers and channels and relay messages back. Each network joined is represented as a new IRC user (E.g "freenode" or "rizon") that relays messages in that network to the main channel.

**Managed through IRC**

  * RelayBot is controlled 100% through IRC commands sent to the "RelayManager".

**Portable**

  * RelayBot runs anywhere Python 2.5.5 runs (Linix, Windows, Mac).

**Secure**

  * Only users given access can add/remove networks and channels.

**Fast**

  * RelayBot runs on top of the Twisted framework, and as such it uses no threads and purely asynchronous code. Twisted can scale to thousands of connections with hardly any noticeable load.


**How to use:**

**Downloading**

Download and install [Python 2.5.5](http://www.python.org/download/releases/2.5.5/) (Or [2.5.4](http://www.python.org/download/releases/2.5.4/) if you are on Windows and cannot/won't compile from source).
Download and install [Twisted 10.1.0 for Python 2.5](http://twistedmatrix.com/)
Download RelayBot.py and config.py and save them both to the same directory.

**Creating the config**

Run config.py and answer all the questions. This will create your config file and set up all the information on users.

**Starting the bot**

(These instructions are only for Linux/Mac. Running "twistd" on Windows takes some fiddling, but I am working on the assumption nobody will run this on Windows. If you do need more clear instructions, make an issue in the issue tracker)
Twisted comes with a file called "twistd", which is used to launch applications that use Twisted. RelayManager uses "twistd" for all its forking and log management, so to run RelayBot you need to locate "twistd". Normally running "whereis twistd" is enough.
Once you have located twistd run the following command (In the directory containing relaybot.py): "[twistd\_location](twistd_location.md) --python relaybot.py"
This should create a relaybot.pid file if launched correctly.

**IRC commands**

If launched correctly the bot (Called RelayManager) should connect and join your IRC server and channel. For a full list of commands say "RelayManager help" in the chat.
All commands are prefixed with the bots name (RelayManager) like so: RelayManager [command](command.md) [arg1](arg1.md) [arg2](arg2.md) [argY](argY.md)

The commands you need to be aware most of are:

**add\_network [identifier](identifier.md) [address](address.md) [port](port.md) (Nickname - Default is RelayBot)**

**add\_channel [network](network.md) [channel](channel.md) (password - Leave blank for no password)**

Have an experiment. To set up a simple relay with Freenode say the following command in the channel:

_RelayManager add\_network Freenode irc.freenode.org 6667_

This should make a new user called "Freenode" join your channel, and will cause a RelayBot to connect to irc.freenode.org
To make the bot then join a channel say the following:

_RelayManager add\_channel irc.freenode.org #freenode_

This will make the external bot join #freenode and then relay all messages back.


Thats it! Enjoy.