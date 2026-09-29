## BlazeDemo Performance Testing

Performance test script for the BlazeDemo flight booking demo application, created with Apache JMeter.

### Test scenario

The test simulates a complete user journey, split into transactions so that response time can be measured for each step:

1. **Open Website** – load the home page
2. **Choose cities** – search flights from Boston to London
3. **Choose Flight** – select a flight
4. **Input Info** – submit passenger and payment details and confirm the purchase

### Test plan components

- **Thread Group** – virtual users, ramp-up period and loop count
- **Transaction Controllers** – group requests into user steps
- **HTTP Request samplers** – GET and POST requests
- **Uniform Random Timers** – simulate user think time between steps
- **HTTP Cookie and Cache Managers** – cleared on each iteration to simulate new users
- **User Defined Variables** – base URL of the application
- **Listeners** – Summary Report, Aggregate Report and View Results Tree

### Tools

- Apache JMeter 5.6.3
- BlazeMeter Chrome recorder (for recording the initial script)

### How to run

1. Install Apache JMeter.
2. Open `blazedemo.jmx` in JMeter to review the test plan.
3. Adjust the Thread Group (number of users, ramp-up, loops) for the desired load.
4. Run the test in non-GUI mode:

   jmeter -n -t blazedemo.jmx -l results.jtl -e -o report

5. Open `report/index.html` to see the results.

### Key metrics

- Response time (average and 90th percentile)
- Throughput (requests per second)
- Error rate
