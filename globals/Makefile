CC:=clang-19
FILE:=main.cpp
TEST:=test.c
PLUGIN:=lib.so
TEST_OUT:=test.lo
TEST_OPTIONS=-S -emit-llvm
PLUGIN_OPTIONS=-shared -o

all:
	$(CC) $(TEST_OPTIONS) $(TEST) -o $(TEST_OUT)
	$(CC) $(PLUGIN_OPTIONS) $(PLUGIN) $(FILE) -fPIC
	opt -load-pass-plugin ./$(PLUGIN) --passes=globals,gunused --disable-output $(TEST_OUT)

clean:
	rm -rf $(PLUGIN) $(TEST_OUT)