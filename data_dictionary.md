data\_dictionary
================

``` r
url = "https://chronicdata.cdc.gov/500-Cities/500-Cities-City-level-Data-GIS-Friendly-Format-201/k56w-7tny"


read_dict = function(url) {
  
  h = read_html(url)
  
  var_name = h %>%
    html_nodes(".column-summary .column-name") %>%
    html_text()
  
  var_description = h %>%
    html_nodes(".Linkify") %>%
    html_text()
  
  var_type = h %>%
    html_nodes(".type-name") %>%
    html_text()
  
  tibble(
    name = var_name,
    description = var_description,
    type = var_type
  )
}



data_dictionary = read_dict("https://chronicdata.cdc.gov/500-Cities/500-Cities-City-level-Data-GIS-Friendly-Format-201/k56w-7tny")
```

This doesn't read in anything? So for now I copied from the webpage into an excel file (will try to figure this out to get the selector gadget to work before submission)

``` r
data_dictionary = readxl::read_xlsx("./data/data_dictionary.xlsx") 
data_dictionary = data_dictionary %>%
  janitor::clean_names() %>%
  filter(column_name %in% c("StateAbbr", "PlaceName", "Population2010", "ACCESS2_CrudePrev", "ACCESS2_AdjPrev", "BPHIGH_CrudePrev", "BPHIGH_AdjPrev", "BPMED_CrudePrev", "BPMED_AdjPrev", "CANCER_CrudePrev", "CANCER_AdjPrev", "CHD_CrudePrev", "CHD_AdjPrev", "CHECKUP_CrudePrev", "CHECKUP_AdjPrev", "CHOLSCREEN_CrudePrev", "CHOLSCREEN_AdjPrev", "COLON_SCREEN_CrudePrev", "COLON_SCREEN_AdjPrev", "COPD_CrudePrev", "COPD_AdjPrev", "COREM_CrudePrev", "COREM_AdjPrev", "COREW_CrudePrev", "COREW_AdjPrev", "DENTAL_CrudePrev", "DENTAL_AdjPrev", "DIABETES_CrudePrev", "DIABETES_AdjPrev", "HIGHCHOL_CrudePrev", "HIGHCHOL_AdjPrev", "LPA_CrudePrev", "LPA_AdjPrev", "MAMMOUSE_CrudePrev", "MAMMOUSE_AdjPrev", "OBESITY_CrudePrev", "OBESITY_AdjPrev", "PAPTEST_CrudePrev", "PAPTEST_AdjPrev", "PHLTH_CrudePrev", "PHLTH_AdjPrev", "STROKE_CrudePrev", "STROKE_AdjPrev", "Geolocation"))
```
