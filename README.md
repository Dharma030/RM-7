# RM-7

// Step 1: Fetch the data from the API
fetch("https://restcountries.com/v3.1/all")
  .then(response => response.json())
  .then(data => {
    // Step 2: Get all the countries from Asia continent/region using Filter function
    const asianCountries = data.filter(country => country.region === "Asia");

    console.log("Asian Countries:");
    asianCountries.forEach(country => console.log(country.name.common));
    console.log("-----------------------------");

    // Step 3: Get all the countries with a population of less than 2 lakhs using Filter function
    const countriesWithPopulationLessThan2Lakhs = data.filter(country => country.population < 200000);

    console.log("Countries with Population Less than 2 Lakhs:");
    countriesWithPopulationLessThan2Lakhs.forEach(country => console.log(country.name.common));
    console.log("-----------------------------");

    // Step 4: Print the following details name, capital, flag using forEach function
    console.log("Country Details:");
    data.forEach(country => {
      console.log("Name:", country.name.common);
      console.log("Capital:", country.capital);
      console.log("Flag:", country.flags.svg);
      console.log("-----------------------------");
    });

    // Step 5: Print the total population of countries using reduce function
    const totalPopulation = data.reduce((accumulator, country) => accumulator + country.population, 0);

    console.log("Total Population:", totalPopulation);
    console.log("-----------------------------");

    // Step 6: Print the country which uses US Dollars as currency
    const usDollarCountries = data.filter(country => country.currencies.USD);

    console.log("Countries using US Dollars:");
    usDollarCountries.forEach(country => console.log(country.name.common));
    console.log("-----------------------------");
  })
  .catch(error => console.log("Error fetching data:", error));
