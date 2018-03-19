Jupyter Notebook
Summary by each school - Copy
Last Checkpoint: 6 minutes ago
(autosaved)
Current Kernel Logo
Python [conda root] 
File
Edit
View
Insert
Cell
Kernel
Widgets
Help
Jupyter Notebook
Panda Homework
Last Checkpoint: a day ago
(autosaved)
Current Kernel Logo
Python [conda env:pythondata] 
File
Edit
View
Insert
Cell
Kernel
Widgets
Help


import pandas as pd
import csv
school_list_path="school_list.csv"
student_list_path="student_list.csv"
school_list_pd= pd.read_csv(school_list_path)
student_list_pd= pd.read_csv(student_list_path)
student_list_pd.head()
Student ID	name	gender	grade	school	reading_score	math_score
0	0	Paul Bradley	M	9th	Huang High School	66	79
1	1	Victor Smith	M	12th	Huang High School	94	61
2	2	Kevin Rodriguez	M	12th	Huang High School	90	60
3	3	Dr. Richard Scott	M	12th	Huang High School	67	58
4	4	Bonnie Ray	F	9th	Huang High School	97	84

school_list_pd.head()
School ID	name	type	size	budget
0	0	Huang High School	District	2917	1910635
1	1	Figueroa High School	District	2949	1884411
2	2	Shelton High School	Charter	1761	1056600
3	3	Hernandez High School	District	4635	3022020
4	4	Griffin High School	Charter	1468	917500

Total_school=len(school_list_pd)
Total_school
15

Total_students=student_list_pd["name"].count()
Total_students
39170

Total_budget=school_list_pd["budget"].sum()
Total_budget
24649428

​
Average_math_score=student_list_pd["math_score"].mean()
Average_reading_score=student_list_pd["reading_score"].mean()
Average_math_score
Average_reading_score
81.87784018381414

Average_math_score
​
78.98537145774827

Mathscore_pass=student_list_pd.loc[student_list_pd["math_score"] >= 60,:]
Mathscore_pass
TheNumber_Mathscore_pass=len(Mathscore_pass)
TheNumber_Mathscore_pass
36211

Percentage_Math_passed=(TheNumber_Mathscore_pass/Total_students)*100
Percentage_Math_passed
92.4457492979321

Readingcore_pass=student_list_pd.loc[student_list_pd["reading_score"] >= 60,:]
Readingcore_pass
TheNumber_Readingcore_pass=len(Readingcore_pass)
TheNumber_Readingcore_pass
39170

Percentage_Reading_passed=(TheNumber_Readingcore_pass/Total_students)*100
Percentage_Reading_passed
100.0

over_passing_rate=(Percentage_Reading_passed+Percentage_Math_passed)/2
over_passing_rate
96.22287464896604

District_Summany= pd.DataFrame({"Totalschools": [Total_school],"Total students": [Total_students],
                                   "Total Budget": [Total_budget],
                                   " Average math score": [Average_math_score]," Average reading score": [Average_reading_score],
                               
                                 
                                   "% Percentage Math passed": [Percentage_Math_passed], "% Percentage Reading passed": [Percentage_Reading_passed],
                                
                                   "% over passing rate":[over_passing_rate],
                                   
})
​
District_Summany = District_Summany[["Totalschools", 
                                         "Total students", 
                                         "Total Budget", 
                                         " Average math score", 
                                         " Average reading score", 
                                         "% Percentage Math passed", 
                                         "% Percentage Reading passed",
                                         "% over passing rate"
                                         ]]
​
​
​
​
​
​
District_Summany=District_Summany.round(2)
District_Summany.dtypes
​
Totalschools                     int64
Total students                   int64
Total Budget                     int64
 Average math score            float64
 Average reading score         float64
% Percentage Math passed       float64
% Percentage Reading passed    float64
% over passing rate            float64
dtype: object

#District_Summany[" Average math score"]=District_Summany[" Average math score"].format(float(u"5.0"))
​
#District_Summany[" Average_reading_score"]=District_Summany[" Average_reading_score"]."% over passing rate"
District_Summany[ "% Percentage Math passed"]=District_Summany[ "% Percentage Math passed"].map("{0:,.2f}%".format)
​
District_Summany[ "% Percentage Reading passed"]=District_Summany[ "% Percentage Reading passed"].map("{0:,.2f}%".format)
District_Summany[ "% over passing rate"]=District_Summany[ "% over passing rate"].map("{0:,.2f}%".format)
District_Summany
Totalschools	Total students	Total Budget	Average math score	Average reading score	% Percentage Math passed	% Percentage Reading passed	% over passing rate
0	15	39170	24649428	78.99	81.88	92.45%	100.00%	96.22%

​

​


import pandas as pd
import csv
import numpy
school_list_path="school_list.csv"
student_list_path="student_list.csv"
school_list_pd= pd.read_csv(school_list_path)
student_list_pd= pd.read_csv(student_list_path)
student_list_pd.head()
​
Student ID	name	gender	grade	school	reading_score	math_score
0	0	Paul Bradley	M	9th	Huang High School	66	79
1	1	Victor Smith	M	12th	Huang High School	94	61
2	2	Kevin Rodriguez	M	12th	Huang High School	90	60
3	3	Dr. Richard Scott	M	12th	Huang High School	67	58
4	4	Bonnie Ray	F	9th	Huang High School	97	84

Numbers_student_per_school =student_list_pd["school"].value_counts()
​
Numbers_student_per_school.head(15)
​
Bailey High School       4976
Johnson High School      4761
Hernandez High School    4635
Rodriguez High School    3999
Figueroa High School     2949
Huang High School        2917
Ford High School         2739
Wilson High School       2283
Cabrera High School      1858
Wright High School       1800
Shelton High School      1761
Thomas High School       1635
Griffin High School      1468
Pena High School          962
Holden High School        427
Name: school, dtype: int64

The_numbers_of_student_summany = pd.DataFrame({"The numbers of student":Numbers_student_per_school})
The_numbers_of_student_summany.index.name="name"
The_numbers_of_student_summany.reset_index(level=0, inplace=True)
The_numbers_of_student_summany
​
​
​
name	The numbers of student
0	Bailey High School	4976
1	Johnson High School	4761
2	Hernandez High School	4635
3	Rodriguez High School	3999
4	Figueroa High School	2949
5	Huang High School	2917
6	Ford High School	2739
7	Wilson High School	2283
8	Cabrera High School	1858
9	Wright High School	1800
10	Shelton High School	1761
11	Thomas High School	1635
12	Griffin High School	1468
13	Pena High School	962
14	Holden High School	427

​
​

school_list_pd.head(100)
School ID	name	type	size	budget
0	0	Huang High School	District	2917	1910635
1	1	Figueroa High School	District	2949	1884411
2	2	Shelton High School	Charter	1761	1056600
3	3	Hernandez High School	District	4635	3022020
4	4	Griffin High School	Charter	1468	917500
5	5	Wilson High School	Charter	2283	1319574
6	6	Cabrera High School	Charter	1858	1081356
7	7	Bailey High School	District	4976	3124928
8	8	Holden High School	Charter	427	248087
9	9	Pena High School	Charter	962	585858
10	10	Wright High School	Charter	1800	1049400
11	11	Rodriguez High School	District	3999	2547363
12	12	Johnson High School	District	4761	3094650
13	13	Ford High School	District	2739	1763916
14	14	Thomas High School	Charter	1635	1043130

school_list_pd["Budget per student"]=school_list_pd["budget"]/school_list_pd["size"]
school_list_pd["Budget per student"]
0     655.0
1     639.0
2     600.0
3     652.0
4     625.0
5     578.0
6     582.0
7     628.0
8     581.0
9     609.0
10    583.0
11    637.0
12    650.0
13    644.0
14    638.0
Name: Budget per student, dtype: float64

school2_list_pd = school_list_pd.sort_values(["Budget per student"], ascending=False)
school2_list_pd.reset_index(inplace=True)
school2_list_pd
​
index	School ID	name	type	size	budget	Budget per student
0	0	0	Huang High School	District	2917	1910635	655.0
1	3	3	Hernandez High School	District	4635	3022020	652.0
2	12	12	Johnson High School	District	4761	3094650	650.0
3	13	13	Ford High School	District	2739	1763916	644.0
4	1	1	Figueroa High School	District	2949	1884411	639.0
5	14	14	Thomas High School	Charter	1635	1043130	638.0
6	11	11	Rodriguez High School	District	3999	2547363	637.0
7	7	7	Bailey High School	District	4976	3124928	628.0
8	4	4	Griffin High School	Charter	1468	917500	625.0
9	9	9	Pena High School	Charter	962	585858	609.0
10	2	2	Shelton High School	Charter	1761	1056600	600.0
11	10	10	Wright High School	Charter	1800	1049400	583.0
12	6	6	Cabrera High School	Charter	1858	1081356	582.0
13	8	8	Holden High School	Charter	427	248087	581.0
14	5	5	Wilson High School	Charter	2283	1319574	578.0

merge_table = pd.merge(school2_list_pd, The_numbers_of_student_summany, on="name")
merge_table.head()
index	School ID	name	type	size	budget	Budget per student	The numbers of student
0	0	0	Huang High School	District	2917	1910635	655.0	2917
1	3	3	Hernandez High School	District	4635	3022020	652.0	4635
2	12	12	Johnson High School	District	4761	3094650	650.0	4761
3	13	13	Ford High School	District	2739	1763916	644.0	2739
4	1	1	Figueroa High School	District	2949	1884411	639.0	2949

change_nameto_school=merge_table.rename(columns={"name":"school"})
change_nameto_school
index	School ID	school	type	size	budget	Budget per student	The numbers of student
0	0	0	Huang High School	District	2917	1910635	655.0	2917
1	3	3	Hernandez High School	District	4635	3022020	652.0	4635
2	12	12	Johnson High School	District	4761	3094650	650.0	4761
3	13	13	Ford High School	District	2739	1763916	644.0	2739
4	1	1	Figueroa High School	District	2949	1884411	639.0	2949
5	14	14	Thomas High School	Charter	1635	1043130	638.0	1635
6	11	11	Rodriguez High School	District	3999	2547363	637.0	3999
7	7	7	Bailey High School	District	4976	3124928	628.0	4976
8	4	4	Griffin High School	Charter	1468	917500	625.0	1468
9	9	9	Pena High School	Charter	962	585858	609.0	962
10	2	2	Shelton High School	Charter	1761	1056600	600.0	1761
11	10	10	Wright High School	Charter	1800	1049400	583.0	1800
12	6	6	Cabrera High School	Charter	1858	1081356	582.0	1858
13	8	8	Holden High School	Charter	427	248087	581.0	427
14	5	5	Wilson High School	Charter	2283	1319574	578.0	2283

​

​

groupSchool=student_list_pd.groupby("school").sum()
groupSchool.reset_index(level=0, inplace=True)
groupSchool.head()
school	Student ID	reading_score	math_score
0	Bailey High School	101303896	403225	383393
1	Cabrera High School	31477307	156027	154329
2	Figueroa High School	12949059	239335	226223
3	Ford High School	99055935	221164	211184
4	Griffin High School	19077394	123043	122360

groupSchool_mean=student_list_pd.groupby("school").mean()
groupSchool_mean
groupSchool_mean.reset_index(level=0, inplace=True)
groupSchool_mean
#renamed_df = groupSchool.rename(columns={"reading_score":"ave-reading_score", "math_score":"ave-math_score"})
#renamed_df.head()
school	Student ID	reading_score	math_score
0	Bailey High School	20358.5	81.033963	77.048432
1	Cabrera High School	16941.5	83.975780	83.061895
2	Figueroa High School	4391.0	81.158020	76.711767
3	Ford High School	36165.0	80.746258	77.102592
4	Griffin High School	12995.5	83.816757	83.351499
5	Hernandez High School	9944.0	80.934412	77.289752
6	Holden High School	23060.0	83.814988	83.803279
7	Huang High School	1458.0	81.182722	76.629414
8	Johnson High School	32415.0	80.966394	77.072464
9	Pena High School	23754.5	84.044699	83.839917
10	Rodriguez High School	28035.0	80.744686	76.842711
11	Shelton High School	6746.0	83.725724	83.359455
12	Thomas High School	38352.0	83.848930	83.418349
13	Wilson High School	14871.0	83.989488	83.274201
14	Wright High School	25135.5	83.955000	83.682222

renamed_df_groupSchool_mean = groupSchool_mean.rename(columns={"reading_score":"ave-reading_score", "math_score":"ave-math_score"})
renamed_df_groupSchool_mean.head()
renamed_df_groupSchool_mean = groupSchool_mean.rename(columns={"reading_score":"ave-reading_score", "math_score":"ave-math_score"})
renamed_df_groupSchool_mean.head()
school	Student ID	ave-reading_score	ave-math_score
0	Bailey High School	20358.5	81.033963	77.048432
1	Cabrera High School	16941.5	83.975780	83.061895
2	Figueroa High School	4391.0	81.158020	76.711767
3	Ford High School	36165.0	80.746258	77.102592
4	Griffin High School	12995.5	83.816757	83.351499

merge_table2 = pd.merge(renamed_df_groupSchool_mean, groupSchool, on="school")
merge_table2.head()
school	Student ID_x	ave-reading_score	ave-math_score	Student ID_y	reading_score	math_score
0	Bailey High School	20358.5	81.033963	77.048432	101303896	403225	383393
1	Cabrera High School	16941.5	83.975780	83.061895	31477307	156027	154329
2	Figueroa High School	4391.0	81.158020	76.711767	12949059	239335	226223
3	Ford High School	36165.0	80.746258	77.102592	99055935	221164	211184
4	Griffin High School	12995.5	83.816757	83.351499	19077394	123043	122360

final_merge1 = pd.merge(change_nameto_school, merge_table2, on="school")
final_merge1 = pd.merge(change_nameto_school, merge_table2, on="school")
final_merge1.head()
final_merge1.dtypes
​
index                       int64
School ID                   int64
school                     object
type                       object
size                        int64
budget                      int64
Budget per student        float64
The numbers of student      int64
Student ID_x              float64
ave-reading_score         float64
ave-math_score            float64
Student ID_y                int64
reading_score               int64
math_score                  int64
dtype: object

Newschool_list = final_merge1[["school","type",'The numbers of student',"budget","Budget per student","reading_score","math_score","ave-math_score","ave-reading_score"]]
Newschool_list.head()
Newschool_list
​
school	type	The numbers of student	budget	Budget per student	reading_score	math_score	ave-math_score	ave-reading_score
0	Huang High School	District	2917	1910635	655.0	236810	223528	76.629414	81.182722
1	Hernandez High School	District	4635	3022020	652.0	375131	358238	77.289752	80.934412
2	Johnson High School	District	4761	3094650	650.0	385481	366942	77.072464	80.966394
3	Ford High School	District	2739	1763916	644.0	221164	211184	77.102592	80.746258
4	Figueroa High School	District	2949	1884411	639.0	239335	226223	76.711767	81.158020
5	Thomas High School	Charter	1635	1043130	638.0	137093	136389	83.418349	83.848930
6	Rodriguez High School	District	3999	2547363	637.0	322898	307294	76.842711	80.744686
7	Bailey High School	District	4976	3124928	628.0	403225	383393	77.048432	81.033963
8	Griffin High School	Charter	1468	917500	625.0	123043	122360	83.351499	83.816757
9	Pena High School	Charter	962	585858	609.0	80851	80654	83.839917	84.044699
10	Shelton High School	Charter	1761	1056600	600.0	147441	146796	83.359455	83.725724
11	Wright High School	Charter	1800	1049400	583.0	151119	150628	83.682222	83.955000
12	Cabrera High School	Charter	1858	1081356	582.0	156027	154329	83.061895	83.975780
13	Holden High School	Charter	427	248087	581.0	35789	35784	83.803279	83.814988
14	Wilson High School	Charter	2283	1319574	578.0	191748	190115	83.274201	83.989488

Readingcore_pass=student_list_pd.loc[student_list_pd["reading_score"] >= 60,:]
math_and_Readingcore_pass=Readingcore_pass.loc[Readingcore_pass["math_score"] >= 60,:]
math_and_Readingcore_pass.head()
Student ID	name	gender	grade	school	reading_score	math_score
0	0	Paul Bradley	M	9th	Huang High School	66	79
1	1	Victor Smith	M	12th	Huang High School	94	61
2	2	Kevin Rodriguez	M	12th	Huang High School	90	60
4	4	Bonnie Ray	F	9th	Huang High School	97	84
5	5	Bryan Miranda	M	9th	Huang High School	94	94

overall_pass_number =math_and_Readingcore_pass["school"].value_counts()
​
overall_pass_number.head(15)
Bailey High School       4455
Johnson High School      4246
Hernandez High School    4129
Rodriguez High School    3541
Figueroa High School     2608
Huang High School        2592
Ford High School         2446
Wilson High School       2283
Cabrera High School      1858
Wright High School       1800
Shelton High School      1761
Thomas High School       1635
Griffin High School      1468
Pena High School          962
Holden High School        427
Name: school, dtype: int64

rename_The_numbers_of_Passed_summany
The_numbers_of_Passed_summany = pd.DataFrame({"The numbers of student passed both":overall_pass_number})
The_numbers_of_Passed_summany.index.name="name"
The_numbers_of_Passed_summany.reset_index(level=0, inplace=True)
rename_The_numbers_of_Passed_summany =The_numbers_of_Passed_summany.rename(columns={"name":"school"})
​
rename_The_numbers_of_Passed_summany
school	The numbers of student passed both
0	Bailey High School	4455
1	Johnson High School	4246
2	Hernandez High School	4129
3	Rodriguez High School	3541
4	Figueroa High School	2608
5	Huang High School	2592
6	Ford High School	2446
7	Wilson High School	2283
8	Cabrera High School	1858
9	Wright High School	1800
10	Shelton High School	1761
11	Thomas High School	1635
12	Griffin High School	1468
13	Pena High School	962
14	Holden High School	427

Overpassratio_merge
Overpassratio_merge = pd.merge(Newschool_list, rename_The_numbers_of_Passed_summany, on="school")
Overpassratio_merge.head()
school	type	The numbers of student	budget	Budget per student	reading_score	math_score	ave-math_score	ave-reading_score	The numbers of student passed both
0	Huang High School	District	2917	1910635	655.0	236810	223528	76.629414	81.182722	2592
1	Hernandez High School	District	4635	3022020	652.0	375131	358238	77.289752	80.934412	4129
2	Johnson High School	District	4761	3094650	650.0	385481	366942	77.072464	80.966394	4246
3	Ford High School	District	2739	1763916	644.0	221164	211184	77.102592	80.746258	2446
4	Figueroa High School	District	2949	1884411	639.0	239335	226223	76.711767	81.158020	2608

Overpassratio_merge
Overpassratio_merge["overall pass rate"]=(Overpassratio_merge["The numbers of student passed both"]/Overpassratio_merge["The numbers of student"])*100
Overpassratio_merge["overall pass rate"]
0      88.858416
1      89.083064
2      89.182945
3      89.302665
4      88.436758
5     100.000000
6      88.547137
7      89.529743
8     100.000000
9     100.000000
10    100.000000
11    100.000000
12    100.000000
13    100.000000
14    100.000000
Name: overall pass rate, dtype: float64

Overpassratio_merge
Overpassratio_merge = Overpassratio_merge.sort_values(["overall pass rate"], ascending=False)
Overpassratio_merge.reset_index(inplace=True)
Overpassratio_merge.head()
level_0	index	school	type	The numbers of student	budget	Budget per student	reading_score	math_score	ave-math_score	ave-reading_score	The numbers of student passed both	overall pass rate
0	0	5	Thomas High School	Charter	1635	1043130	638.0	137093	136389	83.418349	83.848930	1635	100.0
1	1	8	Griffin High School	Charter	1468	917500	625.0	123043	122360	83.351499	83.816757	1468	100.0
2	2	9	Pena High School	Charter	962	585858	609.0	80851	80654	83.839917	84.044699	962	100.0
3	3	10	Shelton High School	Charter	1761	1056600	600.0	147441	146796	83.359455	83.725724	1761	100.0
4	4	11	Wright High School	Charter	1800	1049400	583.0	151119	150628	83.682222	83.955000	1800	100.0

Smallest_five=Overpassratio_merge.nsmallest(5, "overall pass rate")
Smallest_five
Smallest_five=Overpassratio_merge.nsmallest(5, "overall pass rate")
Smallest_five
level_0	index	school	type	The numbers of student	budget	Budget per student	reading_score	math_score	ave-math_score	ave-reading_score	The numbers of student passed both	overall pass rate
14	14	4	Figueroa High School	District	2949	1884411	639.0	239335	226223	76.711767	81.158020	2608	88.436758
13	13	6	Rodriguez High School	District	3999	2547363	637.0	322898	307294	76.842711	80.744686	3541	88.547137
12	12	0	Huang High School	District	2917	1910635	655.0	236810	223528	76.629414	81.182722	2592	88.858416
11	11	1	Hernandez High School	District	4635	3022020	652.0	375131	358238	77.289752	80.934412	4129	89.083064
10	10	2	Johnson High School	District	4761	3094650	650.0	385481	366942	77.072464	80.966394	4246	89.182945

largest
largest_five=Overpassratio_merge.nlargest(5, "overall pass rate")
largest_five
level_0	index	school	type	The numbers of student	budget	Budget per student	reading_score	math_score	ave-math_score	ave-reading_score	The numbers of student passed both	overall pass rate
0	0	5	Thomas High School	Charter	1635	1043130	638.0	137093	136389	83.418349	83.848930	1635	100.0
1	1	8	Griffin High School	Charter	1468	917500	625.0	123043	122360	83.351499	83.816757	1468	100.0
2	2	9	Pena High School	Charter	962	585858	609.0	80851	80654	83.839917	84.044699	962	100.0
3	3	10	Shelton High School	Charter	1761	1056600	600.0	147441	146796	83.359455	83.725724	1761	100.0
4	4	11	Wright High School	Charter	1800	1049400	583.0	151119	150628	83.682222	83.955000	1800	100.0

Math_score_by_grade=student_list_pd.groupby(["school","grade"]).mean()
Math_score_by_grade.head()
Student ID	reading_score	math_score
school	grade			
Bailey High School	10th	20365.058918	80.907183	76.996772
11th	20345.148681	80.945643	77.515588
12th	20386.724708	80.912451	76.492218
9th	20344.481481	81.303155	77.083676
Cabrera High School	10th	16909.487124	84.253219	83.154506

bins = [60, 70, 80, 90, 100]
group_names = ['Low', 'Okay', 'Good', 'Great']
pd.cut(Overpassratio_merge["ave-math_score"], bins, labels=group_names)
Overpassratio_merge["ave-math_scorey"] = pd.cut(Overpassratio_merge["ave-math_score"], bins, labels=group_names)
pd.cut(Overpassratio_merge["ave-reading_score"], bins, labels=group_names)
Overpassratio_merge["ave-reading_score"] = pd.cut(Overpassratio_merge["ave-reading_score"], bins, labels=group_names)
​
​
Overpassratio_merge.head()
level_0	index	school	type	The numbers of student	budget	Budget per student	reading_score	math_score	ave-math_score	ave-reading_score	The numbers of student passed both	overall pass rate	ave-math_scorey
0	0	5	Thomas High School	Charter	1635	1043130	638.0	137093	136389	83.418349	Good	1635	100.0	Good
1	1	8	Griffin High School	Charter	1468	917500	625.0	123043	122360	83.351499	Good	1468	100.0	Good
2	2	9	Pena High School	Charter	962	585858	609.0	80851	80654	83.839917	Good	962	100.0	Good
3	3	10	Shelton High School	Charter	1761	1056600	600.0	147441	146796	83.359455	Good	1761	100.0	Good
4	4	11	Wright High School	Charter	1800	1049400	583.0	151119	150628	83.682222	Good	1800	100.0	Good

​
