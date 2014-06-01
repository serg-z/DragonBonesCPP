TARGET = DragonBones

DRAGONBONES_PATH = $(abspath ../..)

INCLUDES = \
	-I.. \
	-I$(DRAGONBONES_PATH)/dragonbones \
	-I$(DRAGONBONES_PATH)/renderer/cocos2d-x-2.x

SOURCES = \
	$(DRAGONBONES_PATH)/renderer/cocos2d-x-2.x/CCDragonBones.cpp \
	$(DRAGONBONES_PATH)/renderer/cocos2d-x-2.x/Cocos2dxDisplayBridge.cpp \
	$(DRAGONBONES_PATH)/renderer/cocos2d-x-2.x/Cocos2dxTextureAtlas.cpp \
	$(DRAGONBONES_PATH)/renderer/cocos2d-x-2.x/Cocos2dxAtlasNode.cpp \
	$(DRAGONBONES_PATH)/renderer/cocos2d-x-2.x/Cocos2dxFactory.cpp \
	$(DRAGONBONES_PATH)/dragonbones/Slot.cpp \
	$(DRAGONBONES_PATH)/dragonbones/events/AnimationEvent.cpp \
	$(DRAGONBONES_PATH)/dragonbones/events/Event.cpp \
	$(DRAGONBONES_PATH)/dragonbones/events/ArmatureEvent.cpp \
	$(DRAGONBONES_PATH)/dragonbones/events/SoundEvent.cpp \
	$(DRAGONBONES_PATH)/dragonbones/events/SoundEventManager.cpp \
	$(DRAGONBONES_PATH)/dragonbones/events/FrameEvent.cpp \
	$(DRAGONBONES_PATH)/dragonbones/utils/BytesType.cpp \
	$(DRAGONBONES_PATH)/dragonbones/utils/DBDataUtil.cpp \
	$(DRAGONBONES_PATH)/dragonbones/utils/DBGeometry.cpp \
	$(DRAGONBONES_PATH)/dragonbones/utils/ConstValues.cpp \
	$(DRAGONBONES_PATH)/dragonbones/utils/TransformUtil.cpp \
	$(DRAGONBONES_PATH)/dragonbones/Bone.cpp \
	$(DRAGONBONES_PATH)/dragonbones/Armature.cpp \
	$(DRAGONBONES_PATH)/dragonbones/objects/TransformTimeline.cpp \
	$(DRAGONBONES_PATH)/dragonbones/objects/dbtinyxml2.cpp \
	$(DRAGONBONES_PATH)/dragonbones/objects/XMLDataParser.cpp \
	$(DRAGONBONES_PATH)/dragonbones/objects/DisplayData.cpp \
	$(DRAGONBONES_PATH)/dragonbones/factories/BaseFactory.cpp \
	$(DRAGONBONES_PATH)/dragonbones/core/DBObject.cpp \
	$(DRAGONBONES_PATH)/dragonbones/core/DragonBones.cpp \
	$(DRAGONBONES_PATH)/dragonbones/animation/TimelineState.cpp \
	$(DRAGONBONES_PATH)/dragonbones/animation/Animation.cpp \
	$(DRAGONBONES_PATH)/dragonbones/animation/AnimationState.cpp

COCOS_ROOT ?= ../../..
include $(COCOS_ROOT)/cocos2dx/proj.linux/cocos2dx.mk

DEFINES += -DCOCOS2D_2X

CXXFLAGS += -std=c++11

ifeq ($(DEBUG), 1)
DIR := debug
else
DIR := release
endif

LIBPATH = $(DIR)/lib$(TARGET).a

all: $(TARGET)

$(TARGET): $(OBJECTS) $(STATICLIBS) $(COCOS_LIBS) $(CORE_MAKEFILE_LIST)
	@mkdir -p $(DIR)
	@ar rc $(LIBPATH) $(OBJECTS)
	@ranlib $(LIBPATH)

$(OBJ_DIR)/%.o: %.cpp $(CORE_MAKEFILE_LIST)
	@mkdir -p $(@D)
	$(LOG_CXX)$(CXX) $(CXXFLAGS) $(INCLUDES) $(DEFINES) $(VISIBILITY) -c $< -o $@

$(OBJ_DIR)/%.o: ../%.cpp $(CORE_MAKEFILE_LIST)
	@mkdir -p $(@D)
	$(LOG_CXX)$(CXX) $(CXXFLAGS) $(INCLUDES) $(DEFINES) $(VISIBILITY) -c $< -o $@
