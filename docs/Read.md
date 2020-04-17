# Read and Clean

## Read data

The functions are designed to bring in data from either a remote source or from your local machine. Data from remote sources are accessed through URLs. Data from your local machine is read by opening up a file system browser, identifying a file, and importing the selected file. Each method returns  Pandas data frame.

### read_data_from_remote_json(URL):

The read_data_frame_from_remote_json function reads JSON files from a URL. JSON data is flattened (in the case of nested data) and cast into Pandas data frame.

### read_data_frame_from_local_csv(col_names = [], delim_whitespace=False, header = 'infer'):

This function allows you to import local character-delimited (commas, tabs, spaces) files. All parameters are optional. By default, the function will infer the header from the data, but an explicit header can be specified.

### read_data_frame_from_remote_csv(csv_url, col_names = [], delim_whitespace=False, header = 'infer'):

This function works the same way as read_data_frame_from_local_csv function except that it reads the file from a URL instead of from your local machine. The URL is required.

### read_data_frame_from_local_excel_file():

This function allows you to import XLSX files. When the file explorer is launched, you must select an XLSX file or the function will result in an error.

## Clean data

### clean_dataframe(df, impute = False, text_fields = [], date_fields = [], numeric_fields = [], categorical_fields = []):

The clean_dataframe method imputes missing data, cleans the column headings, removes empty rows and columns, anonymizes text, and casts fields to their proper data type. Except for the data, every input field for clean_dataframe is optional. By default the method will not impute missing data. If instructed, clean_dataframe will replace missing numeric fields with the mean value and replace missing categorical fields with the mode.