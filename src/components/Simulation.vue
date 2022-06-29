
<template>
  <div class="bg-white p-10 shadow-lg w-full">
    <h1
      class="
        text-4xl
        font-extrabold
        border-b-2 border-blue-400
        pb-5
        text-slate-600
      "
    >
      Simulador de estimación de proyectos
      <span class="text-slate-300 text-base font-medium">(Monte Carlo)</span>
    </h1>

    <div class="flex mb-9 mt-14">
      <div class="mr-3 text-blue-700">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-12 w-12"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-3 7h3m-3 4h3m-6-4h.01M9 16h.01"
          />
        </svg>
      </div>
      <div>
        <h2 class="mb-1 uppercase text-slate-600 font-medium text-lg">
          Agregar Tareas:
        </h2>
        <p class="text-slate-500 text-sm">Agrega las tareas para simular</p>
      </div>
    </div>
    <table
      class="table-auto overflow-hidden rounded-2xl border-collapse w-full"
    >
      <thead class="bg-slate-100 pt-5">
        <tr>
          <th
            class="
              border-b
              dark:border-slate-600
              font-medium
              p-4
              pl-8
              pb-3
              text-slate-400
              dark:text-black-400
              text-left
            "
          >
            #
          </th>
          <th
            class="
              border-b
              dark:border-slate-600
              font-medium
              p-4
              pl-8
              pb-3
              text-slate-400
              dark:text-black-400
              text-left
            "
          >
            Tarea
          </th>
          <th
            class="
              border-b
              dark:border-slate-600
              font-medium
              p-4
              pl-8
              pb-3
              text-slate-400
              dark:text-black-400
              text-left
            "
          >
            Tiempo min.
          </th>
          <th
            class="
              border-b
              dark:border-slate-600
              font-medium
              p-4
              pl-8
              pb-3
              text-slate-400
              dark:text-black-400
              text-left
            "
          >
            Tiempo max.
          </th>
          <th
            class="
              border-b
              dark:border-slate-600
              font-medium
              p-4
              pl-8
              pb-3
              text-slate-400
              dark:text-black-400
              text-left
            "
          >
            Confianza (%)
          </th>
          <th
            class="
              border-b
              dark:border-slate-600
              font-medium
              p-4
              pl-8
              pb-3
              text-slate-400
              dark:text-black-400
              text-left
            "
          >
            Costo por hora
          </th>
          <th
            class="
              border-b
              dark:border-slate-600
              font-medium
              p-4
              pl-8
              pb-3
              text-slate-400
              dark:text-black-400
              text-left
            "
          >
            Acción
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td
            class="
              border-b border-slate-300
              dark:border-slate-700
              p-4
              pl-8
              text-slate-500
              dark:text-slate-400
              w-2/12
            "
          >
            {{ index + 1 }}
          </td>
          <td
            class="
              border-b border-slate-300
              dark:border-slate-700
              p-4
              pl-8
              text-slate-500
              dark:text-slate-400
              w-2/12
            "
          >
            <input
              v-model="task.name"
              type="text"
              class="
                border border-slate-300
                p-2
                text-sm
                w-full
                focus:outline-none focus:bg-slate-50
              "
            />
          </td>
          <td
            class="
              border-b border-slate-300
              dark:border-slate-700
              p-4
              pl-8
              text-slate-500
              dark:text-slate-400
              w-2/12
            "
          >
            <input
              v-model="task.min"
              type="text"
              class="
                border border-slate-300
                p-2
                text-sm
                w-full
                focus:outline-none focus:bg-slate-50
              "
            />
          </td>
          <td
            class="
              border-b border-slate-300
              dark:border-slate-700
              p-4
              pl-8
              text-slate-500
              dark:text-slate-400
              w-2/12
            "
          >
            <input
              v-model="task.max"
              type="text"
              class="
                border border-slate-300
                p-2
                text-sm
                w-full
                focus:outline-none focus:bg-slate-50
              "
            />
          </td>
          <td
            class="
              border-b border-slate-300
              dark:border-slate-700
              p-4
              pl-8
              text-slate-500
              dark:text-slate-400
              w-2/12
            "
          >
            <input
              v-model="task.confidence"
              type="text"
              class="
                border border-slate-300
                p-2
                text-sm
                w-full
                focus:outline-none focus:bg-slate-50
              "
            />
          </td>
          <td
            class="
              border-b border-slate-300
              dark:border-slate-700
              p-4
              pl-8
              text-slate-500
              dark:text-slate-400
              w-2/12
            "
          >
            <input
              v-model="task.cost"
              type="text"
              class="
                border border-slate-300
                p-2
                text-sm
                w-full
                focus:outline-none focus:bg-slate-50
              "
            />
          </td>
          <td
            class="
              border-b border-slate-300
              dark:border-slate-700
              p-4
              pl-8
              text-slate-500
              dark:text-slate-400
            "
          >
            <button
              @click="handleDeleteTask(index)"
              class="
                border-2 border-red-400
                text-red-400
                font-semibold
                py-1
                p-5
                rounded-2xl
                hover:bg-red-400 hover:text-white
                text-sm
              "
            >
              Borrar
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <button
      @click="handleAddTask()"
      class="
        border-2 border-blue-400
        px-4
        py-1
        font-medium
        text-blue-400
        hover:bg-blue-400 hover:text-white
        mt-4
        text-sm
      "
    >
      Agregar Tarea
    </button>

    <div class="flex mt-16 mb-9">
      <div class="mr-3 text-blue-700">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-12 w-12"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M12 6V4m0 2a2 2 0 100 4m0-4a2 2 0 110 4m-6 8a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4m6 6v10m6-2a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4"
          />
        </svg>
      </div>
      <div>
        <h2 class="mb-1 uppercase text-slate-600 font-medium text-lg">
          Opciones de Simulador
        </h2>
        <p class="text-slate-500 text-sm">
          Seleccione las opciones de la simulación
        </p>
      </div>
    </div>

    <label class="font-medium text-slate-400" for="numberSimulations">
      Número de simulaciones:
    </label>
    <input
      class="
        mr-5
        ml-5
        border border-slate-300
        p-2
        text-sm
        w-30
        focus:outline-none focus:bg-slate-50
      "
      v-model="numberSimulations"
      type="number"
      id="numberSimulations"
    />

    <!--     <label class="font-medium text-slate-400" for="">Limitar los valores atípicos del gráfico: </label>
    <input type="checkbox" name="" id=""> -->

    <div class="text-center mt-10">
      <button
        @click="handleRunSimulation()"
        class="px-6 py-3 bg-blue-700 text-white font-medium hover:bg-blue-900"
      >
        Iniciar Simulación
      </button>
    </div>

    <div class="flex mt-16 mb-9">
      <div class="mr-3 text-blue-700">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-12 w-12"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M7 12l3-3 3 3 4-4M8 21l4-4 4 4M3 4h18M4 4h16v12a1 1 0 01-1 1H5a1 1 0 01-1-1V4z"
          />
        </svg>
      </div>
      <div>
        <h2 class="mb-1 uppercase text-slate-600 font-medium text-lg">
          Resultados
        </h2>
        <p class="text-slate-500 text-sm">Consulte los resultados obtenidos</p>
      </div>
    </div>

    <div class="mt-5">
      <p>
        Tiempo de corrida de la simulación (ms):
        <template v-if="output != null"> {{ output.runningTime }}</template>
      </p>
    </div>

    <div class="mt-5">
      <h2 class="flex items-center">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="mr-3 h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M9 5l7 7-7 7"
          />
        </svg>
        Tiempo Estimado
      </h2>
      <template v-if="output != null">
        <p class="font-medium text-slate-400">
          Tiempo medio: {{ output.times.median }}
        </p>
        <p class="font-medium text-slate-400">
          Rango probable: {{ output.times.likelyMin }} -
          {{ output.times.likelyMax }}
        </p>
        <p class="font-medium text-slate-400">
          Tiempo minimo: {{ output.times.min }}
        </p>
        <p class="font-medium text-slate-400">
          Tiempo máximo: {{ output.times.max }}
        </p>
        <p class="font-medium text-slate-400">
          Desviación estandar: {{ output.times.sd }}
        </p>
      </template>
    </div>

    <div class="mt-5">
      <h2 class="flex items-center">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="mr-3 h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M9 5l7 7-7 7"
          />
        </svg>
        Costos Estimados
      </h2>
      <template v-if="output != null">
        <p class="font-medium text-slate-400">
          Rango probable: {{ output.costs.likelyMin }}
        </p>
        <p class="font-medium text-slate-400">
          Costo minimo: {{ output.costs.min }}
        </p>
        <p class="font-medium text-slate-400">
          Costo máximo: {{ output.costs.max }}
        </p>
        <p class="font-medium text-slate-400">
          Desviación estandar: {{ output.costs.sd }}
        </p>
      </template>
    </div>

    <div class="w-full flex justify-center mt-5">
      <div id="histogram"></div>
    </div>
  </div>
</template>

<script type="module">
import * as d3 from "d3";

export default {
  data() {
    return {
      tasks: [
       {name: '', min: '', max: '' , confidence: '', cost: '' },
      ],
      numberSimulations: 100,
      output: null,
    };
  },
  methods: {
    handleAddTask() {
      this.tasks.push({ name: '', min: '', max: '', confidence: '', cost: '' });
    },
    handleDeleteTask(index) {
      this.tasks = this.tasks.filter((task, ind) => index !== ind);
    },
    getRandom(minimum, maximum) {
      const min = Math.ceil(minimum);
      const max = Math.floor(maximum);
      return Math.floor(Math.random() * (max - min + 1)) + min;
    },
    taskUpperBound(maxEstimate, confidence) {
      const boundary = maxEstimate * Math.abs(Math.floor(10 - confidence * 10));
      return boundary;
    },
    calculateUpperBond(tasks, useCost = false) {
      let total = 0;
      let multiplier = 1;
      tasks.forEach((row) => {
        if (useCost) {
          multiplier = row.Cost;
        }
        total += this.taskUpperBound(row.max, row.confidence) * multiplier;
      });
      return total;
    },
    generateEstimate(minimum, maximum, confidence) {
      const max = parseInt(maximum, 10);
      const min = parseInt(minimum, 10);
      const base = this.getRandom(1, 1000);
      const boundary = confidence * 1000;
      const midBoundary = Math.floor((1000 - boundary) / 2);
      const range = max - min + 1;
      const maxOverrun = this.taskUpperBound(max, confidence);
      let total = 0;

      if (base < boundary) {
        total = (base % range) + min;
      } else if (base - boundary < midBoundary) {
        total = min === 0 ? 0 : base % min;
      } else {
        total = this.getRandom(max, maxOverrun);
      }

      return total;
    },
    getValueCount(data) {
      // Find total count of values.
      let valueCount = 0;
      data.forEach((value) => {
        valueCount += value;
      });
      return valueCount;
    },
    getMedian(data) {
      // Find total count of values.
      const valueCount = this.getValueCount(data);

      // Walk back to the middle of the result set to see which is median
      const midCount = valueCount / 2;
      let median = 0;
      let currentDistance = 0;
      for (let i = 0; i < data.length; i += 1) {
        currentDistance += data[i];
        // We passed the mid point in this segment, we are sitting on the value.
        if (currentDistance > midCount) {
          median = i;
          break;
        }
        // The median falls on the line between this segment and the next we have a bit of work to do.
        // If this is a odd-length set (rare in this design) average this and the next.
        // If there is gap between this value and the next, we need to measure it and pick the
        // midpoint of the gap.
        if (currentDistance === midCount) {
          const lookAhead = data[i + 1];
          if (lookAhead) {
            // No gap, to the median is between here and the next.
            median = (i + (i + 1)) / 2;
            return median;
          } else {
            // We have a gap, so find next value.
            let gap = 1;
            let offset = 0;
            for (let j = i + 2; j < data.length; j += 1) {
              if (data[j] === 0) {
                gap += 1;
              } else {
                // Found end of gap. The median is the middle of the gap.
                offset = gap / 2;
                break;
              }
            }
            median = i + offset + 0.5;
            return median;
          }
        }
      }
      return median;
    },
    getStandardDeviation(numberArray) {
      // Calculate the average.
      const sum = numberArray.reduce(
        (total, currentValue, currentIndex) =>
          total + currentValue * currentIndex
      );
      const valueCount = this.getValueCount(numberArray);
      const avg = sum / valueCount;

      // Calculate the standard deviation itself.
      let sdPrep = 0;
      for (let i = 0; i < numberArray.length; i += 1) {
        sdPrep += (i - avg) ** 2 * numberArray[i];
      }

      // Divide by n - 1
      // This answer is the variance of the sample.
      const variance = sdPrep / (valueCount - 1);

      const standardDev = Math.sqrt(variance);
      return standardDev;
    },
    calculateUpperBound(tasks, useCost = false) {
      let total = 0;
      let multiplier = 1;
      tasks.forEach((row) => {
        if (useCost) {
          multiplier = row.cost;
        }
        total += this.taskUpperBound(row.max, row.confidence) * multiplier;
      });
      return total;
    },
    runSimulation(passes, data) {
      const upperTimeBound = this.calculateUpperBound(data);
      const upperCostBound = this.calculateUpperBound(data, true);
      let times = new Array(upperTimeBound).fill(0);
      const costs = new Array(upperCostBound).fill(0);
      const estimates = {
        times: [],
        costs: [],
      };
      const estimateDetails = [];
      const startTime = Date.now();
      let minTime = -1;
      let maxTime = 0;
      let minCost = -1;
      let maxCost = 0;
      let endTime = 0;
      let totalTime = 0;
      let totalCost = 0;
      let outcome = {};

      // Run the simulation.
      for (let i = 0; i < passes; i += 1) {
        totalTime = 0;
        totalCost = 0;
        outcome = {};

        for (const row of data) {
          const taskTime = this.generateEstimate(
            row.min,
            row.max,
            row.confidence
          );

          const taskCost = taskTime * row.Cost;
          totalTime += taskTime;

          totalCost += taskCost;
          outcome[row.Name] = {
            time: taskTime,
            cost: taskCost,
          };
        }

        /* ----------------------------------------------------------
         ** In many cases totalTime is greater than the array length
         ************************************************************/

        if (totalTime >= 0 && totalTime < upperTimeBound) {
            times[totalTime] += 1;
            costs[totalCost] += 1;
        }  
            
        estimates.times.push(totalTime);
        estimates.costs.push(totalCost);
        estimateDetails.push(outcome);

        if (totalTime < minTime || minTime === -1) {
          minTime = totalTime;
        }
        if (totalTime > maxTime) {
          maxTime = totalTime;
        }
        if (totalCost < minCost || minCost === -1) {
          minCost = totalCost;
        }
        if (totalCost > maxCost) {
          maxCost = totalCost;
        }
      }
      endTime = Date.now();

      // Calculate and display the results.

      const runningTime = endTime - startTime;
      const results = {
        runningTime,
        estimateDetails,
        times: {
          median: this.getMedian(times),
          sd: this.getStandardDeviation(times),
          min: minTime,
          max: maxTime,
          list: times,
        },
        costs: {
          median: this.getMedian(costs),
          sd: this.getStandardDeviation(costs),
          min: minCost,
          max: maxCost,
          list: costs,
        },
      };

      results.times.likelyMin = Math.round(
        results.times.median - results.times.sd
      );
      results.times.likelyMax = Math.round(
        results.times.median + results.times.sd
      );
      results.costs.likelyMin = Math.round(
        results.costs.median - results.costs.sd
      );
      results.costs.likelyMax = Math.round(
        results.costs.median + results.costs.sd
      );

      this.output = results;

      this.buildHistogram(
        document.getElementById('histogram'),
        results.times.list,
        results.times.min,
        results.times.max,
        results.times.median,
        results.times.sd,
        'Horas',
        true
      );

      return this.output;
    },
    handleRunSimulation() {
      let inputs = [];
      this.tasks.forEach((task) => {
        let obj = {};
        obj.min = parseInt(task.min, 10);
        obj.max = parseInt(task.max, 10);
        obj.confidence = parseInt(task.confidence) / 100;
        obj.cost = parseInt(task.cost, 10);
        inputs.push(obj);
      });

      if (this.tasks.length > 1) {
        this.runSimulation(this.numberSimulations, inputs);
      } else {
        alert('Debes colocar tareas para usarlos de datos para la simulacion');
      }
    },
    buildHistogram(targetNode, list, min, max, median, stdDev, xLabel, limitGraph) {
      // Remove and existing graphs
      targetNode.innerHTML = '';

      // The number of points before it switches to using a line graph.
      const barCutoff = 600;

      // The width of the image
      const imageWidth = 800;
      const imageHeight = 500;

      // Image Margins
      const binMargin = 0.2;
      const margin = {
        top: 10,
        right: 30,
        bottom: 50,
        left: 60,
      };

      // Set outer bounds of graph.
      let minBin = min;
      let maxBin = max;

      // Trim the array to just hold cells in the range of results.
      // If limit graph is set, just show two standard deviations on the graph.
      if (limitGraph) {
        maxBin = median + stdDev * 2 < max ? median + stdDev * 2 : max;
        minBin = median - stdDev * 2 > min ? median - stdDev * 2 : min;
      }
      const data = list.filter((e, i) => i >= minBin && i <= maxBin);

      // We need to round the median and standard deviation and find the
      // index we expect for the bars.
      const medianIndex = Math.round(median - minBin);
      const stdDevOffset = Math.round(stdDev);
      const stdDevLowIndex = medianIndex - stdDevOffset;
      const stdDevHighIndex = medianIndex + stdDevOffset;

      // whitespace on either side of the bars
      const width = imageWidth - margin.left - margin.right;
      const height = imageHeight - margin.top - margin.bottom;

      // Set the limits of the x axis
      const xMin = minBin - 1;
      const xMax = maxBin + 1;

      // Determine if we should use a bar graph or scatter plot.
      const useBars = xMax - xMin < barCutoff;

      // Set the max range of the y axis.
      // The data array can be quite large so standard Math.Max approaches can fail.
      const sortedData = [...data].sort((a, b) => a - b);
      const yMax = sortedData[sortedData.length - 1];

      // This scale is for determining the widths of the histogram bars
      const x = d3
        .scaleLinear()
        .domain([0, xMax - xMin])
        .range([0, width]);

      // Scale for the placement of the bars
      const x2 = d3.scaleLinear().domain([xMin, xMax]).range([0, width]);

      const y = d3.scaleLinear().domain([0, yMax]).range([height, 0]);

      const xAxis = d3.axisBottom().scale(x2);
      const yAxis = d3.axisLeft().scale(y).ticks(8);

      // Put the graph in the histogram div.
      const svg = d3
        .select(targetNode)
        .append('svg')
        .attr('width', width + margin.left + margin.right)
        .attr('height', height + margin.top + margin.bottom)
        .append('g')
        .attr('transform', `translate(${margin.left},${margin.top})`);

      // Add the x axis and x-label.
      svg
        .append('g')
        .attr('class', 'x axis')
        .attr('transform', `translate(0,${height})`)
        .call(xAxis);
      svg
        .append('text')
        .attr('class', 'xLabel')
        .attr('text-anchor', 'middle')
        .attr('x', width / 2)
        .attr('y', height + margin.bottom)
        .text(xLabel);

      // Add the y axis and y-label.
      svg
        .append('g')
        .attr('class', 'y axis')
        .attr('transform', 'translate(0,0)')
        .call(yAxis);
      svg
        .append('text')
        .attr('class', 'yLabel')
        .attr('y', 0 - margin.left) // x and y switched due to rotation.
        .attr('x', 0 - height / 2)
        .attr('dy', '1em')
        .attr('transform', 'rotate(-90)')
        .style('text-anchor', 'middle')
        .text('Frecuencia');

      // Set up the bars.
      if (useBars) {
        const bar = svg
          .selectAll('.bar')
          .data(data)
          .enter()
          .append('g')
          .attr('class', (d, i) => {
            if (i === medianIndex) {
              return 'bar median';
            }
            if (i > stdDevLowIndex && i < stdDevHighIndex) {
              return 'bar stdDev';
            }
            return 'bar';
          })
          .attr('transform', (d, i) => `translate(${x2(i + minBin)},${y(d)})`);

        // Add rectangles of correct size at correct location.
        bar
          .append('rect')
          .attr('x', x(binMargin))
          .attr('width', x(2 * binMargin))
          .attr('height', (d) => height - y(d));
      } else {
        // Use Scatter plot instead of bars
        svg
          .selectAll('dot')
          .data(data)
          .join('circle')
          .attr('cx', (d, i) => x(i))
          .attr('cy', (d) => y(d))
          .attr('r', (d, i) => {
            if (i === medianIndex) {
              return 3;
            }
            return 1;
          })
          .attr('class', (d, i) => {
            if (i === medianIndex) {
              return 'graphXY median';
            }
            if (i > stdDevLowIndex && i < stdDevHighIndex) {
              return 'graphXY stdDev';
            }
            return 'graphXY';
          });
      }
    },
  },
};
</script>

<style scoped>
</style>
