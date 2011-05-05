PROG = streetview-explorer
SRCS += Application.cpp
SRCS += EditLocationsDialog.cpp
SRCS += Explorer.cpp
SRCS += GLCanvas.cpp
SRCS += MainFrame.cpp
SRCS += Panorama.cpp
SRCS += Player.cpp
SRCS += PreferencesDialog.cpp
SRCS += Settings.cpp
SRCS += Utm.cpp
SRCS += base64.cpp
SRCS += common.cpp
SRCS += download.cpp
SRCS += statustext.cpp

X11BASE ?= /usr/X11R6
LOCALBASE ?= /usr/local

RM ?= rm -f
CXXFLAGS += -ggdb3 -O0 -W -Wall
CPPFLAGS += -I${X11BASE}/include -I${LOCALBASE}/include
CPPFLAGS += `wx-config --cxxflags`
LDADD += -L${X11BASE}/lib -L${LOCALBASE}/lib
LDADD += -lGL -lGLU -lwx_gtk2_gl -lcurl
LDADD += `wx-config --libs`
OBJS = ${SRCS:M*.cpp:R:S/$/.o/g}

.SUFFIXES: .cpp .o

all: ${PROG}

.cpp.o:
	${CXX} ${CPPFLAGS} ${CXXFLAGS} -o ${.TARGET} -c ${.IMPSRC}

depend:
	@files="${SRCS:M*.cpp}"; \
	if [ "$$files" != "  " ]; then \
	  echo mkdep -a ${MKDEP} ${CXXFLAGS:M-[ID]*} ${CPPFLAGS} $$files; \
	  mkdep -a ${MKDEP} ${CXXFLAGS:M-[ID]*} ${CPPFLAGS} $$files; \
	fi

${PROG}: ${OBJS}
	c++ -o ${PROG} ${OBJS} ${LDADD}

clean:
	${RM} ${PROG} ${OBJS}