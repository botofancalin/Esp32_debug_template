file(GLOB template_sources ./*.cpp ./*.c)
set(COMPONENT_SRCS ${template_sources})
set(COMPONENT_ADD_INCLUDEDIRS ".")

register_component()
