# User-specific paths
WORK_DIR=/hpf/projects/mkoziarski/slu/quickvina/dist/Vina-GPU-2.1/AutoDock-Vina-GPU-2.1
BOOST_LIB_PATH=/hpf/projects/mkoziarski/slu/quickvina/dist/boost_1_83_0
OPENCL_LIB_PATH=/hpf/projects/mkoziarski/slu/.conda/envs/rgfn
OPENCL_VERSION=-DOPENCL_2_0
GPU_PLATFORM=-DNVIDIA_PLATFORM
DOCKING_BOX_SIZE=-DSMALL_BOX

# Include paths
BOOST_INC_PATH=-I$(BOOST_LIB_PATH) -I$(BOOST_LIB_PATH)/boost
VINA_GPU_INC_PATH=-I$(WORK_DIR)/lib -I$(WORK_DIR)/OpenCL/inc
OPENCL_INC_PATH=-I$(OPENCL_LIB_PATH)/include

# Libraries and linking
LIB1=-lboost_program_options -lboost_system -lboost_filesystem
LIB2=-lstdc++ -lstdc++fs
LIB3=-lm -lpthread
LIB_PATH=-L/hpf/projects/mkoziarski/slu/quickvina/dist/boost/lib -L$(OPENCL_LIB_PATH)/lib64
OPENCL_LIB=/usr/lib64/libOpenCL.so.1  # Direct path to OpenCL library

# Source files
SRC=./lib/*.cpp ./OpenCL/src/wrapcl.cpp $(BOOST_LIB_PATH)/libs/thread/src/pthread/thread.cpp $(BOOST_LIB_PATH)/libs/thread/src/pthread/once.cpp

# Compiler macros
MACRO=$(OPENCL_VERSION) $(GPU_PLATFORM) $(DOCKING_BOX_SIZE) -DBOOST_TIMER_ENABLE_DEPRECATED

# Targets
all: out

out: ./main/main.cpp
	gcc -o AutoDock-Vina-GPU-2.1 $(BOOST_INC_PATH) $(VINA_GPU_INC_PATH) $(OPENCL_INC_PATH) ./main/main.cpp -O3 $(SRC) $(LIB1) $(LIB2) $(LIB3) $(OPENCL_LIB) $(LIB_PATH) $(MACRO) -DNDEBUG

source: ./main/main.cpp
	gcc -o AutoDock-Vina-GPU-2.1 $(BOOST_INC_PATH) $(VINA_GPU_INC_PATH) $(OPENCL_INC_PATH) ./main/main.cpp -O3 $(SRC) $(LIB1) $(LIB2) $(LIB3) $(OPENCL_LIB) $(LIB_PATH) $(MACRO) -DNDEBUG -DBUILD_KERNEL_FROM_SOURCE

debug: ./main/main.cpp
	gcc -o AutoDock-Vina-GPU-2.1 $(BOOST_INC_PATH) $(VINA_GPU_INC_PATH) $(OPENCL_INC_PATH) ./main/main.cpp -g $(SRC) $(LIB1) $(LIB2) $(LIB3) $(OPENCL_LIB) $(LIB_PATH) $(MACRO) -DBUILD_KERNEL_FROM_SOURCE

clean:
	rm AutoDock-Vina-GPU-2.1
