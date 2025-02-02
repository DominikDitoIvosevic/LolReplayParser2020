# LolReplayParser2020
Trying to collect knowledge and successfully parse League of Legends replay files again.

Please open an issue if you have any meaningful info or links to other projects which at any point in time touched on this subject.

My current limitation is lack of knowledge of reverse engineering and bitstream manipulation. As far as I understood from a LoL dev blogpost a while ago they encrypted their client (whatever they meant by that) which I guess means it's way harder to directly reverse the code and get more meaningful info.
Last info was that they were using Blowfish for encrypting the payload and gzip for compressing it, but that might have changed.

## Current progress:

I'm using https://github.com/ryancole/LeagueReplayReader to decompress and decrypt the replay file and I tried using https://github.com/Zero3/LolSpecAnalyzer to find some meaning. In any case, I'm trying to find any recognizable strings in the files generated by LeagueReplayReader which might resemble ward totem item codes or summoner names but so far no luck. I would like to know the generated files are correct but by reading https://github.com/robertabcd/lol-ob/wiki/ROFL-Container-Notes I don't think I'm finding the correct magic numbers so maybe the decompression/decryption method changed or the magic numbers changed. The cool thing about decompressing is that as I understand (I didn't bother checking yet) since we first decrypt then decompress, had we decrypted using wrong key or method then we couldn't decompress since there are some assumptions about the compressed format which wouldn't be valid if the decrypted file just gave us random bitstream.

Update: Well, I'm giving up for now. I haven't managed to figure out the meaning of the bits in the keyframes. I tried using IDA to disassemble the exe and find some meaning there but that didn't give results because I lack the experience. If someone wants to play with this don't hesisate to get in touch via opening an issue or whatever

# Existing projects and links which touched on this subject:

@loldevs / leaguespec 
https://github.com/loldevs/leaguespec/wiki
https://github.com/loldevs/leaguespec/wiki/Meeting-Summaries

@lukegb lukegb/lolparse.py
https://gist.github.com/lukegb/d2997a5fc7970ce6e1e1

A parser of League of Legends replay files. 
https://github.com/ryancole/LeagueReplayReader

LolSpecAnalyzer is a Java debugging tool/framework for analyzing the League of Legends (http://leagueoflegends.com) spectator data format.
https://github.com/Zero3/LolSpecAnalyzer

@robertabcd / lol-ob - ROFL Container Notes
https://github.com/robertabcd/lol-ob/wiki/ROFL-Container-Notes

Reference implementation of the rofl file parser
https://github.com/loldevs/libOL

LoL bot which I guess did everything from connecting to the RIOT server to issuing commands in version 4.X
https://github.com/Theoretical/Summoning
I've managed to collect and compile everything in one place https://github.com/Kungitoo/Summoning

@EloGank / lol-replay-downloader 
https://github.com/EloGank/lol-replay-downloader

@leeanchu / ROFL-Player 
https://github.com/leeanchu/ROFL-Player

AutoCaster for Hackathon 2015 by Team Float
https://github.com/protopizza/AutoCaster

@Matviy / LeagueReplayHook 
https://github.com/Matviy/LeagueReplayHook

This is an unofficial, uncomplete and (pretty sure) wrong documentation of the RESTful service which powers the League of Legends spectator mode.
https://gist.github.com/themasch/8375971

https://stackoverflow.com/questions/22827221/league-of-legends-read-chunks-keyframes-through-its-restful-api

https://gamedev.stackexchange.com/questions/49856/league-of-legends-spectator-stream-format

https://www.reddit.com/r/ReverseEngineering/comments/19fqm9/decoding_binary_files/

https://csharp.developreference.com/article/14676731/Blowfish+ECB+encryption+in+C%23+implementation

