CODE_DIRS=. #Add more folders
INC_DIRS=. #Add more folders
OUTPUT=exe

CXX=gcc

#Produce ".d" files that includes make rules for the ".h" dependencies
DEP_FLAGS=-MP -MD

CFLAGS=-Wall -g $(foreach F,$(INC_DIRS),-I$(F)) $(DEP_FLAGS)

CFILES=$(foreach F,$(CODE_DIRS),$(wildcard $(F)/*.c))

OBJECTS=$(patsubst %.c,%.o,$(CFILES))
DEP_FILES=$(patsubst %.c,%.d,$(CFILES))

all: $(OUTPUT)

$(OUTPUT): $(OBJECTS)
	$(CXX) -o $@ $^

%.o:%.c
	$(CXX) $(CFLAGS) -c -o $@ $<

clean:
	rm -rf $(OUTPUT) $(OBJECTS) $(DEP_FILES)

.PHONY: all clean
