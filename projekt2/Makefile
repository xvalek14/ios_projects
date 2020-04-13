#Project: proj2
#Author: Vladislav Valek
#Date: 12.4.2020

# Usage:
# make        # Compile all binary
# make clean  # Remove ALL binaries and object files from the directory
# make archive # Pack all c and h files together with Makefile into archive.
# make debug # Run debugger
TARGET = proj2

# Define variables used as names of programs in built-in rules
SHELL = /bin/bash
CC      = gcc
RM      = rm -f
RMFILES = *.o *.out $(TARGET)
ALLFILES = Makefile *.c *.h

# Extra flags to give to the C compiler
# https://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html
CFLAGS = -std=gnu99 -Wall -Wextra -Werror -pedantic -g

# We define all the targets(commands) that are not files
.PHONY = clean	

SRCS := $(wildcard *.c)

## Generic compilation rule
# $@...The file name of the target of the rule
# $<...The name of the first prerequisite
# $^...The names of all the prerequisites, with spaces between them
# https://www.gnu.org/software/make/manual/html_node/Automatic-Variables.html#Automatic-Variables
# '%' is a pattern for matching file names

## Rule for making the actual target
$(TARGET) : $(SRCS)
	@echo -e "Compiling and linking \t$^ --> $@"
	@$(CC) $(CFLAGS) $^ -o $@

#Making debug environment
debug : $(TARGET)
	@export EDITOR=vim
	@gdb $(TARGET)

#Rule for making the archive
archive : $(TARGET) clean
	@echo -e "Packing \t$< --> $<.zip"
	@zip $<.zip $(ALLFILES)

# Clean rule
clean :
	@echo -e "Cleaning project files \t$(RMFILES)"
	@$(RM) $(RMFILES)