libname mylib '/path/to/your/data';
/*---------------------------------------------------------
  The options statement below should be placed
  before the data step when submitting this code.
---------------------------------------------------------*/
options VALIDMEMNAME=EXTEND VALIDVARNAME=ANY;
   /*------------------------------------------
   Generated SAS Scoring Code
     Date             : December 16, 2024, 02:40:38 AM
     Locale           : en_US
     Model Type       : Logistic Regression
     Interval variable: Age (Y)
     Interval variable: BMI (kg/m^2)
     Interval variable: Height (m)
     Interval variable: Weight (kg)
     Class variable   : Primary cancer
     Class variable   : va__d__E_Case(Case)
     Response variable: va__d__E_Case(Case)
     Distribution     : Binary
     Link Function    : Logit
     ------------------------------------------*/
/* Temporary Computed Columns */
if (('Case'n = '15094')) then do;
'va__d__E_Case'n= 1.0;
end;
else do;
'va__d__E_Case'n= 0.0;
end;
;

/*------------------------------------------*/
   /*---------------------------------------------------------
     Generated SAS Scoring Code
     Date: 16Dec2024:02:40:38
     -------------------------------------------------------*/

   /*---------------------------------------------------------
   Defining temporary arrays and variables   
     -------------------------------------------------------*/
   drop _badval_ _linp_ _temp_ _i_ _j_;
   _badval_ = 0;
   _linp_   = 0;
   _temp_   = 0;
   _i_      = 0;
   _j_      = 0;
   drop MACLOGBIG;
   MACLOGBIG= 7.0978271289338392e+02;

   array _xrow_36_0_{18} _temporary_;
   array _beta_36_0_{18} _temporary_ (    530.056439009459
           83.1665284872237
           72.7623693162681
           67.9316304917516
           42.7944898085689
           56.5185850765825
           144.118747531439
           -0.6009326460778
           18.8982349914087
           30.1652313693646
           31.5171118300614
           143.719036302657
           35.3143334701582
                          0
           3.85150333644671
          -19.9281201651182
          -472.415075506254
           6.07085295169667);

   length '_Primary cancer_'n $19; drop '_Primary cancer_'n;
   '_Primary cancer_'n = left(trim(put('Primary cancer'n,$19.)));
   /*------------------------------------------*/
   /*Missing values in model variables result  */
   /*in missing values for the prediction.     */
   if missing('Age (Y)'n) 
      or missing('BMI (kg/m^2)'n) 
      or missing('Weight (kg)'n) 
      or missing('Height (m)'n) 
      then do;
         _badval_ = 1;
         goto skip_36_0;
   end;
   /*------------------------------------------*/

   do _i_=1 to 18; _xrow_36_0_{_i_} = 0; end;

   _xrow_36_0_[1] = 1;

   _temp_ = 1;
   select ('_Primary cancer_'n);
      when ('Bile Ducts') _xrow_36_0_[2] = _temp_;
      when ('Breast') _xrow_36_0_[3] = _temp_;
      when ('Cervical') _xrow_36_0_[4] = _temp_;
      when ('Colon') _xrow_36_0_[5] = _temp_;
      when ('Lung') _xrow_36_0_[6] = _temp_;
      when ('Neuro') _xrow_36_0_[7] = _temp_;
      when ('Prostate') _xrow_36_0_[8] = _temp_;
      when ('Renal') _xrow_36_0_[9] = _temp_;
      when ('Skeletal') _xrow_36_0_[10] = _temp_;
      when ('Skin') _xrow_36_0_[11] = _temp_;
      when ('Soft Tissue Sarcoma') _xrow_36_0_[12] = _temp_;
      when ('Urothelial') _xrow_36_0_[13] = _temp_;
      when ('Uterus') _xrow_36_0_[14] = _temp_;
      otherwise do; _badval_ = 1; goto skip_36_0; end;
   end;

   _xrow_36_0_[15] = 'Age (Y)'n;

   _xrow_36_0_[16] = 'BMI (kg/m^2)'n;

   _xrow_36_0_[17] = 'Height (m)'n;

   _xrow_36_0_[18] = 'Weight (kg)'n;

   do _i_=1 to 18;
      _linp_ + _xrow_36_0_{_i_} * _beta_36_0_{_i_};
   end;

   skip_36_0:
   length I_va__d__E_Case $12;
   label I_va__d__E_Case = 'Into: va__d__E_Case';
   array _levels_36_{2} $ 12 _TEMPORARY_ ('1'
   ,'0'
   );
   label P_va__d__E_Case1 = 'Predicted: va__d__E_Case=1';
   if (_badval_ eq 0) and not missing(_linp_) then do;
      if (_linp_ > 0) then do;
         P_va__d__E_Case1 = 1 / (1+exp(-_linp_));
      end; else do;
         P_va__d__E_Case1 = exp(_linp_) / (1+exp(_linp_));
      end;
      P_va__d__E_Case0 = 1 - P_va__d__E_Case1;
      if P_va__d__E_Case1 >= 0.5                  then do;
         I_va__d__E_Case = _levels_36_{1};
      end; else do;
         I_va__d__E_Case = _levels_36_{2};
      end;
   end; else do;
      _linp_ = .;
      P_va__d__E_Case1 = .;
      P_va__d__E_Case0 = .;
      I_va__d__E_Case = ' ';
   end;
   /*------------------------------------------*/
   /*_VA_DROP*/ drop 'va__d__E_Case'n 'I_va__d__E_Case'n 'P_va__d__E_Case1'n 'P_va__d__E_Case0'n;
length 'I_va__d__E_Case_36'n $32;
      'I_va__d__E_Case_36'n='I_va__d__E_Case'n;
'P_va__d__E_Case1_36'n='P_va__d__E_Case1'n;
'P_va__d__E_Case0_36'n='P_va__d__E_Case0'n;
   /*------------------------------------------*/
   

