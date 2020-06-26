# utl-importing-a-four-deep-nested-JSON-file-into-SAS-using-R
Importing a four deep nested JSON file into SAS
     Importing a four deep nested JSON file into SAS                                                                              
                                                                                                                                  
          Method                                                                                                                  
             1. Load the nested json file into an R list                                                                          
             2. Create key value pairs for SAS to parse (SAS is a strong parser)                                                  
             3. Result convert this                                                                                               
                                                                                                                                  
                {                                                                                                                 
                  "S2": [                                                                                                         
                    {                                                                                                             
                      "ETL_GE_GE": [                                                                                              
                        {                                                                                                         
                          "SZENARIO_ID": 0,                                                                                       
                          "GESCHAEFT_FID": 705138,                                                                                
                          "LAND_FID": 205,                                                                                        
                    ...                                                                                                           
                                                                                                                                  
                INTO                                                                                                              
                                                                                                                                  
                WORK.WANT total obs=260                                                                                           
                                                                                                                                  
                  KEY                                 VALUE                                                                       
                                                                                                                                  
                  S2.ETL_GE_GE.SZENARIO_ID            0                                                                           
                  S2.ETL_GE_GE.GESCHAEFT_FID          705138                                                                      
                  S2.ETL_GE_GE.LAND_FID               205                                                                         
                  ...                                                                                                             
                                                                                                                                  
                  I leave it up to you to parse and transpose in SAS                                                              
                                                                                                                                  
    github                                                                                                                        
    https://tinyurl.com/ya2yu9jp                                                                                                  
    https://github.com/rogerjdeangelis/utl-importing-a-four-deep-nested-JSON-file-into-SAS-using-R                                
                                                                                                                                  
    StackOverflow SAS                                                                                                             
    https://tinyurl.com/ybuqvwak                                                                                                  
    https://stackoverflow.com/questions/62572616/importing-a-nested-json-into-sas-without-libname-engine                          
                                                                                                                                  
    /*                   _                                                                                                        
    (_)_ __  _ __  _   _| |_                                                                                                      
    | | `_ \| `_ \| | | | __|                                                                                                     
    | | | | | |_) | |_| | |_                                                                                                      
    |_|_| |_| .__/ \__,_|\__|                                                                                                     
            |_|                                                                                                                   
    */                                                                                                                            
                                                                                                                                  
    filename ft15f001 "d:/json/meta.json";                                                                                        
    parmcards4;                                                                                                                   
    {                                                                                                                             
      "S2": [                                                                                                                     
        {                                                                                                                         
          "ETL_GE_GE": [                                                                                                          
            {                                                                                                                     
              "SZENARIO_ID": 0,                                                                                                   
              "GESCHAEFT_FID": 705138,                                                                                            
              "LAND_FID": 205,                                                                                                    
              "TEILKREDIT_FID": 2627502,                                                                                          
              "BOERSENGEHANDELT_TYP_B": false,                                                                                    
              "DURCHLEITBANK_ABGERECHNET_TYP_B": false                                                                            
            },                                                                                                                    
            {                                                                                                                     
              "SZENARIO_ID": 0,                                                                                                   
              "GESCHAEFT_FID": 3138913,                                                                                           
              "LAND_FID": 205,                                                                                                    
              "TEILKREDIT_FID": 2627503,                                                                                          
              "BOERSENGEHANDELT_TYP_B": false,                                                                                    
              "DURCHLEITGESCHAEFT_TYP_B": false,                                                                                  
              "DURCHLEITBANK_ABGERECHNET_TYP_B": false                                                                            
            }                                                                                                                     
          ],                                                                                                                      
          "ETL_SI_SI": [                                                                                                          
            {                                                                                                                     
              "SICHERHEIT_FID": 33435,                                                                                            
              "SZENARIO_ID": 0,                                                                                                   
              "WAEHRUNG_TYP_S": 201                                                                                               
            },                                                                                                                    
            {                                                                                                                     
              "SICHERHEIT_FID": 34244,                                                                                            
              "SZENARIO_ID": 0,                                                                                                   
              "WAEHRUNG_TYP_S": 201                                                                                               
            }                                                                                                                     
          ]                                                                                                                       
        }                                                                                                                         
      ],                                                                                                                          
      "S3": [                                                                                                                     
        {                                                                                                                         
          "RMP_GE_GE": [                                                                                                          
            {                                                                                                                     
              "GESCHAEFT_FID": 705138,                                                                                            
              "AVA": "NaN",                                                                                                       
              "BAROBLIGO": 755940.4336239336,                                                                                     
              "BETRAG_HERAUSGELEGT": 0,                                                                                           
              "BEWERTEN_TYP_B": true,                                                                                             
              "BUCHWERT": 757208.784969132,                                                                                       
              "BEBUCHT_TYP_B": true                                                                                               
            },                                                                                                                    
            {                                                                                                                     
              "GESCHAEFT_FID": 299792458,                                                                                         
              "AVA": "NaN",                                                                                                       
              "BAROBLIGO": 725292.4162682628,                                                                                     
              "BETRAG_HERAUSGELEGT": 0,                                                                                           
              "BEWERTEN_TYP_B": true,                                                                                             
              "BUCHWERT": 727229.2501975278,                                                                                      
              "BEBUCHT_TYP_B": true                                                                                               
            }                                                                                                                     
          ],                                                                                                                      
          "RMP_SI_SI": [                                                                                                          
            {                                                                                                                     
              "SICHERHEIT_FID": 33435,                                                                                            
              "SZENARIO_ID": 0,                                                                                                   
              "MINIMAL_BEWERTUNGSTAG_TECHNISCH_TYP_B": true                                                                       
            },                                                                                                                    
            {                                                                                                                     
              "SICHERHEIT_FID": 34244,                                                                                            
              "SZENARIO_ID": 0,                                                                                                   
              "MINIMAL_BEWERTUNGSTAG_TECHNISCH_TYP_B": false                                                                      
            }                                                                                                                     
          ]                                                                                                                       
        }                                                                                                                         
      ]                                                                                                                           
    }                                                                                                                             
    ;;;;                                                                                                                          
    run;quit;                                                                                                                     
                                                                                                                                  
                                                                                                                                  
    /*           _               _                                                                                                
      ___  _   _| |_ _ __  _   _| |_                                                                                              
     / _ \| | | | __| `_ \| | | | __|                                                                                             
    | (_) | |_| | |_| |_) | |_| | |_                                                                                              
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                             
                    |_|                                                                                                           
    */                                                                                                                            
                                                                                                                                  
    WORK.WANT total obs=39                                                                                                        
                                                                                                                                  
       V1                                                      V2                                                                 
                                                                                                                                  
       S2.ETL_GE_GE.SZENARIO_ID                                0                                                                  
       S2.ETL_GE_GE.GESCHAEFT_FID                              705138                                                             
       S2.ETL_GE_GE.LAND_FID                                   205                                                                
       S2.ETL_GE_GE.TEILKREDIT_FID                             2627502                                                            
       S2.ETL_GE_GE.BOERSENGEHANDELT_TYP_B                     FALSE                                                              
       S2.ETL_GE_GE.DURCHLEITBANK_ABGERECHNET_TYP_B            FALSE                                                              
       S2.ETL_GE_GE.SZENARIO_ID.1                              0                                                                  
       S2.ETL_GE_GE.GESCHAEFT_FID.1                            3138913                                                            
       S2.ETL_GE_GE.LAND_FID.1                                 205                                                                
       S2.ETL_GE_GE.TEILKREDIT_FID.1                           2627503                                                            
       S2.ETL_GE_GE.BOERSENGEHANDELT_TYP_B.1                   FALSE                                                              
       S2.ETL_GE_GE.DURCHLEITGESCHAEFT_TYP_B                   FALSE                                                              
       S2.ETL_GE_GE.DURCHLEITBANK_ABGERECHNET_TYP_B.1          FALSE                                                              
       S2.ETL_SI_SI.SICHERHEIT_FID                             33435                                                              
       S2.ETL_SI_SI.SZENARIO_ID                                0                                                                  
       S2.ETL_SI_SI.WAEHRUNG_TYP_S                             201                                                                
       S2.ETL_SI_SI.SICHERHEIT_FID.1                           34244                                                              
       S2.ETL_SI_SI.SZENARIO_ID.1                              0                                                                  
       S2.ETL_SI_SI.WAEHRUNG_TYP_S.1                           201                                                                
       S3.RMP_GE_GE.GESCHAEFT_FID                              705138                                                             
       S3.RMP_GE_GE.AVA                                        NaN                                                                
       S3.RMP_GE_GE.BAROBLIGO                                  755940.4                                                           
       S3.RMP_GE_GE.BETRAG_HERAUSGELEGT                        0                                                                  
       S3.RMP_GE_GE.BEWERTEN_TYP_B                             TRUE                                                               
       S3.RMP_GE_GE.BUCHWERT                                   757208.8                                                           
       S3.RMP_GE_GE.BEBUCHT_TYP_B                              TRUE                                                               
       S3.RMP_GE_GE.GESCHAEFT_FID.1                            299792458                                                          
       S3.RMP_GE_GE.AVA.1                                      NaN                                                                
       S3.RMP_GE_GE.BAROBLIGO.1                                725292.4                                                           
       S3.RMP_GE_GE.BETRAG_HERAUSGELEGT.1                      0                                                                  
       S3.RMP_GE_GE.BEWERTEN_TYP_B.1                           TRUE                                                               
       S3.RMP_GE_GE.BUCHWERT.1                                 727229.3                                                           
       S3.RMP_GE_GE.BEBUCHT_TYP_B.1                            TRUE                                                               
       S3.RMP_SI_SI.SICHERHEIT_FID                             33435                                                              
       S3.RMP_SI_SI.SZENARIO_ID                                0                                                                  
       S3.RMP_SI_SI.MINIMAL_BEWERTUNGSTAG_TECHNISCH_TYP_B      TRUE                                                               
       S3.RMP_SI_SI.SICHERHEIT_FID.1                           34244                                                              
       S3.RMP_SI_SI.SZENARIO_ID.1                              0                                                                  
       S3.RMP_SI_SI.MINIMAL_BEWERTUNGSTAG_TECHNISCH_TYP_B.1    FALSE                                                              
                                                                                                                                  
                                                                                                                                  
    /*                                                                                                                            
     _ __  _ __ ___   ___ ___  ___ ___                                                                                            
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|                                                                                           
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                           
    | .__/|_|  \___/ \___\___||___/___/                                                                                           
    |_|                                                                                                                           
    */                                                                                                                            
                                                                                                                                  
    proc datasets lib=work nolist;                                                                                                
      delete want;                                                                                                                
    run;quit;                                                                                                                     
                                                                                                                                  
    %utlfkil(d:/xpt/jsnxpo.xpt);  delete if it exists ;                                                                           
                                                                                                                                  
    %utl_submit_r64(resolve('                                                                                                     
                                                                                                                                  
      library("rjson");                                                                                                           
      library(SASxport);                                                                                                          
                                                                                                                                  
      /* load the json file into an R list */                                                                                     
      jsn <- as.data.frame(fromJSON(paste(readLines("d:/json/meta.json"),collapse="")));                                          
                                                                                                                                  
      /* bind the keys with the values */                                                                                         
      want<-as.data.frame(cbind(names(jsn),t(jsn)));                                                                              
                                                                                                                                  
      /* convert R factors to SAS character strings */                                                                            
      want[] <- lapply(want, as.character);                                                                                       
                                                                                                                                  
      /* create sas v5 transport file */                                                                                          
      write.xport(want,file="d:/xpt/jsnxpo.xpt");                                                                                 
    '));                                                                                                                          
                                                                                                                                  
                                                                                                                                  
    libname xpt xport "d:/xpt/jsnxpo.xpt";                                                                                        
    data want ;                                                                                                                   
      set xpt.want;                                                                                                               
    run;quit;                                                                                                                     
    libname xpt clear;                                                                                                            
                                                                                                                                  
                                                                                                                                  
                                                                                                                                  
