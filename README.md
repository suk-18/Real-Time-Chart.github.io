# Real-Time-Chart

This is a simple web application which help the users understand how to use Chart.js to create a line chart that updates in real time.

## Setup

1.This repository should be cloned to your local machines.

2.Install the dependencies by running npm install.

3.Start the server by running npm start.

## Explanation of Code

To understand the code of this project we need to follow the following steps as below:

## HTML

```

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Real-Time Chart</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div id="div">
      <canvas id="realTimeChart"></canvas>
    </div>

    <script src="index.js"></script>
  </body>
</html>

```

## CSS

```

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    background-color:  pink;
  }
  canvas {
    max-width: 100%;
    height: auto;
  }
  #div {
    width: 80%;
    margin: auto;
  }

```

## JS

```

const ctx = document.getElementById("realTimeChart").getContext("2d");
let chart;
const initialData = {
  labels: [],
  datasets: [
    {
      label: "Price",
      data: [],
      borderColor: "rgba(75, 192, 192, 1)",
      borderWidth: 1,
      fill: false,
    },
  ],
};
const chartConfig = {
  type: "line",
  data: initialData,
  options: {
    scales: {
      x: {
        type: "linear",
        position: "bottom",
        title: {
          display: true,
          text: "Time",
        },
      },
      y: {
        beginAtZero: true,
        title: {
          display: true,
          text: "Price",
        },
      },
    },
    animation: false,
  },
};
chart = new Chart(ctx, chartConfig);
function addData() {
  const newData = Math.random() * 500;
  chart.data.labels.push(chart.data.labels.length);
  chart.data.datasets[0].data.push(newData);
  chart.update();
}
setInterval(addData, 1000);

```

**Hosted LInk**:https://suk-18.github.io/Real-Time-Chart.github.io/

