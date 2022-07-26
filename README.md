# YACPBot
A repository for YACPBot, a Discord bot that posts problems from [YACPDB](https://www.yacpdb.org/).

## Gallery
![image](https://user-images.githubusercontent.com/16442480/177006133-5ebf780b-cb9c-4c9f-9823-e3a2a077e2f0.png) | ![image](https://user-images.githubusercontent.com/16442480/177006112-f9522259-4924-492a-b8a7-8802baf32115.png)
--- | ---
*White mates in two; how?* | *This bot also supports fairy problems!*

## To add this bot to your server:
1. Click [this link](https://discord.com/api/oauth2/authorize?client_id=843945577741156393&permissions=277025508416&scope=bot%20applications.commands).
2. Select your server.
3. Give it all the permissions you think it needs. At minimum it needs "Send Messages", "Embed Links", "Attach Files", and either "Use Application Commands" (for slash commands) or "Read Messages" (for `y!` commands) or both. Eventually reaction roles will be implemented, so you should consider checking "Add Reactions" for until then as well. The other two permissions ("Send Messages in Threads", "Read Message History") are there just in case the bot doesn't work without them.
4. Click "Authorise".
5. Type /help in Discord to start things off.

## To run your own copy of this:
1. Download the repository.
2. Put your environment variables into the `.env` file.
3. Make sure the bot has the right permissions in the Discord Developer Portal (see `Required Permissions.txt`), and invite it to any server necessary.
4. Run YACPBot.py.
5. Type /help in Discord to start things off.

## FAQ:
**Q: Why aren't you using FEN to store the positions/PGN to store the solutions?**

A: YACPBot doesn't just post orthodox chess problems. It also posts fairy problems with nonstandard pieces (e.g. Nightrider, Grasshopper, Camel), fairy conditions (e.g. Circe, Madrasi, Take & Make), and seriesmovers (where one side moves multiple times in a row). FEN and PGN simply aren't compatible with these sorts of problems. Further, YACPBot pulls from YACPDB, which already uses its own notation systems. It's fine, just leave it.

**Q: The diagrams look ugly! Can I have CBurnett or Merida pieces instead of Good Companion pieces?**

A: This is a consequence of the above. YACPDB's xfen-to-image converter is one of only two converters I know of that supports all the fairy pieces in YACPDB. The other one is janko.at, and it's harder to get working. If you know of any other chess position image converter that's compatible with fairy pieces and rotated pieces, please let me know.

**Q: Why is knight "S" and not "N"?**

A: Because YACPDB uses "S" for knight and not "N". "N" is already reserved for the "Nightrider", a fairy piece. Changing this when there's no other clear consensus on what "Nightrider" should be notated as is worse than keeping it as-is right now.

**Q: The diagrams look tiny! Can you make them bigger?**

A: Not by much, unfortunately. Discord has a size limit on embedded image previews (something like 256x256) and YACPDB's xfen-to-image converter outputs a 258x258 image. If you know any way to embed larger images, or to make YACPDB's xfen-to-image converter output a larger image, please let me know. Also, check your Discord zoom settings (App Settings > Appearance > Zoom Level), as the previews scale with this.

**Q: Could you please add the ability for Discord users to solve the problem move by move (like with other Discord chess puzzle bots)?**

A: This is infeasible for the time being. The primary reason is that YACPDB is rather patchy when it comes to solution formatting; some problems in YACPDB don't even have a solution recorded, and many more have their solution recorded in the wrong format. Secondarily, this would require me to code up a way for the bot to choose Black's move, and probably to choose a refutation for Black if the user gives the wrong solution. Come back in a few years, when people have fixed the holes in YACPDB, and when I've gotten much better at programming, and then maybe I'll entertain this idea.

**Q: I'm having trouble understanding some of these stipulations. Who moves first? What does "Ser-hs#92 Madrasi" mean?**

A: See "Planned future updates" below. In the meantime, Marken Foo's [Introduction to Problems: Literacy](https://thechesspolyglot.netlify.app/introduction-to-problems/) is a good place to get started.

**Q: What does "b) Remove wSe4" mean?**

A: This is a twin stipulation. Once you solve the problem, go back to the original position and remove the white knight on e4, then solve it again.

**Q: Your bot is slow!**

A: Yes, it unfortunately is. This will be improved in a later update once I cache YACPDB and host the bot externally. If you know how to make it faster other than this, please let me know.

**Q: Your bot's code is messy and amateurish!**

A: Yes, I'm an amateur coder. If you're willing to help improve my code at your own expense, please let me know. 

**Q: Your bot's code has stuff that isn't used, like `TestingSlashCommands.py`!**

A: This one's on me. Some of this is just test files you can ignore and some of it is stuff I'm planning on using later. I'll clean up this repository at some point.

## Planned future updates:
The following is a rough outline of planned future updates. This is not set in stone and very much subject to change.

v1.5: Run maintenance on the bot's code; more specifically, update the prerequisite packages and possibly reformat any code to deal with such updates if necessary.

v1.6: Add reaction-commands, so that users can delete the bot's responses to them.

v1.7: Fully deprecate `y!` commands, transition to slash commands only to reduce confusion.

v1.8: Prettify certain stipulations into more readable English (for the benefit of people who don't do chess problems very often).

v1.9: Fully implement `/search`, using reaction commands to page results.

v2.0: Transition the bot to a permanent host (e.g. Heroku) instead of running it off my own computer.

v3.0: Hook up the bot to cache YACPDB using something like MongoDB, to improve the speed of the bot.
