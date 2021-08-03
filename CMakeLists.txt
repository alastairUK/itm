# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
#
cmake_minimum_required (VERSION 3.15)

project ("ITM")

set(CMAKE_CXX_STANDARD 11)

include_directories(${PROJECT_SOURCE_DIR}/include)

set(Headers
    include/Enums.h
    include/Errors.h
    include/itm.h
    include/Warnings.h)

set(Sources
    src/ComputeDeltaH.cpp                                     
    src/DiffractionLoss.cpp                                   
    src/FindHorizons.cpp                                      
    src/FreeSpaceLoss.cpp                                     
    src/FresnelIntegral.cpp                                   
    src/H0Function.cpp                                        
    src/InitializeArea.cpp                                    
    src/InitializePointToPoint.cpp                            
    src/InverseComplementaryCumulativeDistributionFunction.cpp
    src/itm_area.cpp                                          
    src/itm_p2p.cpp                                           
    src/KnifeEdgeDiffraction.cpp                              
    src/LinearLeastSquaresFit.cpp                             
    src/LineOfSightLoss.cpp                                   
    src/LongleyRice.cpp                                       
    src/QuickPfl.cpp                                          
    src/SigmaHFunction.cpp                                    
    src/SmoothEarthDiffraction.cpp                            
    src/TerrainRoughness.cpp                                  
    src/TroposcatterLoss.cpp                                  
    src/ValidateInputs.cpp                                    
    src/Variability.cpp)

# Add source to this project's executable.
add_library(${PROJECT_NAME} STATIC ${Sources} ${Headers})

if(MSVC)
    target_compile_options(${PROJECT_NAME} PRIVATE /W4 /WX)
else()
    target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -pedantic -Werror)
endif()