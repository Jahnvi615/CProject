[SetUp]
public void Setup()
{
    var options = new DbContextOptionsBuilder<ApplicationDbContext>()
        .UseInMemoryDatabase(databaseName: "TestDatabase")
        .Options;

    _dbContext = new ApplicationDbContext(options);
    _mockQuoteService = new Mock<IQuoteService>();
    
    // Make sure the logger type matches the controller's logger type
    _mockLogger = new Mock<ILogger<QuoteController>>();  // Use QuoteController instead of WeatherForecastController
    
    _controller = new QuoteController(_mockQuoteService.Object, _dbContext, _mockLogger.Object);
}
