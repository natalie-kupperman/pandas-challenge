

```python
#Py Academy Key Metrics
```


```python
#intializing data 
import pandas as pd

file_one = "schools_complete.csv"
file_two = "students_complete.csv"

school_df = pd.read_csv(file_one)
student_df = pd.read_csv(file_two)
```


```python
#check school csv
school_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
#check student csv
student_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
#calculate district totals from school_df
total_schools = len(school_df)

total_students = school_df["size"].sum()

total_budget = school_df["budget"].sum()

#calculate district totals from student_df
avg_math = round(student_df["math_score"].mean(), 1)

avg_read = round(student_df["reading_score"].mean(), 1)

student_total = len(student_df)

pass_math = (student_df["math_score"] >= 70).value_counts()[True]
perc_pass_math= round((pass_math/student_total)*100, 1)

pass_read = (student_df["reading_score"] >= 70).value_counts()[True]
perc_pass_read = round((pass_read/student_total)*100, 1)

perc_pass_overall = round((perc_pass_math + perc_pass_read)/2, 1)
```


```python
district_summary_df = pd.DataFrame({"Number of Schools": [total_schools],
                                    "Number of Students": [total_students],
                                    "Total Budget": [total_budget],
                                    "Average Math Score": [avg_math],
                                    "Percent Passing Math": [perc_pass_math],
                                    "Average Reading Score": [avg_read],
                                    "Percent Passing Reading": [perc_pass_read],
                                    "Overall Passing Percentage": [perc_pass_overall] },
                                    columns = ["Number of Schools", "Number of Students", "Total Budget", 
                                               "Average Math Score", "Percent Passing Math", "Average Reading Score", 
                                               "Percent Passing Reading", "Overall Passing Percentage"])
district_summary_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Number of Schools</th>
      <th>Number of Students</th>
      <th>Total Budget</th>
      <th>Average Math Score</th>
      <th>Percent Passing Math</th>
      <th>Average Reading Score</th>
      <th>Percent Passing Reading</th>
      <th>Overall Passing Percentage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>15</td>
      <td>39170</td>
      <td>24649428</td>
      <td>79.0</td>
      <td>75.0</td>
      <td>81.9</td>
      <td>85.8</td>
      <td>80.4</td>
    </tr>
  </tbody>
</table>
</div>




```python
#rename columns for merge
school_df = school_df.rename(columns = {"name": "school name"})

student_df = student_df.rename(columns = {"school": "school name"})
```


```python
#group students by school
student_groupby_school = student_df.groupby(["school name"])

#calculate average math scores and total number passing by school
avg_math_school = pd.DataFrame(round(student_groupby_school["math_score"].mean(), 2))
avg_math_school.columns = ["average math score"]
avg_math_school = avg_math_school.reset_index()

pass_math_school = student_df[student_df["math_score"] > 70].groupby("school name")

pass_math_total_school = pd.DataFrame(round(pass_math_school["math_score"].count(), 1))
pass_math_total_school.columns = ["number pass math"]
pass_math_total_school = pass_math_total_school.reset_index()

#calculate average reading scores and total number passing by school
avg_read_school = pd.DataFrame(round(student_groupby_school["reading_score"].mean(), 1))
avg_read_school.columns = ["average reading score"]
avg_read_school = avg_read_school.reset_index()

pass_read_school = student_df[student_df["reading_score"] > 70].groupby("school name")

pass_read_total_school = pd.DataFrame(pass_read_school["reading_score"].count())
pass_read_total_school.columns = ["number pass reading"]
pass_read_total_school = pass_read_total_school.reset_index()
```


```python
#merge school dataframe with newly made math and reading dataframes
combined_df = pd.merge(school_df, avg_math_school, on = "school name", how = "outer")

combined_df = pd.merge(combined_df, pass_math_total_school, on = "school name", how = "outer")

combined_df = pd.merge(combined_df, avg_read_school, on = "school name", how = "outer")

combined_df = pd.merge(combined_df, pass_read_total_school, on= "school name", how = "outer")

combined_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>average math score</th>
      <th>number pass math</th>
      <th>average reading score</th>
      <th>number pass reading</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>76.63</td>
      <td>1847</td>
      <td>81.2</td>
      <td>2299</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>76.71</td>
      <td>1880</td>
      <td>81.2</td>
      <td>2313</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>83.36</td>
      <td>1583</td>
      <td>83.7</td>
      <td>1631</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>77.29</td>
      <td>3001</td>
      <td>80.9</td>
      <td>3624</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>83.35</td>
      <td>1317</td>
      <td>83.8</td>
      <td>1371</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>83.27</td>
      <td>2076</td>
      <td>84.0</td>
      <td>2129</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>83.06</td>
      <td>1664</td>
      <td>84.0</td>
      <td>1744</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>77.05</td>
      <td>3216</td>
      <td>81.0</td>
      <td>3946</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>83.80</td>
      <td>387</td>
      <td>83.8</td>
      <td>396</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>83.84</td>
      <td>882</td>
      <td>84.0</td>
      <td>887</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>83.68</td>
      <td>1625</td>
      <td>84.0</td>
      <td>1682</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>76.84</td>
      <td>2562</td>
      <td>80.7</td>
      <td>3109</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>77.07</td>
      <td>3040</td>
      <td>81.0</td>
      <td>3727</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>77.10</td>
      <td>1801</td>
      <td>80.7</td>
      <td>2123</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>83.42</td>
      <td>1475</td>
      <td>83.8</td>
      <td>1519</td>
    </tr>
  </tbody>
</table>
</div>




```python
#create new column for percent passing math at each school
combined_df["% passing math"] = round((combined_df["number pass math"]/combined_df["size"])*100, 1)

#create new column for percent passing reading at each school
combined_df["% passing reading"] = round((combined_df["number pass reading"]/combined_df["size"])*100, 1)

#create new column for percent passing reading and math at each school
combined_df["% overall passing"] = round((combined_df["% passing math"] + combined_df["% passing reading"])/2, 1)

combined_df

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>average math score</th>
      <th>number pass math</th>
      <th>average reading score</th>
      <th>number pass reading</th>
      <th>% passing math</th>
      <th>% passing reading</th>
      <th>% overall passing</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>76.63</td>
      <td>1847</td>
      <td>81.2</td>
      <td>2299</td>
      <td>63.3</td>
      <td>78.8</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>76.71</td>
      <td>1880</td>
      <td>81.2</td>
      <td>2313</td>
      <td>63.8</td>
      <td>78.4</td>
      <td>71.1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>83.36</td>
      <td>1583</td>
      <td>83.7</td>
      <td>1631</td>
      <td>89.9</td>
      <td>92.6</td>
      <td>91.2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>77.29</td>
      <td>3001</td>
      <td>80.9</td>
      <td>3624</td>
      <td>64.7</td>
      <td>78.2</td>
      <td>71.4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>83.35</td>
      <td>1317</td>
      <td>83.8</td>
      <td>1371</td>
      <td>89.7</td>
      <td>93.4</td>
      <td>91.6</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>83.27</td>
      <td>2076</td>
      <td>84.0</td>
      <td>2129</td>
      <td>90.9</td>
      <td>93.3</td>
      <td>92.1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>83.06</td>
      <td>1664</td>
      <td>84.0</td>
      <td>1744</td>
      <td>89.6</td>
      <td>93.9</td>
      <td>91.8</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>77.05</td>
      <td>3216</td>
      <td>81.0</td>
      <td>3946</td>
      <td>64.6</td>
      <td>79.3</td>
      <td>71.9</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>83.80</td>
      <td>387</td>
      <td>83.8</td>
      <td>396</td>
      <td>90.6</td>
      <td>92.7</td>
      <td>91.6</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>83.84</td>
      <td>882</td>
      <td>84.0</td>
      <td>887</td>
      <td>91.7</td>
      <td>92.2</td>
      <td>92.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>83.68</td>
      <td>1625</td>
      <td>84.0</td>
      <td>1682</td>
      <td>90.3</td>
      <td>93.4</td>
      <td>91.8</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>76.84</td>
      <td>2562</td>
      <td>80.7</td>
      <td>3109</td>
      <td>64.1</td>
      <td>77.7</td>
      <td>70.9</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>77.07</td>
      <td>3040</td>
      <td>81.0</td>
      <td>3727</td>
      <td>63.9</td>
      <td>78.3</td>
      <td>71.1</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>77.10</td>
      <td>1801</td>
      <td>80.7</td>
      <td>2123</td>
      <td>65.8</td>
      <td>77.5</td>
      <td>71.6</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>83.42</td>
      <td>1475</td>
      <td>83.8</td>
      <td>1519</td>
      <td>90.2</td>
      <td>92.9</td>
      <td>91.6</td>
    </tr>
  </tbody>
</table>
</div>




```python
#create new column for budget per student
combined_df["budget/student"] = round(combined_df["budget"]/combined_df["size"], 2)

combined_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>average math score</th>
      <th>number pass math</th>
      <th>average reading score</th>
      <th>number pass reading</th>
      <th>% passing math</th>
      <th>% passing reading</th>
      <th>% overall passing</th>
      <th>budget/student</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>76.63</td>
      <td>1847</td>
      <td>81.2</td>
      <td>2299</td>
      <td>63.3</td>
      <td>78.8</td>
      <td>71.0</td>
      <td>655.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>76.71</td>
      <td>1880</td>
      <td>81.2</td>
      <td>2313</td>
      <td>63.8</td>
      <td>78.4</td>
      <td>71.1</td>
      <td>639.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>83.36</td>
      <td>1583</td>
      <td>83.7</td>
      <td>1631</td>
      <td>89.9</td>
      <td>92.6</td>
      <td>91.2</td>
      <td>600.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>77.29</td>
      <td>3001</td>
      <td>80.9</td>
      <td>3624</td>
      <td>64.7</td>
      <td>78.2</td>
      <td>71.4</td>
      <td>652.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>83.35</td>
      <td>1317</td>
      <td>83.8</td>
      <td>1371</td>
      <td>89.7</td>
      <td>93.4</td>
      <td>91.6</td>
      <td>625.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>83.27</td>
      <td>2076</td>
      <td>84.0</td>
      <td>2129</td>
      <td>90.9</td>
      <td>93.3</td>
      <td>92.1</td>
      <td>578.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>83.06</td>
      <td>1664</td>
      <td>84.0</td>
      <td>1744</td>
      <td>89.6</td>
      <td>93.9</td>
      <td>91.8</td>
      <td>582.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>77.05</td>
      <td>3216</td>
      <td>81.0</td>
      <td>3946</td>
      <td>64.6</td>
      <td>79.3</td>
      <td>71.9</td>
      <td>628.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>83.80</td>
      <td>387</td>
      <td>83.8</td>
      <td>396</td>
      <td>90.6</td>
      <td>92.7</td>
      <td>91.6</td>
      <td>581.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>83.84</td>
      <td>882</td>
      <td>84.0</td>
      <td>887</td>
      <td>91.7</td>
      <td>92.2</td>
      <td>92.0</td>
      <td>609.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>83.68</td>
      <td>1625</td>
      <td>84.0</td>
      <td>1682</td>
      <td>90.3</td>
      <td>93.4</td>
      <td>91.8</td>
      <td>583.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>76.84</td>
      <td>2562</td>
      <td>80.7</td>
      <td>3109</td>
      <td>64.1</td>
      <td>77.7</td>
      <td>70.9</td>
      <td>637.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>77.07</td>
      <td>3040</td>
      <td>81.0</td>
      <td>3727</td>
      <td>63.9</td>
      <td>78.3</td>
      <td>71.1</td>
      <td>650.0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>77.10</td>
      <td>1801</td>
      <td>80.7</td>
      <td>2123</td>
      <td>65.8</td>
      <td>77.5</td>
      <td>71.6</td>
      <td>644.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>83.42</td>
      <td>1475</td>
      <td>83.8</td>
      <td>1519</td>
      <td>90.2</td>
      <td>92.9</td>
      <td>91.6</td>
      <td>638.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#dataframe for school summary
school_summary_unformatted = pd.DataFrame(combined_df[["school name", "type", "size", "budget", "budget/student", 
                                                       "average math score", "% passing math", "average reading score", 
                                                       "% passing reading", "% overall passing"]])
school_summary_unformatted
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>school name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>budget/student</th>
      <th>average math score</th>
      <th>% passing math</th>
      <th>average reading score</th>
      <th>% passing reading</th>
      <th>% overall passing</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>76.63</td>
      <td>63.3</td>
      <td>81.2</td>
      <td>78.8</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>76.71</td>
      <td>63.8</td>
      <td>81.2</td>
      <td>78.4</td>
      <td>71.1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>83.36</td>
      <td>89.9</td>
      <td>83.7</td>
      <td>92.6</td>
      <td>91.2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>77.29</td>
      <td>64.7</td>
      <td>80.9</td>
      <td>78.2</td>
      <td>71.4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.35</td>
      <td>89.7</td>
      <td>83.8</td>
      <td>93.4</td>
      <td>91.6</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.27</td>
      <td>90.9</td>
      <td>84.0</td>
      <td>93.3</td>
      <td>92.1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.06</td>
      <td>89.6</td>
      <td>84.0</td>
      <td>93.9</td>
      <td>91.8</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>77.05</td>
      <td>64.6</td>
      <td>81.0</td>
      <td>79.3</td>
      <td>71.9</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>83.80</td>
      <td>90.6</td>
      <td>83.8</td>
      <td>92.7</td>
      <td>91.6</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>83.84</td>
      <td>91.7</td>
      <td>84.0</td>
      <td>92.2</td>
      <td>92.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>83.68</td>
      <td>90.3</td>
      <td>84.0</td>
      <td>93.4</td>
      <td>91.8</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>76.84</td>
      <td>64.1</td>
      <td>80.7</td>
      <td>77.7</td>
      <td>70.9</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>77.07</td>
      <td>63.9</td>
      <td>81.0</td>
      <td>78.3</td>
      <td>71.1</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>77.10</td>
      <td>65.8</td>
      <td>80.7</td>
      <td>77.5</td>
      <td>71.6</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>83.42</td>
      <td>90.2</td>
      <td>83.8</td>
      <td>92.9</td>
      <td>91.6</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Top Performing Schools Based on % Overall Passing Metric
top_perform_schools = pd.DataFrame(school_summary_unformatted.sort_values("% overall passing", ascending = False)[:5])
top_perform_schools
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>school name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>budget/student</th>
      <th>average math score</th>
      <th>% passing math</th>
      <th>average reading score</th>
      <th>% passing reading</th>
      <th>% overall passing</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.27</td>
      <td>90.9</td>
      <td>84.0</td>
      <td>93.3</td>
      <td>92.1</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>83.84</td>
      <td>91.7</td>
      <td>84.0</td>
      <td>92.2</td>
      <td>92.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.06</td>
      <td>89.6</td>
      <td>84.0</td>
      <td>93.9</td>
      <td>91.8</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>83.68</td>
      <td>90.3</td>
      <td>84.0</td>
      <td>93.4</td>
      <td>91.8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.35</td>
      <td>89.7</td>
      <td>83.8</td>
      <td>93.4</td>
      <td>91.6</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Bottom Performing Schools Based on % Overall Passing Metric
bottom_perform_schools = pd.DataFrame(school_summary_unformatted.sort_values("% overall passing")[:5])
bottom_perform_schools
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>school name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>budget/student</th>
      <th>average math score</th>
      <th>% passing math</th>
      <th>average reading score</th>
      <th>% passing reading</th>
      <th>% overall passing</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11</th>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>76.84</td>
      <td>64.1</td>
      <td>80.7</td>
      <td>77.7</td>
      <td>70.9</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>76.63</td>
      <td>63.3</td>
      <td>81.2</td>
      <td>78.8</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>76.71</td>
      <td>63.8</td>
      <td>81.2</td>
      <td>78.4</td>
      <td>71.1</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>77.07</td>
      <td>63.9</td>
      <td>81.0</td>
      <td>78.3</td>
      <td>71.1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>77.29</td>
      <td>64.7</td>
      <td>80.9</td>
      <td>78.2</td>
      <td>71.4</td>
    </tr>
  </tbody>
</table>
</div>




```python
#collect data per grade
ninth = student_df.loc[student_df["grade"] == "9th"].groupby("school name", as_index = False)
tenth = student_df.loc[student_df["grade"] == "10th"].groupby("school name", as_index = False)
eleventh = student_df.loc[student_df["grade"] == "11th"].groupby("school name", as_index = False)
twelfth = student_df.loc[student_df["grade"] == "12th"].groupby("school name", as_index = False)
```


```python
#calculate math score averages per grade by school
ninth_math_avg_df = pd.DataFrame(round(ninth["math_score"].mean(), 1))
tenth_math_avg_df = pd.DataFrame(round(tenth["math_score"].mean(), 1))
eleventh_math_avg_df = pd.DataFrame(round(eleventh["math_score"].mean(), 1))
twelfth_math_avg_df = pd.DataFrame(round(twelfth["math_score"].mean(), 1))
```


```python
#Math Scores by Grade
#merge into one dataframe
avg_math_bygrade_df = pd.merge(ninth_math_avg_df, tenth_math_avg_df, on = "school name", how = "inner")
avg_math_bygrade_df = pd.merge(avg_math_bygrade_df, eleventh_math_avg_df, on = "school name", how = "inner")
avg_math_bygrade_df = pd.merge(avg_math_bygrade_df, twelfth_math_avg_df, on = "school name", how = "inner")
avg_math_bygrade_df.columns = ["school name", "9th", "10th", "11th", "12th"]
avg_math_bygrade_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>school name</th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Bailey High School</td>
      <td>77.1</td>
      <td>77.0</td>
      <td>77.5</td>
      <td>76.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Cabrera High School</td>
      <td>83.1</td>
      <td>83.2</td>
      <td>82.8</td>
      <td>83.3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Figueroa High School</td>
      <td>76.4</td>
      <td>76.5</td>
      <td>76.9</td>
      <td>77.2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Ford High School</td>
      <td>77.4</td>
      <td>77.7</td>
      <td>76.9</td>
      <td>76.2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Griffin High School</td>
      <td>82.0</td>
      <td>84.2</td>
      <td>83.8</td>
      <td>83.4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Hernandez High School</td>
      <td>77.4</td>
      <td>77.3</td>
      <td>77.1</td>
      <td>77.2</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Holden High School</td>
      <td>83.8</td>
      <td>83.4</td>
      <td>85.0</td>
      <td>82.9</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Huang High School</td>
      <td>77.0</td>
      <td>75.9</td>
      <td>76.4</td>
      <td>77.2</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Johnson High School</td>
      <td>77.2</td>
      <td>76.7</td>
      <td>77.5</td>
      <td>76.9</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Pena High School</td>
      <td>83.6</td>
      <td>83.4</td>
      <td>84.3</td>
      <td>84.1</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Rodriguez High School</td>
      <td>76.9</td>
      <td>76.6</td>
      <td>76.4</td>
      <td>77.7</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Shelton High School</td>
      <td>83.4</td>
      <td>82.9</td>
      <td>83.4</td>
      <td>83.8</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Thomas High School</td>
      <td>83.6</td>
      <td>83.1</td>
      <td>83.5</td>
      <td>83.5</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Wilson High School</td>
      <td>83.1</td>
      <td>83.7</td>
      <td>83.2</td>
      <td>83.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Wright High School</td>
      <td>83.3</td>
      <td>84.0</td>
      <td>83.8</td>
      <td>83.6</td>
    </tr>
  </tbody>
</table>
</div>




```python
#calculate reading score averages per grade by school
ninth_read_avg_df = pd.DataFrame(round(ninth["reading_score"].mean(), 1))
tenth_read_avg_df = pd.DataFrame(round(tenth["reading_score"].mean(), 1))
eleventh_read_avg_df = pd.DataFrame(round(eleventh["reading_score"].mean(), 1))
twelfth_read_avg_df = pd.DataFrame(round(twelfth["reading_score"].mean(), 1))
```


```python
#Reading Scores by Grade
#merge into one dataframe
avg_read_bygrade_df = pd.merge(ninth_read_avg_df, tenth_read_avg_df, on = "school name", how = "inner")
avg_read_bygrade_df = pd.merge(avg_read_bygrade_df, eleventh_read_avg_df, on = "school name", how = "inner")
avg_read_bygrade_df = pd.merge(avg_read_bygrade_df, twelfth_read_avg_df, on = "school name", how = "inner")
avg_read_bygrade_df.columns = ["school name", "9th", "10th", "11th", "12th"]
avg_read_bygrade_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>school name</th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Bailey High School</td>
      <td>81.3</td>
      <td>80.9</td>
      <td>80.9</td>
      <td>80.9</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Cabrera High School</td>
      <td>83.7</td>
      <td>84.3</td>
      <td>83.8</td>
      <td>84.3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Figueroa High School</td>
      <td>81.2</td>
      <td>81.4</td>
      <td>80.6</td>
      <td>81.4</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Ford High School</td>
      <td>80.6</td>
      <td>81.3</td>
      <td>80.4</td>
      <td>80.7</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Griffin High School</td>
      <td>83.4</td>
      <td>83.7</td>
      <td>84.3</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Hernandez High School</td>
      <td>80.9</td>
      <td>80.7</td>
      <td>81.4</td>
      <td>80.9</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Holden High School</td>
      <td>83.7</td>
      <td>83.3</td>
      <td>83.8</td>
      <td>84.7</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Huang High School</td>
      <td>81.3</td>
      <td>81.5</td>
      <td>81.4</td>
      <td>80.3</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Johnson High School</td>
      <td>81.3</td>
      <td>80.8</td>
      <td>80.6</td>
      <td>81.2</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Pena High School</td>
      <td>83.8</td>
      <td>83.6</td>
      <td>84.3</td>
      <td>84.6</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Rodriguez High School</td>
      <td>81.0</td>
      <td>80.6</td>
      <td>80.9</td>
      <td>80.4</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Shelton High School</td>
      <td>84.1</td>
      <td>83.4</td>
      <td>84.4</td>
      <td>82.8</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Thomas High School</td>
      <td>83.7</td>
      <td>84.3</td>
      <td>83.6</td>
      <td>83.8</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Wilson High School</td>
      <td>83.9</td>
      <td>84.0</td>
      <td>83.8</td>
      <td>84.3</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Wright High School</td>
      <td>83.8</td>
      <td>83.8</td>
      <td>84.2</td>
      <td>84.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
#School Metrics by Budget/Student
bins = [0, 600, 625, 650, 675]
group_names = ["< $600", "$600 - 625", "$625 - 650", "$650 - 675"]

metrics_bybudget = round(school_summary_unformatted[["average math score", "% passing math", 
                                                     "average reading score", "% passing reading", 
                                                     "% overall passing"]].groupby(pd.cut(school_summary_unformatted[
                                                     "budget/student"], bins = bins, labels = group_names)).mean(), 1)
metrics_bybudget
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>average math score</th>
      <th>% passing math</th>
      <th>average reading score</th>
      <th>% passing reading</th>
      <th>% overall passing</th>
    </tr>
    <tr>
      <th>budget/student</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt; $600</th>
      <td>83.4</td>
      <td>90.3</td>
      <td>83.9</td>
      <td>93.2</td>
      <td>91.7</td>
    </tr>
    <tr>
      <th>$600 - 625</th>
      <td>83.6</td>
      <td>90.7</td>
      <td>83.9</td>
      <td>92.8</td>
      <td>91.8</td>
    </tr>
    <tr>
      <th>$625 - 650</th>
      <td>78.0</td>
      <td>68.7</td>
      <td>81.4</td>
      <td>80.7</td>
      <td>74.7</td>
    </tr>
    <tr>
      <th>$650 - 675</th>
      <td>77.0</td>
      <td>64.0</td>
      <td>81.1</td>
      <td>78.5</td>
      <td>71.2</td>
    </tr>
  </tbody>
</table>
</div>




```python
#School Metrics by School Size
bins = [0, 1000, 3500, 5000]
group_names = ["Small (<1000)", "Medium (1000-3500)", "Large (3500-5000)"]

metrics_bysize = round(school_summary_unformatted[["average math score", "% passing math", 
                                                   "average reading score", "% passing reading", 
                                                   "% overall passing"]].groupby(pd.cut(school_summary_unformatted["size"],
                                                   bins = bins, labels = group_names)).mean(), 1)

metrics_bysize
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>average math score</th>
      <th>% passing math</th>
      <th>average reading score</th>
      <th>% passing reading</th>
      <th>% overall passing</th>
    </tr>
    <tr>
      <th>size</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small (&lt;1000)</th>
      <td>83.8</td>
      <td>91.2</td>
      <td>83.9</td>
      <td>92.4</td>
      <td>91.8</td>
    </tr>
    <tr>
      <th>Medium (1000-3500)</th>
      <td>81.2</td>
      <td>81.5</td>
      <td>82.9</td>
      <td>88.2</td>
      <td>84.9</td>
    </tr>
    <tr>
      <th>Large (3500-5000)</th>
      <td>77.1</td>
      <td>64.3</td>
      <td>80.9</td>
      <td>78.4</td>
      <td>71.3</td>
    </tr>
  </tbody>
</table>
</div>




```python
#School Metrics by School Type
metrics_bytype = round(school_summary_unformatted[["average math score", "% passing math", "average reading score",
                                                   "% passing reading", "% overall passing"]].groupby(
                                                   school_summary_unformatted["type"]).mean(), 1)

metrics_bytype
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>average math score</th>
      <th>% passing math</th>
      <th>average reading score</th>
      <th>% passing reading</th>
      <th>% overall passing</th>
    </tr>
    <tr>
      <th>type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>83.5</td>
      <td>90.4</td>
      <td>83.9</td>
      <td>93.0</td>
      <td>91.7</td>
    </tr>
    <tr>
      <th>District</th>
      <td>77.0</td>
      <td>64.3</td>
      <td>81.0</td>
      <td>78.3</td>
      <td>71.3</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Key Take Aways
#-Charter schools are outperfoming District schools in reading and math scores.
#-Small schools (<1000) are outperforming larger schools (>3500). Keep in mind Charter schools tend to be smaller schools; may be correlated. 
#-Spending more per student does not increase test scores. May need to investigate differences in spending between low and high performing schools.   
```
