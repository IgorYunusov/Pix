#
# Cross Platform Makefile
# Compatible with MSYS2/MINGW, Ubuntu 14.04.1 and Mac OS X
#
# You will need GLFW (http://www.glfw.org):
# Linux:
#   apt-get install libglfw-dev
# Mac OS X:
#   brew install glfw
# MSYS2:
#   pacman -S --noconfirm --needed mingw-w64-x86_64-toolchain mingw-w64-x86_64-glfw
#

#CXX = g++
#CXX = clang++

EXE = pixout
OBJS = main.o imgui_impl_glfw_gl2.o
OBJS += ../../imgui/imgui.o ../../pixui.o ../../tinyfiledialogs.o ../../imgui/imgui_draw.o

UNAME_S := $(shell uname -s)


ifeq ($(UNAME_S), Linux) #LINUX
	ECHO_MESSAGE = "Linux"
	LIBS = -lGL `pkg-config --static --libs glfw3` `pkg-config --cflags --libs opencv` -lpthread

	CXXFLAGS = -I ../../imgui `pkg-config --cflags glfw3`
	CXXFLAGS += -Wall -Wformat
	CFLAGS = $(CXXFLAGS)
endif

# ifeq ($(UNAME_S), Darwin) #APPLE
# 	ECHO_MESSAGE = "Mac OS X"
# 	LIBS = -framework OpenGL -framework Cocoa -framework IOKit -framework CoreVideo
# 	#LIBS += -L/usr/local/lib -lglfw3
# 	LIBS += -L/usr/local/lib -lglfw

# 	CXXFLAGS = -I../../ -I/usr/local/include
# 	CXXFLAGS += -Wall -Wformat
# 	CFLAGS = $(CXXFLAGS)
# endif

# ifeq ($(findstring MINGW,$(UNAME_S)),MINGW)
#    ECHO_MESSAGE = "Windows"
#    LIBS = -lglfw3 -lgdi32 -lopengl32 -limm32

#    CXXFLAGS = -I../../ -I../libs/gl3w `pkg-config --cflags glfw3`
#    CXXFLAGS += -Wall -Wformat
#    CFLAGS = $(CXXFLAGS)
# endif


.cpp.o:
	$(CXX) $(CXXFLAGS) -c -o $@ $<

all: $(EXE)
	@echo Build complete for $(ECHO_MESSAGE)

$(EXE): $(OBJS)
	$(CXX) -o $(EXE) $(OBJS) $(CXXFLAGS) $(LIBS)

clean:
	rm $(EXE) $(OBJS)

