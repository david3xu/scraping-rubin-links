pandas.DataFrame — pandas 2.2.2 documentation
Skip to main content
Back to top
Ctrl+K
Site Navigation
Getting started
User Guide
API reference
Development
Release notes
GitHub
Twitter
Mastodon
Site Navigation
Getting started
User Guide
API reference
Development
Release notes
GitHub
Twitter
Mastodon
Input/output
General functions
Series
DataFrame
pandas.DataFrame
pandas.DataFrame.index
pandas.DataFrame.columns
pandas.DataFrame.dtypes
pandas.DataFrame.info
pandas.DataFrame.select_dtypes
pandas.DataFrame.values
pandas.DataFrame.axes
pandas.DataFrame.ndim
pandas.DataFrame.size
pandas.DataFrame.shape
pandas.DataFrame.memory_usage
pandas.DataFrame.empty
pandas.DataFrame.set_flags
pandas.DataFrame.astype
pandas.DataFrame.convert_dtypes
pandas.DataFrame.infer_objects
pandas.DataFrame.copy
pandas.DataFrame.bool
pandas.DataFrame.to_numpy
pandas.DataFrame.head
pandas.DataFrame.at
pandas.DataFrame.iat
pandas.DataFrame.loc
pandas.DataFrame.iloc
pandas.DataFrame.insert
pandas.DataFrame.__iter__
pandas.DataFrame.items
pandas.DataFrame.keys
pandas.DataFrame.iterrows
pandas.DataFrame.itertuples
pandas.DataFrame.pop
pandas.DataFrame.tail
pandas.DataFrame.xs
pandas.DataFrame.get
pandas.DataFrame.isin
pandas.DataFrame.where
pandas.DataFrame.mask
pandas.DataFrame.query
pandas.DataFrame.__add__
pandas.DataFrame.add
pandas.DataFrame.sub
pandas.DataFrame.mul
pandas.DataFrame.div
pandas.DataFrame.truediv
pandas.DataFrame.floordiv
pandas.DataFrame.mod
pandas.DataFrame.pow
pandas.DataFrame.dot
pandas.DataFrame.radd
pandas.DataFrame.rsub
pandas.DataFrame.rmul
pandas.DataFrame.rdiv
pandas.DataFrame.rtruediv
pandas.DataFrame.rfloordiv
pandas.DataFrame.rmod
pandas.DataFrame.rpow
pandas.DataFrame.lt
pandas.DataFrame.gt
pandas.DataFrame.le
pandas.DataFrame.ge
pandas.DataFrame.ne
pandas.DataFrame.eq
pandas.DataFrame.combine
pandas.DataFrame.combine_first
pandas.DataFrame.apply
pandas.DataFrame.map
pandas.DataFrame.applymap
pandas.DataFrame.pipe
pandas.DataFrame.agg
pandas.DataFrame.aggregate
pandas.DataFrame.transform
pandas.DataFrame.groupby
pandas.DataFrame.rolling
pandas.DataFrame.expanding
pandas.DataFrame.ewm
pandas.DataFrame.abs
pandas.DataFrame.all
pandas.DataFrame.any
pandas.DataFrame.clip
pandas.DataFrame.corr
pandas.DataFrame.corrwith
pandas.DataFrame.count
pandas.DataFrame.cov
pandas.DataFrame.cummax
pandas.DataFrame.cummin
pandas.DataFrame.cumprod
pandas.DataFrame.cumsum
pandas.DataFrame.describe
pandas.DataFrame.diff
pandas.DataFrame.eval
pandas.DataFrame.kurt
pandas.DataFrame.kurtosis
pandas.DataFrame.max
pandas.DataFrame.mean
pandas.DataFrame.median
pandas.DataFrame.min
pandas.DataFrame.mode
pandas.DataFrame.pct_change
pandas.DataFrame.prod
pandas.DataFrame.product
pandas.DataFrame.quantile
pandas.DataFrame.rank
pandas.DataFrame.round
pandas.DataFrame.sem
pandas.DataFrame.skew
pandas.DataFrame.sum
pandas.DataFrame.std
pandas.DataFrame.var
pandas.DataFrame.nunique
pandas.DataFrame.value_counts
pandas.DataFrame.add_prefix
pandas.DataFrame.add_suffix
pandas.DataFrame.align
pandas.DataFrame.at_time
pandas.DataFrame.between_time
pandas.DataFrame.drop
pandas.DataFrame.drop_duplicates
pandas.DataFrame.duplicated
pandas.DataFrame.equals
pandas.DataFrame.filter
pandas.DataFrame.first
pandas.DataFrame.head
pandas.DataFrame.idxmax
pandas.DataFrame.idxmin
pandas.DataFrame.last
pandas.DataFrame.reindex
pandas.DataFrame.reindex_like
pandas.DataFrame.rename
pandas.DataFrame.rename_axis
pandas.DataFrame.reset_index
pandas.DataFrame.sample
pandas.DataFrame.set_axis
pandas.DataFrame.set_index
pandas.DataFrame.tail
pandas.DataFrame.take
pandas.DataFrame.truncate
pandas.DataFrame.backfill
pandas.DataFrame.bfill
pandas.DataFrame.dropna
pandas.DataFrame.ffill
pandas.DataFrame.fillna
pandas.DataFrame.interpolate
pandas.DataFrame.isna
pandas.DataFrame.isnull
pandas.DataFrame.notna
pandas.DataFrame.notnull
pandas.DataFrame.pad
pandas.DataFrame.replace
pandas.DataFrame.droplevel
pandas.DataFrame.pivot
pandas.DataFrame.pivot_table
pandas.DataFrame.reorder_levels
pandas.DataFrame.sort_values
pandas.DataFrame.sort_index
pandas.DataFrame.nlargest
pandas.DataFrame.nsmallest
pandas.DataFrame.swaplevel
pandas.DataFrame.stack
pandas.DataFrame.unstack
pandas.DataFrame.swapaxes
pandas.DataFrame.melt
pandas.DataFrame.explode
pandas.DataFrame.squeeze
pandas.DataFrame.to_xarray
pandas.DataFrame.T
pandas.DataFrame.transpose
pandas.DataFrame.assign
pandas.DataFrame.compare
pandas.DataFrame.join
pandas.DataFrame.merge
pandas.DataFrame.update
pandas.DataFrame.asfreq
pandas.DataFrame.asof
pandas.DataFrame.shift
pandas.DataFrame.first_valid_index
pandas.DataFrame.last_valid_index
pandas.DataFrame.resample
pandas.DataFrame.to_period
pandas.DataFrame.to_timestamp
pandas.DataFrame.tz_convert
pandas.DataFrame.tz_localize
pandas.Flags
pandas.DataFrame.attrs
pandas.DataFrame.plot
pandas.DataFrame.plot.area
pandas.DataFrame.plot.bar
pandas.DataFrame.plot.barh
pandas.DataFrame.plot.box
pandas.DataFrame.plot.density
pandas.DataFrame.plot.hexbin
pandas.DataFrame.plot.hist
pandas.DataFrame.plot.kde
pandas.DataFrame.plot.line
pandas.DataFrame.plot.pie
pandas.DataFrame.plot.scatter
pandas.DataFrame.boxplot
pandas.DataFrame.hist
pandas.DataFrame.sparse.density
pandas.DataFrame.sparse.from_spmatrix
pandas.DataFrame.sparse.to_coo
pandas.DataFrame.sparse.to_dense
pandas.DataFrame.from_dict
pandas.DataFrame.from_records
pandas.DataFrame.to_orc
pandas.DataFrame.to_parquet
pandas.DataFrame.to_pickle
pandas.DataFrame.to_csv
pandas.DataFrame.to_hdf
pandas.DataFrame.to_sql
pandas.DataFrame.to_dict
pandas.DataFrame.to_excel
pandas.DataFrame.to_json
pandas.DataFrame.to_html
pandas.DataFrame.to_feather
pandas.DataFrame.to_latex
pandas.DataFrame.to_stata
pandas.DataFrame.to_gbq
pandas.DataFrame.to_records
pandas.DataFrame.to_string
pandas.DataFrame.to_clipboard
pandas.DataFrame.to_markdown
pandas.DataFrame.style
pandas.DataFrame.__dataframe__
pandas arrays, scalars, and data types
Index objects
Date offsets
Window
GroupBy
Resampling
Style
Plotting
Options and settings
Extensions
Testing
Missing values
API reference
DataFrame
pandas.DataFrame
pandas.DataFrame#
class pandas.DataFrame(data=None, index=None, columns=None, dtype=None, copy=None)[source]#
Two-dimensional, size-mutable, potentially heterogeneous tabular data.
Data structure also contains labeled axes (rows and columns).
Arithmetic operations align on both row and column labels. Can be
thought of as a dict-like container for Series objects. The primary
pandas data structure.
Parameters:
datandarray (structured or homogeneous), Iterable, dict, or DataFrameDict can contain Series, arrays, constants, dataclass or list-like objects. If
data is a dict, column order follows insertion-order. If a dict contains Series
which have an index defined, it is aligned by its index. This alignment also
occurs if data is a Series or a DataFrame itself. Alignment is done on
Series/DataFrame inputs.
If data is a list of dicts, column order follows insertion-order.
indexIndex or array-likeIndex to use for resulting frame. Will default to RangeIndex if
no indexing information part of input data and no index provided.
columnsIndex or array-likeColumn labels to use for resulting frame when data does not have them,
defaulting to RangeIndex(0, 1, 2, …, n). If data contains column labels,
will perform column selection instead.
dtypedtype, default NoneData type to force. Only a single dtype is allowed. If None, infer.
copybool or None, default NoneCopy data from inputs.
For dict data, the default of None behaves like copy=True. For DataFrame
or 2d ndarray input, the default of None behaves like copy=False.
If data is a dict containing one or more Series (possibly of different dtypes),
copy=False will ensure that these inputs are not copied.
Changed in version 1.3.0.
See also
DataFrame.from_recordsConstructor from tuples, also record arrays.
DataFrame.from_dictFrom dicts of Series, arrays, or dicts.
read_csvRead a comma-separated values (csv) file into DataFrame.
read_tableRead general delimited file into DataFrame.
read_clipboardRead text from clipboard into DataFrame.
Notes
Please reference the User Guide for more information.
Examples
Constructing DataFrame from a dictionary.
>>> d = {'col1': [1, 2], 'col2': [3, 4]}
>>> df = pd.DataFrame(data=d)
>>> df
col1
col2
0
1
3
1
2
4
Notice that the inferred dtype is int64.
>>> df.dtypes
col1
int64
col2
int64
dtype: object
To enforce a single dtype:
>>> df = pd.DataFrame(data=d, dtype=np.int8)
>>> df.dtypes
col1
int8
col2
int8
dtype: object
Constructing DataFrame from a dictionary including Series:
>>> d = {'col1': [0, 1, 2, 3], 'col2': pd.Series([2, 3], index=[2, 3])}
>>> pd.DataFrame(data=d, index=[0, 1, 2, 3])
col1
col2
0
0
NaN
1
1
NaN
2
2
2.0
3
3
3.0
Constructing DataFrame from numpy ndarray:
>>> df2 = pd.DataFrame(np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]),
...
columns=['a', 'b', 'c'])
>>> df2
a
b
c
0
1
2
3
1
4
5
6
2
7
8
9
Constructing DataFrame from a numpy ndarray that has labeled columns:
>>> data = np.array([(1, 2, 3), (4, 5, 6), (7, 8, 9)],
...
dtype=[("a", "i4"), ("b", "i4"), ("c", "i4")])
>>> df3 = pd.DataFrame(data, columns=['c', 'a'])
...
>>> df3
c
a
0
3
1
1
6
4
2
9
7
Constructing DataFrame from dataclass:
>>> from dataclasses import make_dataclass
>>> Point = make_dataclass("Point", [("x", int), ("y", int)])
>>> pd.DataFrame([Point(0, 0), Point(0, 3), Point(2, 3)])
x
y
0
0
0
1
0
3
2
2
3
Constructing DataFrame from Series/DataFrame:
>>> ser = pd.Series([1, 2, 3], index=["a", "b", "c"])
>>> df = pd.DataFrame(data=ser, index=["a", "c"])
>>> df
0
a
1
c
3
>>> df1 = pd.DataFrame([1, 2, 3], index=["a", "b", "c"], columns=["x"])
>>> df2 = pd.DataFrame(data=df1, index=["a", "c"])
>>> df2
x
a
1
c
3
Attributes
T
The transpose of the DataFrame.
at
Access a single value for a row/column label pair.
attrs
Dictionary of global attributes of this dataset.
axes
Return a list representing the axes of the DataFrame.
columns
The column labels of the DataFrame.
dtypes
Return the dtypes in the DataFrame.
empty
Indicator whether Series/DataFrame is empty.
flags
Get the properties associated with this pandas object.
iat
Access a single value for a row/column pair by integer position.
iloc
(DEPRECATED) Purely integer-location based indexing for selection by position.
index
The index (row labels) of the DataFrame.
loc
Access a group of rows and columns by label(s) or a boolean array.
ndim
Return an int representing the number of axes / array dimensions.
shape
Return a tuple representing the dimensionality of the DataFrame.
size
Return an int representing the number of elements in this object.
style
Returns a Styler object.
values
Return a Numpy representation of the DataFrame.
Methods
abs()
Return a Series/DataFrame with absolute numeric value of each element.
add(other[, axis, level, fill_value])
Get Addition of dataframe and other, element-wise (binary operator add).
add_prefix(prefix[, axis])
Prefix labels with string prefix.
add_suffix(suffix[, axis])
Suffix labels with string suffix.
agg([func, axis])
Aggregate using one or more operations over the specified axis.
aggregate([func, axis])
Aggregate using one or more operations over the specified axis.
align(other[, join, axis, level, copy, ...])
Align two objects on their axes with the specified join method.
all([axis, bool_only, skipna])
Return whether all elements are True, potentially over an axis.
any(*[, axis, bool_only, skipna])
Return whether any element is True, potentially over an axis.
apply(func[, axis, raw, result_type, args, ...])
Apply a function along an axis of the DataFrame.
applymap(func[, na_action])
(DEPRECATED) Apply a function to a Dataframe elementwise.
asfreq(freq[, method, how, normalize, ...])
Convert time series to specified frequency.
asof(where[, subset])
Return the last row(s) without any NaNs before where.
assign(**kwargs)
Assign new columns to a DataFrame.
astype(dtype[, copy, errors])
Cast a pandas object to a specified dtype dtype.
at_time(time[, asof, axis])
Select values at particular time of day (e.g., 9:30AM).
backfill(*[, axis, inplace, limit, downcast])
(DEPRECATED) Fill NA/NaN values by using the next valid observation to fill the gap.
between_time(start_time, end_time[, ...])
Select values between particular times of the day (e.g., 9:00-9:30 AM).
bfill(*[, axis, inplace, limit, limit_area, ...])
Fill NA/NaN values by using the next valid observation to fill the gap.
bool()
(DEPRECATED) Return the bool of a single element Series or DataFrame.
boxplot([column, by, ax, fontsize, rot, ...])
Make a box plot from DataFrame columns.
clip([lower, upper, axis, inplace])
Trim values at input threshold(s).
combine(other, func[, fill_value, overwrite])
Perform column-wise combine with another DataFrame.
combine_first(other)
Update null elements with value in the same location in other.
compare(other[, align_axis, keep_shape, ...])
Compare to another DataFrame and show the differences.
convert_dtypes([infer_objects, ...])
Convert columns to the best possible dtypes using dtypes supporting pd.NA.
copy([deep])
Make a copy of this object's indices and data.
corr([method, min_periods, numeric_only])
Compute pairwise correlation of columns, excluding NA/null values.
corrwith(other[, axis, drop, method, ...])
Compute pairwise correlation.
count([axis, numeric_only])
Count non-NA cells for each column or row.
cov([min_periods, ddof, numeric_only])
Compute pairwise covariance of columns, excluding NA/null values.
cummax([axis, skipna])
Return cumulative maximum over a DataFrame or Series axis.
cummin([axis, skipna])
Return cumulative minimum over a DataFrame or Series axis.
cumprod([axis, skipna])
Return cumulative product over a DataFrame or Series axis.
cumsum([axis, skipna])
Return cumulative sum over a DataFrame or Series axis.
describe([percentiles, include, exclude])
Generate descriptive statistics.
diff([periods, axis])
First discrete difference of element.
div(other[, axis, level, fill_value])
Get Floating division of dataframe and other, element-wise (binary operator truediv).
divide(other[, axis, level, fill_value])
Get Floating division of dataframe and other, element-wise (binary operator truediv).
dot(other)
Compute the matrix multiplication between the DataFrame and other.
drop([labels, axis, index, columns, level, ...])
Drop specified labels from rows or columns.
drop_duplicates([subset, keep, inplace, ...])
Return DataFrame with duplicate rows removed.
droplevel(level[, axis])
Return Series/DataFrame with requested index / column level(s) removed.
dropna(*[, axis, how, thresh, subset, ...])
Remove missing values.
duplicated([subset, keep])
Return boolean Series denoting duplicate rows.
eq(other[, axis, level])
Get Equal to of dataframe and other, element-wise (binary operator eq).
equals(other)
Test whether two objects contain the same elements.
eval(expr, *[, inplace])
Evaluate a string describing operations on DataFrame columns.
ewm([com, span, halflife, alpha, ...])
Provide exponentially weighted (EW) calculations.
expanding([min_periods, axis, method])
Provide expanding window calculations.
explode(column[, ignore_index])
Transform each element of a list-like to a row, replicating index values.
ffill(*[, axis, inplace, limit, limit_area, ...])
Fill NA/NaN values by propagating the last valid observation to next valid.
fillna([value, method, axis, inplace, ...])
Fill NA/NaN values using the specified method.
filter([items, like, regex, axis])
Subset the dataframe rows or columns according to the specified index labels.
first(offset)
(DEPRECATED) Select initial periods of time series data based on a date offset.
first_valid_index()
Return index for first non-NA value or None, if no non-NA value is found.
floordiv(other[, axis, level, fill_value])
Get Integer division of dataframe and other, element-wise (binary operator floordiv).
from_dict(data[, orient, dtype, columns])
Construct DataFrame from dict of array-like or dicts.
from_records(data[, index, exclude, ...])
Convert structured or record ndarray to DataFrame.
ge(other[, axis, level])
Get Greater than or equal to of dataframe and other, element-wise (binary operator ge).
get(key[, default])
Get item from object for given key (ex: DataFrame column).
groupby([by, axis, level, as_index, sort, ...])
Group DataFrame using a mapper or by a Series of columns.
gt(other[, axis, level])
Get Greater than of dataframe and other, element-wise (binary operator gt).
head([n])
Return the first n rows.
hist([column, by, grid, xlabelsize, xrot, ...])
Make a histogram of the DataFrame's columns.
idxmax([axis, skipna, numeric_only])
Return index of first occurrence of maximum over requested axis.
idxmin([axis, skipna, numeric_only])
Return index of first occurrence of minimum over requested axis.
infer_objects([copy])
Attempt to infer better dtypes for object columns.
info([verbose, buf, max_cols, memory_usage, ...])
Print a concise summary of a DataFrame.
insert(loc, column, value[, allow_duplicates])
Insert column into DataFrame at specified location.
interpolate([method, axis, limit, inplace, ...])
Fill NaN values using an interpolation method.
isetitem(loc, value)
Set the given value in the column with position loc.
isin(values)
Whether each element in the DataFrame is contained in values.
isna()
Detect missing values.
isnull()
DataFrame.isnull is an alias for DataFrame.isna.
items()
Iterate over (column name, Series) pairs.
iterrows()
Iterate over DataFrame rows as (index, Series) pairs.
itertuples([index, name])
Iterate over DataFrame rows as namedtuples.
join(other[, on, how, lsuffix, rsuffix, ...])
Join columns of another DataFrame.
keys()
Get the 'info axis' (see Indexing for more).
kurt([axis, skipna, numeric_only])
Return unbiased kurtosis over requested axis.
kurtosis([axis, skipna, numeric_only])
Return unbiased kurtosis over requested axis.
last(offset)
(DEPRECATED) Select final periods of time series data based on a date offset.
last_valid_index()
Return index for last non-NA value or None, if no non-NA value is found.
le(other[, axis, level])
Get Less than or equal to of dataframe and other, element-wise (binary operator le).
lt(other[, axis, level])
Get Less than of dataframe and other, element-wise (binary operator lt).
map(func[, na_action])
Apply a function to a Dataframe elementwise.
mask(cond[, other, inplace, axis, level])
Replace values where the condition is True.
max([axis, skipna, numeric_only])
Return the maximum of the values over the requested axis.
mean([axis, skipna, numeric_only])
Return the mean of the values over the requested axis.
median([axis, skipna, numeric_only])
Return the median of the values over the requested axis.
melt([id_vars, value_vars, var_name, ...])
Unpivot a DataFrame from wide to long format, optionally leaving identifiers set.
memory_usage([index, deep])
Return the memory usage of each column in bytes.
merge(right[, how, on, left_on, right_on, ...])
Merge DataFrame or named Series objects with a database-style join.
min([axis, skipna, numeric_only])
Return the minimum of the values over the requested axis.
mod(other[, axis, level, fill_value])
Get Modulo of dataframe and other, element-wise (binary operator mod).
mode([axis, numeric_only, dropna])
Get the mode(s) of each element along the selected axis.
mul(other[, axis, level, fill_value])
Get Multiplication of dataframe and other, element-wise (binary operator mul).
multiply(other[, axis, level, fill_value])
Get Multiplication of dataframe and other, element-wise (binary operator mul).
ne(other[, axis, level])
Get Not equal to of dataframe and other, element-wise (binary operator ne).
nlargest(n, columns[, keep])
Return the first n rows ordered by columns in descending order.
notna()
Detect existing (non-missing) values.
notnull()
DataFrame.notnull is an alias for DataFrame.notna.
nsmallest(n, columns[, keep])
Return the first n rows ordered by columns in ascending order.
nunique([axis, dropna])
Count number of distinct elements in specified axis.
pad(*[, axis, inplace, limit, downcast])
(DEPRECATED) Fill NA/NaN values by propagating the last valid observation to next valid.
pct_change([periods, fill_method, limit, freq])
Fractional change between the current and a prior element.
pipe(func, *args, **kwargs)
Apply chainable functions that expect Series or DataFrames.
pivot(*, columns[, index, values])
Return reshaped DataFrame organized by given index / column values.
pivot_table([values, index, columns, ...])
Create a spreadsheet-style pivot table as a DataFrame.
pop(item)
Return item and drop from frame.
pow(other[, axis, level, fill_value])
Get Exponential power of dataframe and other, element-wise (binary operator pow).
prod([axis, skipna, numeric_only, min_count])
Return the product of the values over the requested axis.
product([axis, skipna, numeric_only, min_count])
Return the product of the values over the requested axis.
quantile([q, axis, numeric_only, ...])
Return values at the given quantile over requested axis.
query(expr, *[, inplace])
Query the columns of a DataFrame with a boolean expression.
radd(other[, axis, level, fill_value])
Get Addition of dataframe and other, element-wise (binary operator radd).
rank([axis, method, numeric_only, ...])
Compute numerical data ranks (1 through n) along axis.
rdiv(other[, axis, level, fill_value])
Get Floating division of dataframe and other, element-wise (binary operator rtruediv).
reindex([labels, index, columns, axis, ...])
Conform DataFrame to new index with optional filling logic.
reindex_like(other[, method, copy, limit, ...])
Return an object with matching indices as other object.
rename([mapper, index, columns, axis, copy, ...])
Rename columns or index labels.
rename_axis([mapper, index, columns, axis, ...])
Set the name of the axis for the index or columns.
reorder_levels(order[, axis])
Rearrange index levels using input order.
replace([to_replace, value, inplace, limit, ...])
Replace values given in to_replace with value.
resample(rule[, axis, closed, label, ...])
Resample time-series data.
reset_index([level, drop, inplace, ...])
Reset the index, or a level of it.
rfloordiv(other[, axis, level, fill_value])
Get Integer division of dataframe and other, element-wise (binary operator rfloordiv).
rmod(other[, axis, level, fill_value])
Get Modulo of dataframe and other, element-wise (binary operator rmod).
rmul(other[, axis, level, fill_value])
Get Multiplication of dataframe and other, element-wise (binary operator rmul).
rolling(window[, min_periods, center, ...])
Provide rolling window calculations.
round([decimals])
Round a DataFrame to a variable number of decimal places.
rpow(other[, axis, level, fill_value])
Get Exponential power of dataframe and other, element-wise (binary operator rpow).
rsub(other[, axis, level, fill_value])
Get Subtraction of dataframe and other, element-wise (binary operator rsub).
rtruediv(other[, axis, level, fill_value])
Get Floating division of dataframe and other, element-wise (binary operator rtruediv).
sample([n, frac, replace, weights, ...])
Return a random sample of items from an axis of object.
select_dtypes([include, exclude])
Return a subset of the DataFrame's columns based on the column dtypes.
sem([axis, skipna, ddof, numeric_only])
Return unbiased standard error of the mean over requested axis.
set_axis(labels, *[, axis, copy])
Assign desired index to given axis.
set_flags(*[, copy, allows_duplicate_labels])
Return a new object with updated flags.
set_index(keys, *[, drop, append, inplace, ...])
Set the DataFrame index using existing columns.
shift([periods, freq, axis, fill_value, suffix])
Shift index by desired number of periods with an optional time freq.
skew([axis, skipna, numeric_only])
Return unbiased skew over requested axis.
sort_index(*[, axis, level, ascending, ...])
Sort object by labels (along an axis).
sort_values(by, *[, axis, ascending, ...])
Sort by the values along either axis.
squeeze([axis])
Squeeze 1 dimensional axis objects into scalars.
stack([level, dropna, sort, future_stack])
Stack the prescribed level(s) from columns to index.
std([axis, skipna, ddof, numeric_only])
Return sample standard deviation over requested axis.
sub(other[, axis, level, fill_value])
Get Subtraction of dataframe and other, element-wise (binary operator sub).
subtract(other[, axis, level, fill_value])
Get Subtraction of dataframe and other, element-wise (binary operator sub).
sum([axis, skipna, numeric_only, min_count])
Return the sum of the values over the requested axis.
swapaxes(axis1, axis2[, copy])
(DEPRECATED) Interchange axes and swap values axes appropriately.
swaplevel([i, j, axis])
Swap levels i and j in a MultiIndex.
tail([n])
Return the last n rows.
take(indices[, axis])
Return the elements in the given positional indices along an axis.
to_clipboard(*[, excel, sep])
Copy object to the system clipboard.
to_csv([path_or_buf, sep, na_rep, ...])
Write object to a comma-separated values (csv) file.
to_dict([orient, into, index])
Convert the DataFrame to a dictionary.
to_excel(excel_writer, *[, sheet_name, ...])
Write object to an Excel sheet.
to_feather(path, **kwargs)
Write a DataFrame to the binary Feather format.
to_gbq(destination_table, *[, project_id, ...])
(DEPRECATED) Write a DataFrame to a Google BigQuery table.
to_hdf(path_or_buf, *, key[, mode, ...])
Write the contained data to an HDF5 file using HDFStore.
to_html([buf, columns, col_space, header, ...])
Render a DataFrame as an HTML table.
to_json([path_or_buf, orient, date_format, ...])
Convert the object to a JSON string.
to_latex([buf, columns, header, index, ...])
Render object to a LaTeX tabular, longtable, or nested table.
to_markdown([buf, mode, index, storage_options])
Print DataFrame in Markdown-friendly format.
to_numpy([dtype, copy, na_value])
Convert the DataFrame to a NumPy array.
to_orc([path, engine, index, engine_kwargs])
Write a DataFrame to the ORC format.
to_parquet([path, engine, compression, ...])
Write a DataFrame to the binary parquet format.
to_period([freq, axis, copy])
Convert DataFrame from DatetimeIndex to PeriodIndex.
to_pickle(path, *[, compression, protocol, ...])
Pickle (serialize) object to file.
to_records([index, column_dtypes, index_dtypes])
Convert DataFrame to a NumPy record array.
to_sql(name, con, *[, schema, if_exists, ...])
Write records stored in a DataFrame to a SQL database.
to_stata(path, *[, convert_dates, ...])
Export DataFrame object to Stata dta format.
to_string([buf, columns, col_space, header, ...])
Render a DataFrame to a console-friendly tabular output.
to_timestamp([freq, how, axis, copy])
Cast to DatetimeIndex of timestamps, at beginning of period.
to_xarray()
Return an xarray object from the pandas object.
to_xml([path_or_buffer, index, root_name, ...])
Render a DataFrame to an XML document.
transform(func[, axis])
Call func on self producing a DataFrame with the same axis shape as self.
transpose(*args[, copy])
Transpose index and columns.
truediv(other[, axis, level, fill_value])
Get Floating division of dataframe and other, element-wise (binary operator truediv).
truncate([before, after, axis, copy])
Truncate a Series or DataFrame before and after some index value.
tz_convert(tz[, axis, level, copy])
Convert tz-aware axis to target time zone.
tz_localize(tz[, axis, level, copy, ...])
Localize tz-naive index of a Series or DataFrame to target time zone.
unstack([level, fill_value, sort])
Pivot a level of the (necessarily hierarchical) index labels.
update(other[, join, overwrite, ...])
Modify in place using non-NA values from another DataFrame.
value_counts([subset, normalize, sort, ...])
Return a Series containing the frequency of each distinct row in the Dataframe.
var([axis, skipna, ddof, numeric_only])
Return unbiased variance over requested axis.
where(cond[, other, inplace, axis, level])
Replace values where the condition is False.
xs(key[, axis, level, drop_level])
Return cross-section from the Series/DataFrame.
previous
DataFrame
next
pandas.DataFrame.index
On this page
DataFrame
Show Source
© 2024, pandas via NumFOCUS, Inc. Hosted by OVHcloud.
Created using Sphinx 7.2.6.
Built with the PyData Sphinx Theme 0.14.4.