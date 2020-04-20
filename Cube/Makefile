### COMPILATION ###
C      = gcc
FLAGS  = -Wall -Wextra -Werror


ifeq ($(OS),Windows_NT)
    CCFLAGS += -D WIN32
    ifeq ($(PROCESSOR_ARCHITEW6432),AMD64)
        CCFLAGS += -D AMD64
    else
        ifeq ($(PROCESSOR_ARCHITECTURE),AMD64)
            CCFLAGS += -D AMD64
        endif
        ifeq ($(PROCESSOR_ARCHITECTURE),x86)
            CCFLAGS += -D IA32
        endif
    endif
else
    UNAME_S := $(shell uname -s)
    ifeq ($(UNAME_S),Linux)
        CCFLAGS = -lGL -lGLU -lglut    # https://stackoverflow.com/questions/8352176/error-with-glut-compile-in-ubuntu
    endif
    ifeq ($(UNAME_S),Darwin)
        CCFLAGS = -framework GLUT -framework OpenGL -framework
    endif
    UNAME_P := $(shell uname -p)
    ifeq ($(UNAME_P),x86_64)
        CCFLAGS += -D AMD64
    endif
    ifneq ($(filter %86,$(UNAME_P)),)
        CCFLAGS += -D IA32
    endif
    ifneq ($(filter arm%,$(UNAME_P)),)
        CCFLAGS += -D ARM
    endif
endif



### EXECUTABLE ###
NAME   = cube

### SOURCES ###
SOURCES =	cube.c \


### RULES ###

all: $(NAME)

$(NAME): $(OBJS) packages
	@gcc  -Wno-deprecated  $(NAME).c -o $(NAME) $(CCFLAGS)
	@echo "Project successfully compiled"

packages:
	sudo apt-get update && sudo apt-get install freeglut3-dev

clean:
	@echo "$(GREEN)Supressing libraries files$(CYAN)"
	@rm -f $(NAME).o

fclean:
	@rm -f $(NAME)

re: fclean
	@$(MAKE) all -j

.PHONY: temporary, re, fclean, clean
