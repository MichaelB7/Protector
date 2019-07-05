MAKE=make
#COMPILER=GCC_MINGW64
COMPILER=GCC

CLEAN_CMD=@rm -f *.o *.bak *.bin *.lrn game.* log.* 
#CLEAN_CMD=del *.o *.gcda

ifeq ($(COMPILER),GCC_MINGW64)
   CC=x86_64-w64-mingw32-gcc
   CPPC=x86_64-w64-mingw32-g++
   LN=x86_64-w64-mingw32-g++
else
   CC=gcc
   CPPC=g++
   LN=g++
endif

CFLAGS=-O3 -Wall -ansi -pedantic -Wno-long-long -pthread -flto -msse -DNDEBUG
protectordbg: CFLAGS=-Wall -ansi -pedantic -Wno-long-long -pthread

protectorobjects = protector.o bitboard.o position.o fen.o io.o \
                   movegeneration.o matesearch.o keytable.o hash.o test.o \
                   pgn.o tools.o search.o evaluation.o coordination.o \
                   xboard.o book.o tablebase.o

protectorsources = $(protectorobjects:.o=.c) egtb.cpp

.c.o:
	$(CC) $(CFLAGS) -c $*.c

.cpp.o:
	$(CPPC) $(CPPFLAGS) -O3 -flto -c $*.cpp

protector: $(protectorobjects) egtb.o
	$(LN)  -lm -pthread  -flto -o Protector $(protectorobjects) egtb.o

protectordbg: $(protectorobjects) egtb.o
	$(LN)  -lm -pthread  -flto -o Protector $(protectorobjects) egtb.o

protector_pgogen: $(protectorobjects) egtb.o
	$(LN)  -lm -pthread  -flto -fprofile-generate -o Protector $(protectorobjects) egtb.o

protector_pgouse: $(protectorobjects) egtb.o
	$(LN)  -lm -pthread  -flto -fprofile-use -o Protector $(protectorobjects) egtb.o

all:
	$(MAKE) clean
	$(MAKE) protector
	$(MAKE) clean

debug:
	$(MAKE) clean
	$(MAKE) protectordbg
	$(MAKE) clean

protectorpgo:
	$(MAKE) clean
	$(MAKE) CFLAGS='-fprofile-generate -O3 -Wall -ansi -pedantic -Wno-long-long -pthread -flto -msse -DNDEBUG' CPPFLAGS='-fprofile-generate' protector_pgogen
	rm *.o
	Protector -t pgo.pgn
	$(MAKE) CFLAGS='-fprofile-use -O3 -Wall -ansi -pedantic -Wno-long-long -pthread -flto -msse -DNDEBUG' CPPFLAGS='-fprofile-use' protector_pgouse
	$(MAKE) clean

.PHONY: clean
clean:
	$(CLEAN_CMD)
