PWD			:= $(shell pwd)
#MODULE_DIR		:= $(word 2, $(subst /unit_test/linux/, ,$(PWD)))
#PRIVATE_DIR		:= $(shell echo ./$(MODULE_DIR)|sed 's/\/[0-9a-zA-Z_]*/\/../g' )
MODULE_NAME		:= "Audio Test"

INCLUDE_FLAG    := 
#LINK_FLAG	:= 
LIBS		:= -lasound -lpthread -ldl


LIB_SUFFIX = a
INCLUDE_FLAG += -I../UsageEnvironment/include -I../groupsock/include \
				-I../liveMedia/include -I../BasicUsageEnvironment/include
##################### Included LIBS:
USAGE_ENVIRONMENT_DIR = ../UsageEnvironment
USAGE_ENVIRONMENT_LIB = $(USAGE_ENVIRONMENT_DIR)/libUsageEnvironment.$(LIB_SUFFIX)
BASIC_USAGE_ENVIRONMENT_DIR = ../BasicUsageEnvironment
BASIC_USAGE_ENVIRONMENT_LIB = $(BASIC_USAGE_ENVIRONMENT_DIR)/libBasicUsageEnvironment.$(LIB_SUFFIX)
LIVEMEDIA_DIR = ../liveMedia
LIVEMEDIA_LIB = $(LIVEMEDIA_DIR)/libliveMedia.$(LIB_SUFFIX)
GROUPSOCK_DIR = ../groupsock
GROUPSOCK_LIB = $(GROUPSOCK_DIR)/libgroupsock.$(LIB_SUFFIX)
LOCAL_LIBS = $(LIVEMEDIA_LIB) $(GROUPSOCK_LIB) \
			$(BASIC_USAGE_ENVIRONMENT_LIB) \
			$(USAGE_ENVIRONMENT_LIB)
LIBS += $(LOCAL_LIBS)
INCLUDE_G711 = -I../g711
LIBS_G711 = -L../g711 -lg711
INCLUDE_FLAG += $(INCLUDE_G711)
LIBS += $(LIBS_G711)

RTSP_AUDIO_PATH		= $(APP_PATH)


default:all

.PHONY: all clean

all:pre_all
	-@echo "  [Build $(MODULE_NAME)]:"
	-@echo "    compile testG711... "
	-@$(CROSS_COMPILE)g++ $(APP_CFLAG) -c test_audio.cpp $(INCLUDE_FLAG)
	-@$(CROSS_COMPILE)g++ $(APP_CFLAG) -c G711AudioStreamServerMediaSubsession.cpp $(INCLUDE_FLAG)
	-@$(CROSS_COMPILE)g++ $(APP_CFLAG) -c G711AudioStreamSource.cpp $(INCLUDE_FLAG)
	-@$(CROSS_COMPILE)g++ $(APP_CFLAG) -o \
		testG711 test_audio.o G711AudioStreamServerMediaSubsession.o G711AudioStreamSource.o \
		$(LINK_FLAG) $(LIBS)
	-@$(CROSS_COMPILE)strip testG711

clean:pre_clean
	-@echo "  [Clean $(MODULE_NAME)]:"
	-@rm -f testG711 *.o

pre_all:
	-@echo " "

pre_clean:
	-@echo " "
