# Random_Joke_Generator
Its a random joke generator clicking the button, "New joke" will give you a new joke

import React, { useState } from 'react';

const Random_Joke_Generator = () => {
  const [joke, setJoke] = useState('');

  const fetch_us_Joke = async () => {
    try {
      const response = await fetch('https://official-joke-api.appspot.com/random_joke');
      const data = await response.json();
      setJoke(`${data.setup} ${data.punchline}`);
    } catch (error) {
      console.log(error);
    }
  };

  const Give_us_New_Joke = () => {
    fetch_us_Joke();
  };

  return (
    <div>
      <h1 style={{color: "red"}}>Random Joke Generator</h1>
      <p>{joke}</p>
      <center><button onClick={Give_us_New_Joke}>New Joke</button></center>
    </div>
  );
};

export default Random_Joke_Generator;

