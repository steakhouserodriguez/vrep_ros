# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(vrep_common)
# Load catkin and all dependencies required for this package
# TODO: remove all from COMPONENTS that are not catkin packages.
find_package(catkin REQUIRED COMPONENTS 
	roscpp
	std_msgs
	sensor_msgs
	message_generation)
find_package(OpenCV REQUIRED)

# include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})
# CATKIN_MIGRATION: removed during catkin migration
# cmake_minimum_required(VERSION 2.4.6)

# CATKIN_MIGRATION: removed during catkin migration
# include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
#set(ROS_BUILD_TYPE RelWithDebInfo)


# CATKIN_MIGRATION: removed during catkin migration
# rosbuild_init()

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

#uncomment if you have defined messages
add_message_files(
  FILES
  ForceSensorData.msg
  JointSetStateData.msg
  ObjectGroupData.msg
  ProximitySensorData.msg
  VisionSensorData.msg
  VisionSensorDepthBuff.msg
  VrepInfo.msg
)
#uncomment if you have defined services
add_service_files(
  FILES
  simRosGetUIButtonProperty.srv
  simRosReadVisionSensor.srv
  simRosDisableSubscriber.srv
  simRosTransferFile.srv
  simRosGetBooleanParameter.srv
  simRosReadForceSensor.srv
  simRosGetArrayParameter.srv
  simRosSetFloatSignal.srv
  simRosGetObjectChild.srv
  simRosGetFloatSignal.srv
  simRosCopyPasteObjects.srv
  simRosSetUISlider.srv
  simRosGetIntegerSignal.srv
  simRosGetObjectSelection.srv
  simRosDisplayDialog.srv
  simRosGetInfo.srv
  simRosSetFloatingParameter.srv
  simRosRemoveUI.srv
  simRosSetObjectSelection.srv
  simRosAuxiliaryConsoleOpen.srv
  simRosGetStringParameter.srv
  simRosSetVisionSensorImage.srv
  simRosPauseSimulation.srv
  simRosGetUISlider.srv
  simRosGetDistanceHandle.srv
  simRosEraseFile.srv
  simRosGetObjectPose.srv
  simRosLoadUI.srv
  simRosClearIntegerSignal.srv
  simRosBreakForceSensor.srv
  simRosSetUIButtonLabel.srv
  simRosClearFloatSignal.srv
  simRosSetObjectPose.srv
  simRosGetCollisionHandle.srv
  simRosSynchronous.srv
  simRosGetDialogInput.srv
  simRosSetIntegerParameter.srv
  simRosSetObjectQuaternion.srv
  simRosCloseScene.srv
  simRosGetObjectParent.srv
  simRosStartSimulation.srv
  simRosGetJointMatrix.srv
  simRosCreateDummy.srv
  simRosSetStringSignal.srv
  simRosAddStatusbarMessage.srv
  simRosReadCollision.srv
  simRosDisablePublisher.srv
  simRosAuxiliaryConsoleClose.srv
  simRosGetDialogResult.srv
  simRosSetObjectParent.srv
  simRosGetObjectIntParameter.srv
  simRosGetUIHandle.srv
  simRosRemoveObject.srv
  simRosGetObjectHandle.srv
  simRosLoadScene.srv
  simRosSetJointPosition.srv
  simRosStopSimulation.srv
  simRosGetAndClearStringSignal.srv
  simRosSetBooleanParameter.srv
  simRosSetSphericalJointMatrix.srv
  simRosSetJointTargetPosition.srv
  simRosSetJointState.srv
  simRosGetJointState.srv
  simRosClearStringSignal.srv
  simRosSetObjectIntParameter.srv
  simRosGetObjects.srv
  simRosEnableSubscriber.srv
  simRosGetObjectFloatParameter.srv
  simRosGetUIEventButton.srv
  simRosSynchronousTrigger.srv
  simRosGetObjectGroupData.srv
  simRosAppendStringSignal.srv
  simRosGetIntegerParameter.srv
  simRosGetStringSignal.srv
  simRosGetModelProperty.srv
  simRosSetModelProperty.srv
  simRosLoadModel.srv
  simRosSetObjectPosition.srv
  simRosReadDistance.srv
  simRosGetFloatingParameter.srv
  simRosEnablePublisher.srv
  simRosAuxiliaryConsoleShow.srv
  simRosEndDialog.srv
  simRosGetVisionSensorImage.srv
  simRosSetObjectFloatParameter.srv
  simRosSetJointTargetVelocity.srv
  simRosSetJointForce.srv
  simRosSetArrayParameter.srv
  simRosAuxiliaryConsolePrint.srv
  simRosSetUIButtonProperty.srv
  simRosGetLastErrors.srv
  simRosSetIntegerSignal.srv
  simRosReadProximitySensor.srv
  simRosGetVisionSensorDepthBuffer.srv
)

#common commands for building c++ executables and libraries
#add_library(${PROJECT_NAME} src/example.cpp)
#target_link_libraries(${PROJECT_NAME} another_library)
#
# CATKIN_MIGRATION: removed during catkin migration
# rosbuild_add_boost_directories()
#find_package(Boost REQUIRED COMPONENTS thread)

include_directories(${Boost_INCLUDE_DIRS})
include_directories(${catkin_INCLUDE_DIRS} ${OpenCV_INCLUDE_DIRS} )
#target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES})

#add_executable(example examples/example.cpp)
#target_link_libraries(example ${PROJECT_NAME})
## Generate added messages and services with any dependencies listed here
generate_messages(
    DEPENDENCIES geometry_msgs std_msgs sensor_msgs
)

# catkin_package parameters: http://ros.org/doc/groovy/api/catkin/html/dev_guide/generated_cmake_api.html#catkin-package
# TODO: fill in what other packages will need to use this package
catkin_package(
    DEPENDS roscpp std_msgs sensor_msgs opencv2
    CATKIN_DEPENDS message_runtime
    INCLUDE_DIRS # TODO include
    LIBRARIES # TODO
)