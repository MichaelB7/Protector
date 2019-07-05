Protector is a Bitboard-based chess program that communicates with a chess GUI via the UCI protocol.

### TERMS OF USE

Protector is free, and distributed under the GNU General Public License(GPL). Essentially, this means that you are free to do almost what you want with the program, including distributing it among your friends, making it available for download from your web site, selling it (either by itself or as part of some bigger software package), or using it as the starting point for a software project of your own.

Please note that these terms do not apply for the contents of the two files "egbt.cpp" and "tbdecode.h". These files contain software from a third party (Eugene Nalimov and Andrew Kadatch) and they are not an integral part of Protector but an optional supplement.

The only real limitation is that whenever you distribute Protector in some way, you must always include the full source code, or a pointer to where the source code can be found.  If you make any changes to the source code, these changes must also be made available under the GPL.

For full details, read the copy of the GPL found in the file named Copying.txt.

### COPYRIGHTS

Please note that the sources for the endgame table access from Eugene Nalimov and Andrew Kadatch are NOT distributed under GPL. In order to use them for any other purpose than building Protector you will need an own separate permission from Eugene Nalimov and Andrew Kadatch (see the copyright remarks in their files [egtb.cpp and tbdecode.h] for more details).

### CREDITS

Protector is based on many great ideas from the following people: Fabien Letouzey (pvnodes, blending of opening and endgame values, eval params), Thomas Gaksch (pvnode extensions, extended futility pruning, space attack eval), Robert Hyatt (consistent hashtable entries), Stefan Meyer-Kahlen (UCI), Gerd Isenberg/Lasse Hansen (magic bitboards), Marco Costabla/Tord Romstad/Joona Kiiski (Glaurung/Stockfish sources), Vasik Rajlich/Larry Kaufman (singlemove extensions, op/eg integer arithmetics, values for material imbalances in Rybka/Robbolito) and Andrew Kadatch/Eugene Nalimov (endgame tablebases). Without their contributions Protector would not be what it is. Thank you so much.