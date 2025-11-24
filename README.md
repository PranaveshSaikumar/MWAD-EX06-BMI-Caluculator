# Ex06 BMI Calculator
## Date: 24-11-25

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM
```
BMI.jsx
import { useState } from "react";

function BMICalculator() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBMI] = useState(null);
  const [status, setStatus] = useState("");

  const calculateBMI = () => {
    const h = height / 100; // convert cm → meters
    const result = weight / (h * h);
    const rounded = result.toFixed(2);
    setBMI(rounded);

    if (result < 18.5) setStatus("Underweight");
    else if (result < 24.9) setStatus("Normal weight");
    else if (result < 29.9) setStatus("Overweight");
    else setStatus("Obesity");
  };

  return (
    <div style={{ textAlign: "center", marginTop: 50 }}>
      <h2>BMI Calculator</h2>

      <input
        type="number"
        placeholder="Enter weight (kg)"
        value={weight}
        onChange={(e) => setWeight(e.target.value)}
        style={{ margin: 10, padding: 10 }}
      />

      <input
        type="number"
        placeholder="Enter height (cm)"
        value={height}
        onChange={(e) => setHeight(e.target.value)}
        style={{ margin: 10, padding: 10 }}
      />

      <br />

      <button onClick={calculateBMI} style={{ padding: "10px 20px" }}>
        Calculate BMI
      </button>

      {bmi && (
        <div style={{ marginTop: 20 }}>
          <h3>Your BMI: {bmi}</h3>
          <p>Status: {status}</p>
        </div>
      )}
    </div>
  );
}

export default BMICalculator;
```
```
BMIHome.jsx
import { Link } from "react-router-dom";

function Home() {
  return (
    <div style={{ textAlign: "center", marginTop: 50 }}>
      <h1>Welcome to BMI Calculator</h1>
      <p>Click below to calculate your BMI</p>

      <Link to="/bmi">
        <button style={{ padding: "10px 20px" }}>Go to Calculator</button>
      </Link>
    </div>
  );
}

export default Home;
```
```
App.jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import Home from "./EXPS/BMIHome";
import BMICalculator from "./EXPS/BMI";

function App() {
  return (
    <BrowserRouter>
      <nav style={{ padding: 20 }}>
        <Link to="/" style={{ marginRight: 20 }}>Home</Link>
        <Link to="/bmi">BMI Calculator</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/bmi" element={<BMICalculator />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

## OUTPUT

<img width="792" height="835" alt="image" src="https://github.com/user-attachments/assets/ae667b8c-1a04-4e70-900d-63d4e35563e7" />

## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
