# Code-1
Differential effects of data omissions and positional errors on the minimum acceptable geocoding hit rate
1. How to run the shared codes?

##Overview:

This experiment workflow aims to analyze spatial point patterns with the following steps:

1. **Data Preparation**:
   - Real geographical background data are stored in the "data" folder within the "experiments" folder. 
   - Execute the code located in the "experiments" folder.

2. **Generating Point Patterns**:
   - Use the "Matern process-JD" and "Matern process-SQ" code to generate points within real geographical divisions such as subdistrict or community level respectively.
   - Vary point intensities and clustering levels.
   - Adjust point intensity by changing the number of points and clustering level by altering 'r'.
   - Assess clustering level using the Nearest Neighbor Index (NNI).

3. **Point Statistics**:
   - Employ the "point-tongji-JD" and "point-tongji-SQ" code to count points within each division under real geographical divisions such as subdistrict or community level respectively.
   - Use the "Daochu-txt" code to export the original point coordinates, such as  "GeneratedPoints-nni-0.2_-density-10-JD.txt" or to export the point count results in TXT format, such as "states-mcp2-original-nni-0.2-density-10-JD.txt" in the "experiments" folder.
   - Assume an error-free original spatial pattern and compute distributions accordingly.

4. **Introducing Errors**:
   - Use the "add-error-missing" code to introduce errors such as data omissions, and use the "Transfer-error-expotential" code to introduce positional inaccuracies according to an expotential distribution to the original distribution.
   - The "Transfer-error-GSZXG" code, "Transfer-error-Lognormal" code, and "Transfer-error-TT" code each introduce positional inaccuracies following Gaussian, Lognormal, and T distributions, respectively, to the original distribution.
   - Simulate data omissions by randomly removing 1% of point events or transfering 1% of points events to simulate positional inaccuracy.

5. **Statistical Comparison**:
   - Utilize the Mann-Whitney U test to compare the original distribution with the modified one.
   - Set the significance level at p=0.05.
   - Determine the Minimum Acceptable Hit Rate (MAHR)–the percentage of correctly matched points needed to ensure no significant difference in point statistics before and after introducing errors.
   - If significant, record the percentage and output it as a result.
   - If not significant, return to the "Introducing Errors" section to increase the error point ratio until the point statistics show significant changes.

6.**Result Fitting**:
   - Use the "Qu-mianNH-missing" and "Qu-mianNH-transfer" code to perform surface fitting on the experimental results obtained from "Statistical Comparison" section. 

## Instructions:

1. **Data Preparation**:
   - Ensure real geographical background data are stored in the "data" folder within the "experiments" folder. 
   - Run the code located in the "experiments" folder.

2. **Generating Point Patterns**:
   - Adjust parameters in the "Matern process-JD" and "Matern process-SQ" code to vary point intensities and clustering levels under real geographical divisions such as subdistrict or community level respectively.

3. **Point Statistics**:
   - Run the "point-tongji-JD" and "point-tongji-SQ" code to obtain point counts within each division under real geographical divisions such as subdistrict or community level respectively.

4. **Introducing Errors**:
   - Execute the "add-error-missing" or "Transfer-error-expotential" code to introduce errors to the original distribution.

5. **Statistical Comparison**:
   - Perform the Mann-Whitney U test to compare distributions.
   - Determine the MAHR to assess the impact of errors on point statistics.

6.**Result Fitting**:
   - The resulting fitting functions serve as reference bases for determining the suitability for spatial mapping in cases of missing data or positional errors.
   
## Notes:
- Adjust parameters and code as necessary for specific experiments.
- Record and analyze results meticulously to draw meaningful conclusions.



2. How the expected experimental results validate the reported findings?

#### Objective:
To validate the reported findings by determining the minimum required matching percentage under specific error patterns and aggregation levels, corresponding to different point intensities and clustering levels.

#### Methodology:
Expected experimental results will be obtained by conducting experiments under various error patterns and aggregation levels while varying point intensities and clustering levels.

#### Expected Outcome:
The minimum acceptable match rate is anticipated to fall within the confidence intervals of Figures 9 to 12 in the corresponding paper's Results section.

#### Significance:
Validation of the reported findings through expected experimental results will bolster the credibility of the study's conclusions and provide further insight into the performance of the proposed method under different conditions.

#### Implementation:
1. Define error patterns and aggregation levels.
2. Vary point intensities and clustering levels.
3. Conduct experiments and record results.
4. Compare obtained results with confidence intervals of Figures 9 to 12 from the paper.
5. Validate reported findings based on the consistency of expected experimental results.

3. Expected Experimental Results

#### Data Omissions - Subdistrict Level:

| Intensity | NNI=0.1 | NNI=0.2 | NNI=0.4 | NNI=0.6 | NNI=0.8 | NNI=1.0 |
|-----------|---------|---------|---------|---------|---------|---------|
| 10         | 30%     | 35%    | 50%    | 56%    | 68%    | 80%    |
| 50         | 25%     | 30%    | 42%    | 48%    | 52%    | 63%    |
| 100       | 15%     | 25%    | 32%    | 44%    | 50%    | 60%    |
| 150       | 13%     | 23%    | 30%    | 40%    | 47%    | 57%    |
| 200       | 10%     | 20%    | 28%    | 38%    | 45%    | 55%    |
| 250       | 8%       | 18%    | 28%    | 34%    | 39%    | 53%    |

#### Data Omissions - Community Level:

| Intensity | NNI=0.1 | NNI=0.2 | NNI=0.4 | NNI=0.6 | NNI=0.8 | NNI=1.0 |
|-----------|---------|---------|---------|---------|---------|---------|
| 10         | 33%     | 38%    | 56%    | 57%    | 72%    | 85%    |
| 50         | 28%     | 35%    | 47%    | 52%    | 55%    | 69%    |
| 100       | 18%     | 29%    | 37%    | 49%    | 53%    | 65%    |
| 150       | 16%     | 27%    | 33%    | 44%    | 50%    | 60%    |
| 200       | 13%     | 24%    | 30%    | 41%    | 50%    | 57%    |
| 250       | 10%     | 20%    | 30%    | 38%    | 42%    | 55%    |

#### Positional Error - Subdistrict Level:

| Intensity | NNI=0.1 | NNI=0.2 | NNI=0.4 | NNI=0.6 | NNI=0.8 | NNI=1.0 |
|-----------|---------|---------|---------|---------|---------|---------|
| 10         | 100%   | 86%    | 75%    | 65%    | 38%    | 18%    |
| 50         | 100%   | 90%    | 84%    | 77%    | 74%    | 58%    |
| 100       | 100%   | 96%    | 93%    | 89%    | 89%    | 86%    |
| 150       | 100%   | 98%    | 96%    | 94%    | 91%    | 89%    |
| 200       | 100%   | 99%    | 97%    | 95%    | 95%    | 90%    |
| 250       | 100%   | 99%    | 98%    | 97%    | 95%    | 92%    |

#### Positional Error - Community Level:

| Intensity | NNI=0.1 | NNI=0.2 | NNI=0.4 | NNI=0.6 | NNI=0.8 | NNI=1.0 |
|-----------|---------|---------|---------|---------|---------|---------|
| 10         | 100%   | 89%    | 78%    | 69%    | 42%    | 23%    |
| 50         | 100%   | 93%    | 87%    | 80%    | 78%    | 64%    |
| 100       | 100%   | 98%    | 96%    | 93%    | 94%    | 90%    |
| 150       | 100%   | 100%  | 97%    | 95%    | 93%    | 92%    |
| 200       | 100%   | 100%  | 98%    | 95%    | 95%    | 93%    |
| 250       | 100%   | 99%    | 99%    | 97%    | 95%    | 94%    |

Results are presented as percentages.
