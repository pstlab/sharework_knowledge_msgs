##############################################################################
# CMake
##############################################################################

cmake_minimum_required(VERSION 2.8.3)
project(sharework_knowledge_msgs)

##############################################################################
# Catkin
##############################################################################

#find_package(catkin REQUIRED rosjava_build_tools)
find_package(catkin REQUIRED COMPONENTS
	message_generation
	message_runtime
	std_msgs
)

add_service_files(
	DIRECTORY
	srv
)

add_message_files(
	DIRECTORY
	msg
)

generate_messages(DEPENDENCIES std_msgs)

# Set the gradle targets you want catkin's make to run by default, e.g.
#   catkin_rosjava_setup(installDist)
# Note that the catkin_create_rosjava_xxx scripts will usually automatically
# add tasks to this for you when you create subprojects.
catkin_rosjava_setup()

catkin_package()

##############################################################################
# Installation
##############################################################################

# Change this to match the maven group name you have specified in the
# allprojects closure the root build.gradle
install(DIRECTORY ${CATKIN_DEVEL_PREFIX}/${CATKIN_GLOBAL_MAVEN_DESTINATION}/com/github/rosjava/${PROJECT_NAME}/
        DESTINATION ${CATKIN_GLOBAL_MAVEN_DESTINATION}/com/github/rosjava/${PROJECT_NAME})
