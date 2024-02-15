ChatGPT 3.5

User
Create login page using JWT authentication in react js 

ChatGPT
Certainly! Here's a basic example of a login page using JWT authentication in React.js. Make sure you have the necessary dependencies installed, like axios for handling HTTP requests.

Install required dependencies:
bash
Copy code
npm install react react-dom react-router-dom axios
Create a simple login component (Login.js):
jsx
Copy code
import React, { useState } from 'react';
import { useHistory } from 'react-router-dom';
import axios from 'axios';

const Login = () => {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');
  const history = useHistory();

  const handleLogin = async () => {
    try {
      const response = await axios.post('YOUR_API_ENDPOINT/login', {
        username,
        password,
      });

      // Assuming your server sends back a token upon successful login
      const token = response.data.token;

      // Store the token in localStorage or a secure way of your choice
      localStorage.setItem('token', token);

      // Redirect to a protected route
      history.push('/dashboard');
    } catch (error) {
      console.error('Login failed:', error.message);
    }
  };

  return (
    <div>
      <h2>Login</h2>
      <form>
        <label>
          Username:
          <input
            type="text"
            value={username}
            onChange={(e) => setUsername(e.target.value)}
          />
        </label>
        <br />
        <label>
          Password:
          <input
            type="password"
            value={password}
            onChange={(e) => setPassword(e.target.value)}
          />
        </label>
        <br />
        <button type="button" onClick={handleLogin}>
          Login
        </button>
      </form>
    </div>
  );
};

export default Login;
