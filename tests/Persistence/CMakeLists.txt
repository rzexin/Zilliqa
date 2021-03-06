if(CMAKE_CONFIGURATION_TYPES)
    foreach(config ${CMAKE_CONFIGURATION_TYPES})
        configure_file(${CMAKE_SOURCE_DIR}/constants.xml ${config}/constants.xml COPYONLY)
    endforeach(config)
else(CMAKE_CONFIGURATION_TYPES)
    configure_file(${CMAKE_SOURCE_DIR}/constants.xml constants.xml COPYONLY)
endif(CMAKE_CONFIGURATION_TYPES)

add_executable(Test_MetaPersistence Test_MetaPersistence.cpp)
target_include_directories(Test_MetaPersistence PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_link_libraries(Test_MetaPersistence PUBLIC Crypto Utils Persistence)
add_test(NAME Test_MetaPersistence COMMAND Test_MetaPersistence)

add_executable(Test_DSPersistence Test_DSPersistence.cpp)
target_include_directories(Test_DSPersistence PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_link_libraries(Test_DSPersistence PUBLIC Crypto AccountData BlockChainData Utils Persistence)
add_test(NAME Test_DSPersistence COMMAND Test_DSPersistence)

add_executable(Test_TxPersistence Test_TxPersistence.cpp)
target_include_directories(Test_TxPersistence PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_link_libraries(Test_TxPersistence PUBLIC Crypto AccountData BlockChainData Utils Persistence)
add_test(NAME Test_TxPersistence COMMAND Test_TxPersistence)

add_executable(Test_TxBody Test_TxBody.cpp)
target_include_directories(Test_TxBody PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_link_libraries(Test_TxBody PUBLIC Crypto AccountData BlockChainData Utils Persistence)
add_test(NAME Test_TxBody COMMAND Test_TxBody)

add_executable(ReadBlock ReadBlock.cpp)
target_include_directories(ReadBlock PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_link_libraries(ReadBlock PUBLIC Crypto AccountData BlockChainData Utils Persistence)
add_test(NAME ReadBlock COMMAND ReadBlock)

#add_executable(ReadTxBlock ReadTxBlock.cpp)
#target_include_directories(ReadTxBlock PUBLIC ${CMAKE_SOURCE_DIR}/src)
#target_link_libraries(ReadTxBlock PUBLIC Crypto AccountData BlockChainData Utils Persistence)

#add_executable(ReadTransactions ReadTransactions.cpp)
#target_include_directories(ReadTransactions PUBLIC ${CMAKE_SOURCE_DIR}/src)
#target_link_libraries(ReadTransactions PUBLIC Crypto AccountData BlockChainData Utils Persistence)