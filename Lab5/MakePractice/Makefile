all: static_block dynamic_block

static_block: program.o staticlib.a
	cc program.o staticlib.a -o static_block

dynamic_block: program.o dynlib.so
	cc program.o dynlib.so -o dynamic_block -Wl,-rpath='$$ORIGIN'

program.o: program.c
	cc -c program.c

block.o: source/block.c
	cc -c source/block.c

dynlib.so: block.o
	cc -shared -o dynlib.so block.o

staticlib.a: block.o
	ar qc staticlib.a block.o
