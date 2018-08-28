#
# Makefile
#
default: all


.PHONY: all clean

all:
	-@echo "  [Build $(LIB_NAME)]:"
	-@echo "    compile g711..."
	-@$(CROSS_COMPILE)g++ -fpermissive $(CFLAGS) -c audio_encode.cpp  -o audio_encode.o
	-@$(CROSS_COMPILE)ar rcs libg711.a audio_encode.o

clean:
	-@echo "  [Clean $(LIB_NAME)]:"
	-@rm -f *.a *.o
	-@rm -fr $(LIB_PATH)
