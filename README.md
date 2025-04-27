using Moq;
using NUnit.Framework;
using Microsoft.AspNetCore.Mvc;
using DFBPI.Controllers;
using DFBPI.Services;
using DFBPI.Model.Dto;
using Microsoft.AspNetCore.Http;
using System.Threading.Tasks;
using Microsoft.Extensions.Configuration;
using DFBPI.Data;
using Microsoft.EntityFrameworkCore;

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
            // Mock services
            _authServiceMock = new Mock<IAuthService>();
            _configurationMock = new Mock<IConfiguration>();

            // Initialize controller with mocked services
            _userController = new UserController(_configurationMock.Object, _authServiceMock.Object, null); // Pass null for DbContext if not needed for controller logic
        }

        [TearDown]
        public void TearDown()
        {
            // Clean up if necessary
            // No need to dispose DbContext because it's not used directly in this case
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
            Assert.IsInstanceOf<ActionResult>(result);  // Ensure result is ActionResult type
            Assert.IsInstanceOf<OkObjectResult>(result.Result);  // Check if the inner result is OkObjectResult
            var okResult = result.Result as OkObjectResult;
            Assert.IsNotNull(okResult);
            Assert.AreEqual("Login successful and token set in cookies.", okResult.Value);
        }

        // Additional test cases can go here
    }
}
