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
add_executable(winapi_tests
    src/tests.cpp
)

# �������� � Catch2 � ������������ WinAPI (���������� ����������, � �� exe)
target_link_libraries(winapi_tests PRIVATE
    Catch2::Catch2WithMain
    winapi_server_lib
    winapi_client_lib
)

# ����������� ������
include(CTest)
include(Catch)
catch_discover_tests(winapi_tests)