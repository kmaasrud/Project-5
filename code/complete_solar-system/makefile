CC = g++

# Flags for compiler.
CCFLAGS = -larmadillo -lblas -llapack -std=c++17 -Wall -Wpedantic -Wextra #-fopenmp -O3

# Names of files in src you want to compile: "./obj/<name>.o".
OBJ = ./obj/euler.o ./obj/verlet.o ./obj/body.o ./obj/system.o ./obj/initialize.o

# Headerfile(s) used.
DEPS = ./include/lib.h ./include/body.h ./include/system.h

#------------------------------------
# No need to change the stuff below.
NO_OF_FILES := $(words $(OBJ))
COUNTER = 1

main: $(OBJ) $(DEPS)
	@$(CC) $(wildcard ./obj/*.o) main.cpp $(CCFLAGS) -o main.exe
	@if [ -f "main.exe" ]; then echo "Binary main.exe built \033[0;32msuccessfully\033[0m!"; fi

./obj/%.o: ./src/%.cpp obj_dir $(DEPS)
	@$(CC) $(CCFLAGS) $< -c; \
	mv *.o ./obj/
	@printf "%-50s \033[0;32m$(COUNTER)/$(NO_OF_FILES)\033[0m\n" "$< compiled"
	@$(eval COUNTER=$(shell echo $$(($(COUNTER)+1))))

obj_dir:
	@if [ ! -d "./obj" ]; then echo "Making \033[0;36mobj\033[0m directory"; mkdir obj; fi

clean:
	@rm -rf obj main.exe
	@echo "Directory \033[0;36mobj\033[0m and executable \033[0;36mmain.exe\033[0m deleted."
