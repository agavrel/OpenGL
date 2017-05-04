### COMPILATION ###
C      = gcc
FLAGS  = -Wall -Wextra -Werror

### EXECUTABLE ###
NAME   = cube

### SOURCES ###
SOURCES =	cube.c \


### RULES ###

all: $(NAME)

$(NAME): $(OBJS)
	@gcc -framework GLUT -Wno-deprecated -framework OpenGL -framework Cocoa $(NAME).c -o $(NAME)
	@echo "Project successfully compiled"

clean:
	@echo "$(GREEN)Supressing libraries files$(CYAN)"
	@rm -f $(NAME).o

fclean:
	@rm -f $(NAME)

re: fclean
	@$(MAKE) all -j

.PHONY: temporary, re, fclean, clean
