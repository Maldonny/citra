set(SRCS
            bootmanager.cpp
            debugger/callstack.cpp
            debugger/disassembler.cpp
            debugger/ramview.cpp
            debugger/registers.cpp
            hotkeys.cpp
            main.cpp
            config/controller_config.cpp
            config/controller_config_util.cpp)

qt4_wrap_ui(UI_HDRS
                    debugger/callstack.ui
                    debugger/disassembler.ui
                    debugger/registers.ui
                    hotkeys.ui
                    main.ui
                    config/controller_config.ui)

qt4_wrap_cpp(MOC_SRCS
                        bootmanager.hxx
                        debugger/callstack.hxx
                        debugger/disassembler.hxx
                        debugger/registers.hxx
                        debugger/ramview.hxx
                        hotkeys.hxx
                        main.hxx
                        config/controller_config.hxx
                        config/controller_config_util.hxx)

# add uic results to include directories
include_directories(${CMAKE_CURRENT_BINARY_DIR})
include_directories(./)

add_executable(citra-qt ${SRCS} ${MOC_SRCS} ${UI_HDRS})
target_link_libraries(citra-qt core common video_core qhexedit ${QT_LIBRARIES} ${OPENGL_LIBRARIES} ${SDL2_LIBRARY} rt GLEW ${GLFW_LIBRARIES})

#install(TARGETS citra-qt RUNTIME DESTINATION ${bindir})
