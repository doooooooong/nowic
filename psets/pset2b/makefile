# a makefile example using multiple libraries and include 
# 
# 2020/03/05 Created by idebtor@gmail.com
# 2021/01/02 Updated for macOS and DEBUG options
#
# $@ The name of the EXEC file (the one before the colon)
# $< The name of the first (or only) prerequisite file (the first one after the colon)
# $^ The names of all the prerequisite files (space separated)
# $* The stem (the bit which matches the % wildcard in the rule definition.
#
CC = g++
LIBDIR = ../../lib
INCDIR = ../../include
CCFLAGS = -std=c++11 -Wall -g 
#CCFLAGS += -DDEBUG        # uncomment for debugging
ifeq ($(OS),Windows_NT)
	LDFLAGS = -L$(LIBDIR) -lsort -lnowic -lrand
else
	LDFLAGS = -L$(LIBDIR) -lsort_mac -lnowic_mac -lrand_mac
endif

SRC1 = sorting.cpp 
OBJ1 = $(SRC1:.cpp=.o)
EXE1 = sorting

# rule for link
all: $(EXE1)  
$(EXE1): $(OBJ1)
	$(CC) -o $@ $^ $(LDFLAGS)

# rule for compilation
%.o: %.cpp
	$(CC) $(CCFLAGS) -c -I$(INCDIR) $<

.PHONY: all clean install
clean:
	rm -f *.o *.exe $(OBJ1) $(EXE1)
	
install:
ifeq ($(OS),Windows_NT)
	mkdir -p ./deliverable && \
	cp pset2b.pdf random.pdf makefile ./deliverable
	cp sorting.cpp ./deliverable
	cp -v deliverable/* ../../../nowic/psets/pset2b
	xcopy .vscode ..\..\..\nowic\psets\pset2b\.vscode //E //H //K //Y //I 
endif
