include(FetchContent)

# ���������� Catch2 �� GitHub
FetchContent_Declare(
    catch2
    GIT_REPOSITORY https://github.com/catchorg/Catch2.git
    GIT_TAG v3.4.0
)

FetchContent_MakeAvailable(catch2)
list(APPEND CMAKE_MODULE_PATH ${catch2_SOURCE_DIR}/extras)

# �������� ������������ ����� ������
add_executable(threads_tests
    src/tests.cpp
)

# �������� � Catch2 � ������������ ������� (���������� ����������, � �� exe)
target_link_libraries(threads_tests PRIVATE
    Catch2::Catch2WithMain
    threads_server_lib
    threads_client_lib
)

# ���������� ����� ��� ���������� � ���������� ������� � Linux
if(NOT WIN32)
    target_compile_options(threads_tests PUBLIC -pthread)
    target_link_options(threads_tests PUBLIC -pthread)
endif()

# ����������� ������
include(CTest)
include(Catch)
catch_discover_tests(threads_tests)