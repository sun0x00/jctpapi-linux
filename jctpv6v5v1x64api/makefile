OBJS=jctpv6v5v1x64api_wrap.o
INCLUDE=-I./ -I${JAVA_HOME}/include -I${JAVA_HOME}/include/linux
TARGET=libjctpv6v5v1x64api.so
CXXFLAG=-shared -fPIC
CC=g++
LDLIB=-L. -lthosttraderapi_se -lthostmduserapi_se
LD_RUN_PATH=-Wl,-rpath,/tmp/xyz/redtorch/api/jctp/lib/jctpv6v5v1x64api/

$(TARGET) : $(OBJS)
	$(CC) $(CXXFLAG) $(LD_RUN_PATH) $(INCLUDE) -o $(TARGET) $(OBJS) $(LDLIB) ./libiconv.a
$(OBJS) : %.o : %.cpp
	$(CC) -c -fPIC $(INCLUDE) $< -o $@

clean:
	-rm -f $(OBJS)
	-rm -f $(TARGET)
#install:
#	cp $(TARGET) /usr/lib
