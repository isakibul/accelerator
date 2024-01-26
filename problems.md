<!-- nested dropdown -->

import { useState } from "react";

const countries = [
  {
    name: "Bangladesh",
    cities: ['Dhaka', 'Rajshahi']
  },
  {
    name: "India",
    cities: ['Mumbai', 'Chennai']
  },
];


const App = () => {
  const [selectedCountry, setSelectedCountry] = useState('');

  return (
    <div>
      <select value={selectedCountry} onChange={(e) => setSelectedCountry(e.target.value)}>
        <option value="">Select Country</option>
        {countries.map((country, idx) => (
          <option key={idx} value={country.name}>
            {country.name}
          </option>
        ))}
      </select>

      {selectedCountry && (
        <select>
          {countries.find((country) => country.name === selectedCountry)?.cities.map((city, idx) => (
            <option key={idx}>{city}</option>
          ))}
        </select>
      )}
    </div>
  );
};

export default App;