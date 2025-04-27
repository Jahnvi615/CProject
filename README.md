using Moq;
using NUnit.Framework;
using Microsoft.AspNetCore.Mvc;
using DFBPI.Controllers;
using DFBPI.Services;
using DFBPI.Model.Dto;
using Microsoft.AspNetCore.Http;
using System.Threading.Tasks;
using Microsoft.Extensions.Configuration;

namespace DFBPI.Tests
{
    [TestFixture]
    public class UserControllerTests
    {
        private Mock<IAuthService> _authServiceMock;
        private Mock<IConfiguration> _configurationMock;
        private UserController _userController;

        [SetUp]
        public void SetUp()
        {
            _authServiceMock = new Mock<IAuthService>();
            _configurationMock = new Mock<IConfiguration>();
            _userController = new UserController(_configurationMock.Object, _authServiceMock.Object, null);
        }

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
            var okResult = result as OkObjectResult;
            Assert.IsNotNull(okResult);
            Assert.AreEqual("Login successful and token set in cookies.", okResult.Value);
        }

        // You can add more test cases, e.g. for invalid credentials, etc.
    }
}
