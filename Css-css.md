``` bash
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f9;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.calculator-container {
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    width: 300px;
    text-align: center;
}

#pantalla {
    width: 100%;
    height: 50px;
    margin-bottom: 10px;
    font-size: 20px;
    text-align: right;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.button-container {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

.button {
    width: 100%;
    height: 50px;
    font-size: 18px;
    border: none;
    border-radius: 5px;
    background-color: #f0f0f0;
    cursor: pointer;
}

.button:hover {
    background-color: #ddd;
}

.equal {
    background-color: #4CAF50;
    color: white;
}

.clear {
    background-color: #FF6347;
    color: white;
}
```
