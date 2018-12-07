import pandas as pd
import numpy as np
import warnings
warnings.filterwarnings('ignore') - clears all warnings

------------------------------------------------------------------------------------------------------------------------------
pd.options.mode.chained_assignment=None  - Stop the warning message about ""
pd.get_option('display.max_rows')
pd.set_option('display.max_rows', None) - clear row limit ("Warning")
pd.get_option('display.max_columns')
pd.set_option('display.max_columns',None) - clear column limit
pd.describe_option() -  offline documentation  
pd.reset_option('all') - reset all options
------------------------------------------------------------------------------------------------------------------------------
df=pd.read_excel(C/path/to/file.xlsx",sheet_name"Sheet1") - Import excel spreadshet`s Sheet1
df=pd.read_table(data,sep=|,header=None,names=user_cols) - import data where separator is "|"
df = pd.read_csv("bad-file.csv", error_bad_lines=False)  - Ignore bad lines

------------------------------------------------------------------------------------------------------------------------------
Columns:

df[["column_name"]] - list only one column 
df.rename(columns={"A":"a"}) - renames columns "A" with "a"
df.columns = df.columns.str.replace(' ', '')     - remove spaces in columns
df.column-name = df.column-name.str.replace(' ', '')     - 
df.columns = df.columns.str.lstrip() -  To remove white space at the beginning of string
df.columns = df.columns.str.rstrip() - 
df.rename(columns={"hp":"bhp"},inplace=True) - rename column hp to bhp
df[df.column-name.str.contains("F[AE]LL.*BI[KC]")] - filter column based on regular expression
------------------------------------------------------------------------------------------------------------------------------

df.shape - will show number of rows [0] and colums [1]
df.info                                                      - will list the name and number of columns, number of rows  
------------------------------------------------------------------------------------------------------------------------------
Change values:

df.loc[(df['column_1'] > 100) & (df["column_2"]<=10),"column8"]=1 - Change cell in column8 to 1 if column1>100 and column2<=10
df1=df.loc[((df["column1"]<=17)&(df["column1"]>=13))]  -  lists values in column1 which are between or eaqual to 13 =><=17
df.loc[df["column1]=="NaN"]="0"                           - Changes the cells which contain NaN to 0
df.loc[df['First Season'] > 1990, 'First Season'] = 1    
df[df['bhp'] > 100]                                      - List all columns where cells in column bhp are > 100
df[(df['column1'] > 100) & (df["column2"]<=10)]          - List all columns where "column1" > 100 and column2<=10 (OR |, equal == )
df["column1"]=df["column1"].replace(["?"],"NA")  - replaces string "?" with NA in column "column1"
df1=df.iloc[0:10]  - creating new df1 with all columns and 10 rows
df1=df.iloc[0:10,0:10]  - creating new df1 with all columns and 10 rows
df3=pd.merge(df1,df2[["col-name","colname5","colname7"]],on="col-name",how="left")  - VLOOKUP equivalent (column) both df need to have identical "col-name" column
df=df.rename({"oldname_col":"newname_col"},axis="columns") - rename column 
df[df["column-name"].str.contains("tch")]   - list all columns where string includes "tch" in column "column-name"
df1=df[df["body-style"].str.match("^ha.*p$")] - using regular expression
df.row.str.extract('(?P<fips>\d{5})((?P<state>[A-Z ]*$)|(?P<county>.*?), (?P<state_code>[A-Z]{2}$))') - matches 5 dgits from column "fips"
df["brand"].str.extract("([A-Z][a-z].*)") - capture with regular expression 
------------------------------------------------------------------------------------------------------------------------------
List:
df["bhp"].unique() - List unique values in a column
