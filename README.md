using NUnit.Framework;
using Moq;
using DFBPI.Controllers;
using DFBPI.Services;
using DFBPI.Data;
using DFBPI.Model;
using DFBPI.Model.Dto;
using Microsoft.Extensions.Logging;
using Microsoft.AspNetCore.Mvc;
using Microsoft.EntityFrameworkCore;
using System;
using System.Threading.Tasks;

namespace DFBPI.Tests
{
    public class QuoteControllerTests
    {
        private Mock<IQuoteService> _mockQuoteService;
        private Mock<ILogger<QuoteController>> _mockLogger;
        private ApplicationDbContext _dbContext;
        private QuoteController _controller;

        [SetUp]
        public void Setup()
        {
            // Setting up the in-memory database for testing
            var options = new DbContextOptionsBuilder<ApplicationDbContext>()
                .UseInMemoryDatabase(databaseName: "TestDatabase")
                .Options;

            _dbContext = new ApplicationDbContext(options);
            _mockQuoteService = new Mock<IQuoteService>();
            _mockLogger = new Mock<ILogger<QuoteController>>();
            _controller = new QuoteController(_mockQuoteService.Object, _dbContext, _mockLogger.Object);
        }

        [Test]
        public async Task CreatePolicyQuote_ValidRequest_ReturnsOkResult()
        {
            // Arrange
            var req = new CreateQuoteRequestDto
            {
                Name = "John Doe",
                Email = "john@example.com",
                PhoneNo = "1234567890",
                PropertyAddress = "123 Main St",
                PropertyType = "Residential",
                ConstructionType = "Brick",
                Age = 5,
                Tier = 1,
                HasFireAlarm = true,
                HasSprinklerSystem = false,
                HasSecurityCameras = true,
                HasSecurityGuards = false,
                ContentsSumInsured = 10000,
                BuildingSumInsured = 50000,
                StartDate = DateTime.UtcNow,
                EndDate = DateTime.UtcNow.AddYears(1),
                PropertyArea = 1500
            };

            // Mocking the CalculateFinalPremium method
            _mockQuoteService.Setup(x => x.CalculateFinalPremium(It.IsAny<string>(), It.IsAny<string>(), It.IsAny<int>(), It.IsAny<bool>(), It.IsAny<bool>(), It.IsAny<bool>(), It.IsAny<bool>(), It.IsAny<int>(), It.IsAny<int>(), It.IsAny<int>(), It.IsAny<int>(), It.IsAny<string>()))
                .Returns(1000m);

            // Act
            var result = await _controller.CreatePolicyQuote(req);

            // Assert
            var okResult = result as OkObjectResult;
            Assert.IsNotNull(okResult);
            Assert.AreEqual(200, okResult.StatusCode);
        }
    }
}
