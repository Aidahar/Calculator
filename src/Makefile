GCC=gcc -Wall -Wextra -Werror -std=c11
FILES=s21_helper.c parse_string.c stack.c
RELEASE= -O3
DEBUG= -g -O0
CPPCHECK=cppcheck --enable=style,warning,performance,portability -q *.c

all: debug

release: ${FILES}
	${CPPCHECK}
	${GCC} ${RELEASE} ${FILES}

debug: ${FILES}
	${GCC} ${DEBUG} ${FILES} && ./a.out

valgrind: debug
	valgrind --tool=memcheck --tool=callgrind --trace-children=yes --track-fds=yes --track-origins=yes --leak-check=full --show-leak-kinds=all -s --log-file=test ./a.out && cat test | grep errors

clean: 
	rm -rf a.out *.dSYM *.o test.txt .gdb_history
