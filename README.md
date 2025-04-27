[Test]
public async Task CreateQuoteAsync_ReturnsValidQuoteObject()
{
    // Arrange
    var request = new CreateQuoteRequestDto
    {
        Name = "John Doe",
        Email = "john.doe@example.com",
        PhoneNo = "1234567890",
        PropertyAddress = "123 Main St",
        PropertyType = "House",
        ConstructionType = "Brick",
        Age = 5,
        Tier = 1,
        HasFireAlarm = true,
        HasSprinklerSystem = true,
        HasSecurityCameras = true,
        HasSecurityGuards = false,
        BuildingSumInsured = 500000m,
        ContentsSumInsured = 200000m,
        StartDate = DateTime.UtcNow.AddDays(1),
        EndDate = DateTime.UtcNow.AddYears(1),
        PropertyArea = 250
    };

    var userId = Guid.NewGuid(); // Create a new user ID for the test
    // Simulating a user retrieval logic for the test, or you can mock the user data
    var user = new ApplicationUser { UserId = userId, Role = RoleType.User };
    _dbContext.Users.Add(user);
    await _dbContext.SaveChangesAsync();

    // Act
    var result = await _quoteService.CreateQuoteAsync(request, userId); // Call the service method directly

    // Assert
    Assert.IsNotNull(result);
    Assert.AreEqual("John Doe", result.Name);
    Assert.AreEqual("john.doe@example.com", result.Email);
    Assert.AreEqual(500000m, result.BuildingSumInsured);
    Assert.AreEqual(200000m, result.ContentsSumInsured);
    Assert.AreEqual("Silver", result.PlanType.ToString()); // Check if default plan is Silver
    Assert.AreEqual(750000m, result.GoldCoverageAmount); // Total coverage for Gold plan
    Assert.AreEqual(500000m, result.SilverCoverageAmount); // Total coverage for Silver plan
    Assert.AreEqual(1000000m, result.PlatinumCoverageAmount); // Total coverage for Platinum plan
    Assert.AreEqual("123 Main St", result.PropertyAddress);
}
