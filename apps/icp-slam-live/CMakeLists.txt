INCLUDE(../../cmakemodules/AssureCMakeRootFile.cmake) # Avoid user mistake in CMake source directory
PROJECT(icp_slam_live)

SET(TMP_TARGET_NAME "icp-slam-live")
ADD_EXECUTABLE(${TMP_TARGET_NAME}
               icp-slam-live_main.cpp
			    ${MRPT_VERSION_RC_FILE})

# Add the required libraries for linking:
TARGET_LINK_LIBRARIES(${TMP_TARGET_NAME} ${MRPT_LINKER_LIBS})

# Dependencies on MRPT libraries:
#  Just mention the top-level dependency, the rest will be detected automatically, 
#  and all the needed #include<> dirs added (see the script DeclareAppDependencies.cmake for further details)
DeclareAppDependencies(${TMP_TARGET_NAME} mrpt-gui mrpt-slam mrpt-hwdrivers)

DeclareAppForInstall(${TMP_TARGET_NAME})
