pdf["Month"] = pd.to_datetime(pdf["Month"]) - Convert month column to datetime values of a dataframe
pdf.set_index("Month",inplace=True) - make Month valyes to become dataframe`s index
