[Test]
public async Task Login_ShouldReturnOk_WhenCredentialsAreValid()
{
    // Arrange
    var userDto = new UserDto
    {
        Username = "testuser",
        Password = "testpassword"
    };

    var expectedToken = "valid-jwt-token";
    _authServiceMock.Setup(service => service.LoginAsync(It.IsAny<UserDto>()))
        .ReturnsAsync(expectedToken);

    // Act
    var result = await _userController.Login(userDto);

    // Assert
    Assert.IsInstanceOf<OkObjectResult>(result); // Ensure result is of OkObjectResult type
    var okResult = result as OkObjectResult;
    Assert.IsNotNull(okResult);
    Assert.AreEqual("Login successful and token set in cookies.", okResult.Value);
}
