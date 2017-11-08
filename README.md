# Dynamic_variable_in_a_DOSUBL_execute_macro_in_SAS
Execute a macro query for each observation in the meta data

    ```  Dynamic variable in a DOSUBL execute macro in SAS                                                                                                            ```
    ```                                                                                                                                                               ```
    ```       Execute a macro query for each observation in the meta data                                                                                             ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```       INPUT                                                                                                                                                   ```
    ```       =====                                                                                                                                                   ```
    ```                                                                                                                                                               ```
    ```          WORK.META total obs=3                                                                                                                                ```
    ```                                                                                                                                                               ```
    ```            ROWNUM     NAME                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```               1      Alice                                                                                                                                    ```
    ```               2      John                                                                                                                                     ```
    ```               3      Alfred                                                                                                                                   ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```          MACRO Query                                                                                                                                          ```
    ```                                                                                                                                                               ```
    ```            %macro qry(name);                                                                                                                                  ```
    ```              proc sql;                                                                                                                                        ```
    ```                create                                                                                                                                         ```
    ```                  table want_&name as                                                                                                                          ```
    ```                select                                                                                                                                         ```
    ```                  *                                                                                                                                            ```
    ```                from                                                                                                                                           ```
    ```                  sashelp.class                                                                                                                                ```
    ```                where                                                                                                                                          ```
    ```                  name="&name"                                                                                                                                 ```
    ```              ;quit;                                                                                                                                           ```
    ```            %mend qry;                                                                                                                                         ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```       WORKING CODE ( This is all the code)                                                                                                                    ```
    ```       =====================================                                                                                                                   ```
    ```            data _null_                                                                                                                                        ```
    ```             set meta;                                                                                                                                         ```
    ```              rc=dosubl('%qry('!!name!!');');                                                                                                                  ```
    ```            run;quit;                                                                                                                                          ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```       OUTPUT                                                                                                                                                  ```
    ```       ======                                                                                                                                                  ```
    ```        WORK.WANT_ALICE total obs=1                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```          NAME     SEX    AGE    HEIGHT    WEIGHT                                                                                                              ```
    ```          Alice     F      13     56.5       84                                                                                                                ```
    ```                                                                                                                                                               ```
    ```        WORK.WANT_JOHN total obs=1                                                                                                                             ```
    ```                                                                                                                                                               ```
    ```          NAME    SEX    AGE    HEIGHT    WEIGHT                                                                                                               ```
    ```          John     M      12      59       99.5                                                                                                                ```
    ```                                                                                                                                                               ```
    ```        WORK.WANT_ALFRED total obs=1                                                                                                                           ```
    ```                                                                                                                                                               ```
    ```          NAME     SEX    AGE    HEIGHT    WEIGHT                                                                                                              ```
    ```         Alfred     M      14      69       112.5                                                                                                              ```
    ```                                                                                                                                                               ```
    ```  https://goo.gl/of25L1                                                                                                                                        ```
    ```  https://stackoverflow.com/questions/47175345/dynamic-variable-in-a-call-execute-macro-script-in-sas                                                          ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  *                _              _       _                                                                                                                    ```
    ```   _ __ ___   __ _| | _____    __| | __ _| |_ __ _                                                                                                             ```
    ```  | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |                                                                                                            ```
    ```  | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |                                                                                                            ```
    ```  |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  data meta;                                                                                                                                                   ```
    ```     input Rownum name$;                                                                                                                                       ```
    ```  cards4;                                                                                                                                                      ```
    ```  1 Alice                                                                                                                                                      ```
    ```  2 John                                                                                                                                                       ```
    ```  3 Alfred                                                                                                                                                     ```
    ```  ;;;;                                                                                                                                                         ```
    ```  run;quit;                                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```  *          _       _   _                                                                                                                                     ```
    ```   ___  ___ | |_   _| |_(_) ___  _ __                                                                                                                          ```
    ```  / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                                                         ```
    ```  \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                                                        ```
    ```  |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                                                        ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  data _null_;                                                                                                                                                 ```
    ```    set meta;                                                                                                                                                  ```
    ```      rc=dosubl('%qry('!!name!!');');                                                                                                                          ```
    ```  run;quit;                                                                                                                                                    ```

