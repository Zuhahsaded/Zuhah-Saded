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
   /*---------------------------------------------------------
  The options statement below should be placed
  before the data step when submitting this code.
---------------------------------------------------------*/
options VALIDMEMNAME=EXTEND VALIDVARNAME=ANY;
   /*------------------------------------------
   Generated SAS Scoring Code
     Date             : December 16, 2024, 03:02:54 AM
     Locale           : en_US
     Model Type       : Neural Network
     Interval variable: Age (Y)
     Interval variable: Height (m)
     Interval variable: Weight (kg)
     Class variable   : Primary cancer
     Response variable: Primary cancer
     ------------------------------------------*/
   /*---------------------------------------------------------

   SAS Code Generated by Cloud Analytic Services for Artificial Neural Network

     Date                  : 16Dec2024:03:02:53 UTC
     Response variable      : Primary cancer
     Number of nodes        : 26
     Number of input nodes  : 3

     Number of output nodes : 13
     Number of hidden nodes : 10
     Number of hidden layers: 1
     Type of neural nets    : MLP

     ---------------------------------------------------------*/

   length _strfmt_ $19; drop _strfmt_;
   _strfmt_ = ' ';

   array _tlevname_2582_{13} $19 _temporary_ ( 'Prostate' 
   'Colon' 
   'Skin' 
   'Renal' 
   'Breast' 
   'Lung' 
   'Neuro' 

   'Cervical' 
   'Bile Ducts' 
   'Uterus' 
   'Soft Tissue Sarcoma' 
   'Urothelial' 
   'Skeletal');

   length I_Primary_cancer $19;

   array _node_val_2582_{26} _temporary_; 

   _badval_ = 0;
   _dropinput_ =                    1;
   _drop_ =                    1;

   /* set input node values */


   _numval_ = 'Age (Y)'n;
   if missing(_numval_) then do;
      _badval_ = 1; goto skip_2582; 
   end;
   _tval_ =                   49;

   _sumval_ =                   33;
   _numval_ = 2.0*(_numval_-_sumval_)/_tval_ - 1.0;
   _node_val_2582_{1} = _numval_*_dropinput_;
   _numval_ = 'Height (m)'n;

   if missing(_numval_) then do;
      _badval_ = 1; goto skip_2582; 
   end;
   _tval_ =     0.49299999999999;
   _sumval_ =                1.445;

   _numval_ = 2.0*(_numval_-_sumval_)/_tval_ - 1.0;
   _node_val_2582_{2} = _numval_*_dropinput_;
   _numval_ = 'Weight (kg)'n;

   if missing(_numval_) then do;
      _badval_ = 1; goto skip_2582; 
   end;
   _tval_ =                 64.5;
   _sumval_ =                 42.7;

   _numval_ = 2.0*(_numval_-_sumval_)/_tval_ - 1.0;
   _node_val_2582_{3} = _numval_*_dropinput_;


   /* Forward Propagation of Net 0 */

   _sumval_ = 0.0;


   /* Combination for Node 3 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =    -0.54827640638407;
   _nval_ = _node_val_2582_{1};

   _tval_ = _nval_ *      1.1453228836078;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{2};

   _tval_ = _nval_ *      1.4615255837343;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *    -3.70399899040169;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 3 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{4} = _numval_*_drop_;

   /* Combination for Node 4 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =    -0.97105514133532;
   _nval_ = _node_val_2582_{1};
   _tval_ = _nval_ *     4.06155023705791;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{2};
   _tval_ = _nval_ *    -3.06085298101244;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *    -1.59589312294698;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 4 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{5} = _numval_*_drop_;

   /* Combination for Node 5 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =     3.65119040287282;
   _nval_ = _node_val_2582_{1};
   _tval_ = _nval_ *    -3.84271023444757;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{2};
   _tval_ = _nval_ *    -1.00175693907162;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *     3.39309044514159;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 5 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{6} = _numval_*_drop_;

   /* Combination for Node 6 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =     1.48889427741908;
   _nval_ = _node_val_2582_{1};
   _tval_ = _nval_ *    -2.85220471021174;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{2};
   _tval_ = _nval_ *     0.70286586000754;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *    -5.13544927586011;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 6 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{7} = _numval_*_drop_;

   /* Combination for Node 7 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =    -2.11734806557493;
   _nval_ = _node_val_2582_{1};
   _tval_ = _nval_ *     3.29044728661583;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{2};
   _tval_ = _nval_ *    -2.88015816161917;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *     2.41863041325117;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 7 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{8} = _numval_*_drop_;

   /* Combination for Node 8 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =    -2.26801468832261;
   _nval_ = _node_val_2582_{1};
   _tval_ = _nval_ *    -1.77568186742562;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{2};
   _tval_ = _nval_ *    -2.24737315089962;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *    -3.64876183474892;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 8 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{9} = _numval_*_drop_;

   /* Combination for Node 9 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =    -0.30364025694997;
   _nval_ = _node_val_2582_{1};
   _tval_ = _nval_ *    -2.45795543427189;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{2};
   _tval_ = _nval_ *    -2.99175778757989;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *    -2.12235128348787;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 9 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{10} = _numval_*_drop_;

   /* Combination for Node 10 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =     1.05809076490962;
   _nval_ = _node_val_2582_{1};
   _tval_ = _nval_ *    -2.58894439774339;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{2};
   _tval_ = _nval_ *     2.00485353184796;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *     5.60887184268976;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 10 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{11} = _numval_*_drop_;

   /* Combination for Node 11 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =    -1.04624934049456;
   _nval_ = _node_val_2582_{1};
   _tval_ = _nval_ *    -3.64519914947803;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{2};
   _tval_ = _nval_ *     2.47854278145099;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *     2.15432394276219;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 11 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{12} = _numval_*_drop_;

   /* Combination for Node 12 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =      1.2997116856718;
   _nval_ = _node_val_2582_{1};
   _tval_ = _nval_ *     3.49813353639867;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{2};
   _tval_ = _nval_ *     1.92416438340214;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{3};

   _tval_ = _nval_ *    -2.23491560473403;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 12 */

   _tval_ = 2.0*_numval_;

   if (_tval_ gt     704.782712893384) then do;
      _numval_ = 1.0;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   else do;
      _tval_ = exp(_tval_);

      _numval_ = 1.0-2.0/(1.0+_tval_);
   end;
   _node_val_2582_{13} = _numval_*_drop_;

   /* Combination for Node 13 */

   _numval_ = 0.0;
   _tval_   = 0.0;

   _bias_   =     2.64170574532817;
   _nval_ = _node_val_2582_{4};
   _tval_ = _nval_ *     -0.0651207136519;
   _numval_ + _tval_;

   _nval_ = _node_val_2582_{5};
   _tval_ = _nval_ *     1.46491386695954;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *    -4.02728022455989;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *     1.58558159636373;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *    -0.45451906503741;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *     -1.7645466094239;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *     -1.5105187692286;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *     4.67213077626795;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *     0.96253926634088;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *     2.63389234653849;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 13 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{14} = _numval_;


   /* Combination for Node 14 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =    -2.30666096100149;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *     1.54847509999341;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *    -1.46925380599972;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *     2.47001255187683;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *     0.96957353028108;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *     2.15518880946823;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *    -1.80229549567868;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *     2.60806914395492;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *    -1.70741396219768;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *     -0.0252096336014;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *     0.90144743217396;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 14 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{15} = _numval_;


   /* Combination for Node 15 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =     1.36184727839509;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *     0.46800606380537;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *     1.63184149281827;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *     0.80377389503258;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *    -1.39047824342551;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *    -1.80836011779153;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *     -0.5888063672853;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *    -1.63056290589374;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *    -0.52461904072901;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *     0.60172258357425;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *    -2.62189111942573;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 15 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{16} = _numval_;


   /* Combination for Node 16 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =     3.45575643400148;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *    -0.19546316971738;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *    -3.22255135522879;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *    -1.43859336144394;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *    -2.66752283269596;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *    -0.67130081948946;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *     2.85935864199355;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *    -1.73988069476201;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *    -2.06293988750224;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *    -3.80780400522621;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *    -0.09341969169891;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 16 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{17} = _numval_;


   /* Combination for Node 17 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =     4.07815526413102;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *    -2.84057106830222;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *    -1.15584652184592;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *      1.1250950211755;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *    -0.54536272962969;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *     2.70053928199618;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *     1.47759740366965;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *     2.21330950131766;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *    -1.38123241458162;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *     1.42546863665549;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *    -1.41062063841761;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 17 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{18} = _numval_;


   /* Combination for Node 18 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =     3.05731033149334;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *      0.3597998186289;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *    -2.42017804975003;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *     0.53932791501045;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *     0.18574059765999;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *     3.16204658698238;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *     3.49018407819602;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *     2.29310232747919;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *     2.16409936599896;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *    -0.84460528968636;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *     2.85399344531293;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 18 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{19} = _numval_;


   /* Combination for Node 19 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =    -0.83998772950405;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *    -1.35534629496961;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *     0.99245654527735;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *     0.25981237741416;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *     0.43106878218689;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *    -0.14145953358548;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *    -1.23009786234132;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *     1.24706607671665;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *     1.43116523347722;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *     -1.2037986896378;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *    -2.24742372490912;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 19 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{20} = _numval_;


   /* Combination for Node 20 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =     -1.8584002003454;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *     0.01899037194839;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *     1.53623945209824;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *     2.11001114546582;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *     0.26610507576377;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *    -0.53983968346707;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *     1.53866161795741;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *     0.92990591150607;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *    -0.40774944627469;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *    -0.09376879930047;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *     0.35482585871128;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 20 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{21} = _numval_;


   /* Combination for Node 21 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =    -1.62879354896909;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *    -0.84846882734051;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *    -0.60610474746846;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *     0.09860688806794;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *    -1.33492311034529;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *    -2.06256386524822;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *    -0.09870323767074;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *    -0.40545856462905;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *     0.35456087011725;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *     1.13238950099477;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *     0.65615691704911;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 21 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{22} = _numval_;


   /* Combination for Node 22 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =    -1.72372645037288;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *      1.9863944628096;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *     0.46810899025253;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *    -2.70630170388635;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *    -1.72487107488375;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *     0.70322802291278;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *    -0.75416363014085;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *    -2.02026503077394;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *    -0.76431727076608;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *    -0.37043882514675;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *     0.38646820730443;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 22 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{23} = _numval_;


   /* Combination for Node 23 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =    -0.79582076136443;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *     -0.6206660064847;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *    -0.40944630048108;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *     0.06211602001804;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *     2.13613109386807;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *    -0.36896695365816;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *    -1.02810623170043;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *    -0.74140868646478;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *     0.61292105039693;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *     2.02961152416238;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *    -1.39729069303715;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 23 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{24} = _numval_;


   /* Combination for Node 24 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =    -2.70689574972924;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *     0.96948107299276;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *     1.56642491309926;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *     0.02530864585654;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *     0.81612518923889;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *    -1.85294251975181;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *    -1.36847884755827;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *     0.95918416121563;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *     -0.9653169242164;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *    -0.00875685861778;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *     0.06024815142674;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 24 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{25} = _numval_;


   /* Combination for Node 25 */

   _numval_ = 0.0;
   _tval_   = 0.0;
   _bias_   =    -2.73448965206251;
   _nval_ = _node_val_2582_{4};

   _tval_ = _nval_ *     0.55215284787071;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{5};

   _tval_ = _nval_ *     1.66050725969779;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{6};

   _tval_ = _nval_ *     0.70158229376501;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{7};

   _tval_ = _nval_ *     1.28829685454297;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{8};

   _tval_ = _nval_ *    -0.88160413685958;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{9};

   _tval_ = _nval_ *    -0.81421479084608;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{10};

   _tval_ = _nval_ *    -2.27215673430864;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{11};

   _tval_ = _nval_ *    -1.44196855764375;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{12};

   _tval_ = _nval_ *     0.16424722852932;
   _numval_ + _tval_;
   _nval_ = _node_val_2582_{13};

   _tval_ = _nval_ *    -0.23640036685896;
   _numval_ + _tval_;
   _numval_ + _bias_;

   /* Activation for Node 25 */

   _tval_ = _numval_;

   if (_tval_ ge     704.782712893384) then do;
      _tval_ =     704.782712893384;
   end;

   else if (_tval_ lt         -708.3964185) then do;
      _tval_ = 0.0;
   end;
   else do;
      _tval_ = exp(_tval_);
   end;
   _numval_ = _tval_;
   _sumval_ + _numval_;
   _node_val_2582_{26} = _numval_;
   _numval_ = _node_val_2582_{14};

   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{14} = _numval_;
   _numval_ = _node_val_2582_{15};
   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{15} = _numval_;
   _numval_ = _node_val_2582_{16};

   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{16} = _numval_;
   _numval_ = _node_val_2582_{17};
   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{17} = _numval_;
   _numval_ = _node_val_2582_{18};

   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{18} = _numval_;
   _numval_ = _node_val_2582_{19};
   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{19} = _numval_;
   _numval_ = _node_val_2582_{20};

   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{20} = _numval_;
   _numval_ = _node_val_2582_{21};
   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{21} = _numval_;
   _numval_ = _node_val_2582_{22};

   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{22} = _numval_;
   _numval_ = _node_val_2582_{23};
   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{23} = _numval_;
   _numval_ = _node_val_2582_{24};

   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{24} = _numval_;
   _numval_ = _node_val_2582_{25};
   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{25} = _numval_;
   _numval_ = _node_val_2582_{26};

   _numval_ = _numval_ / _sumval_;
   _node_val_2582_{26} = _numval_;
   skip_2582:
   if (_badval_ eq 1) then do;
      P_Primary_cancerProstate = .;

      P_Primary_cancerColon = .;
      P_Primary_cancerSkin = .;
      P_Primary_cancerRenal = .;
      P_Primary_cancerBreast = .;

      P_Primary_cancerLung = .;
      P_Primary_cancerNeuro = .;
      P_Primary_cancerCervical = .;
      P_Primary_cancerBile_Ducts = .;

      P_Primary_cancerUterus = .;
      P_Primary_cancerSoft_Tissue_Sarc = .;
      P_Primary_cancerUrothelial = .;

      P_Primary_cancerSkeletal = .;
      I_Primary_cancer = ' ';
      _NN_PredP = .  ;
   end;
   else do;
      _nn_pred_lev_ = -1;
      _NN_PredP = 0.0;

      _numval_ = _node_val_2582_{14};
      P_Primary_cancerProstate = _node_val_2582_{14};

      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;
         _nn_pred_lev_ = 1;
      end;

      _numval_ = _node_val_2582_{15};
      P_Primary_cancerColon = _node_val_2582_{15};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;

         _nn_pred_lev_ = 2;
      end;
      _numval_ = _node_val_2582_{16};

      P_Primary_cancerSkin = _node_val_2582_{16};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;
         _nn_pred_lev_ = 3;
      end;

      _numval_ = _node_val_2582_{17};
      P_Primary_cancerRenal = _node_val_2582_{17};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;

         _nn_pred_lev_ = 4;
      end;
      _numval_ = _node_val_2582_{18};

      P_Primary_cancerBreast = _node_val_2582_{18};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;
         _nn_pred_lev_ = 5;
      end;

      _numval_ = _node_val_2582_{19};
      P_Primary_cancerLung = _node_val_2582_{19};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;

         _nn_pred_lev_ = 6;
      end;
      _numval_ = _node_val_2582_{20};

      P_Primary_cancerNeuro = _node_val_2582_{20};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;
         _nn_pred_lev_ = 7;
      end;

      _numval_ = _node_val_2582_{21};
      P_Primary_cancerCervical = _node_val_2582_{21};

      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;
         _nn_pred_lev_ = 8;
      end;

      _numval_ = _node_val_2582_{22};

      P_Primary_cancerBile_Ducts = _node_val_2582_{22};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;
         _nn_pred_lev_ = 9;
      end;

      _numval_ = _node_val_2582_{23};
      P_Primary_cancerUterus = _node_val_2582_{23};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;

         _nn_pred_lev_ = 10;
      end;
      _numval_ = _node_val_2582_{24};

      P_Primary_cancerSoft_Tissue_Sarc = _node_val_2582_{24};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;
         _nn_pred_lev_ = 11;
      end;

      _numval_ = _node_val_2582_{25};

      P_Primary_cancerUrothelial = _node_val_2582_{25};
      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;
         _nn_pred_lev_ = 12;
      end;

      _numval_ = _node_val_2582_{26};
      P_Primary_cancerSkeletal = _node_val_2582_{26};

      if (_numval_ gt _NN_PredP) then do;
         _NN_PredP = _numval_;
         _nn_pred_lev_ = 13;
      end;

      I_Primary_cancer = _tlevname_2582_{_nn_pred_lev_};
   end;

   label I_Primary_cancer = 'Into: Primary cancer';

   label P_Primary_cancerProstate = 'Predicted: Primary cancer=Prostate           ';

   label P_Primary_cancerColon = 'Predicted: Primary cancer=Colon              ';

   label P_Primary_cancerSkin = 'Predicted: Primary cancer=Skin               ';

   label P_Primary_cancerRenal = 'Predicted: Primary cancer=Renal              ';

   label P_Primary_cancerBreast = 'Predicted: Primary cancer=Breast             ';

   label P_Primary_cancerLung = 'Predicted: Primary cancer=Lung               ';

   label P_Primary_cancerNeuro = 'Predicted: Primary cancer=Neuro              ';

   label P_Primary_cancerCervical = 'Predicted: Primary cancer=Cervical           ';

   label P_Primary_cancerBile_Ducts = 'Predicted: Primary cancer=Bile Ducts         ';

   label P_Primary_cancerUterus = 'Predicted: Primary cancer=Uterus             ';

   label P_Primary_cancerSoft_Tissue_Sarc = 'Predicted: Primary cancer=Soft Tissue Sarcoma';

   label P_Primary_cancerUrothelial = 'Predicted: Primary cancer=Urothelial         ';

   label P_Primary_cancerSkeletal = 'Predicted: Primary cancer=Skeletal           ';

   drop _numval_;
   drop _sumval_;
   drop _bias_;
   drop _tval_;
   drop _nval_;
   drop _badval_;
   drop _drop_;

   drop _dropinput_;
   drop _nn_pred_lev_;
   drop _NN_PredP;
   /*------------------------------------------*/
   /*_VA_DROP*/ drop 'I_Primary_cancer'n 'P_Primary_cancerBile_Ducts'n 'P_Primary_cancerBreast'n 'P_Primary_cancerCervical'n 'P_Primary_cancerColon'n 'P_Primary_cancerLung'n 'P_Primary_cancerNeuro'n 'P_Primary_cancerProstate'n 'P_Primary_cancerRenal'n 'P_Primary_cancerSkeletal'n 'P_Primary_cancerSkin'n 'P_Primary_cancerSoft_Tissue_Sarc'n 'P_Primary_cancerUrothelial'n 'P_Primary_cancerUterus'n;
length 'I_Primary_cancer_2582'n $19;
      'I_Primary_cancer_2582'n='I_Primary_cancer'n;
'P_Primary_cancerBile_Duct_2582'n='P_Primary_cancerBile_Ducts'n;
'P_Primary_cancerBreast_2582'n='P_Primary_cancerBreast'n;
'P_Primary_cancerCervical_2582'n='P_Primary_cancerCervical'n;
'P_Primary_cancerColon_2582'n='P_Primary_cancerColon'n;
'P_Primary_cancerLung_2582'n='P_Primary_cancerLung'n;
'P_Primary_cancerNeuro_2582'n='P_Primary_cancerNeuro'n;
'P_Primary_cancerProstate_2582'n='P_Primary_cancerProstate'n;
'P_Primary_cancerRenal_2582'n='P_Primary_cancerRenal'n;
'P_Primary_cancerSkeletal_2582'n='P_Primary_cancerSkeletal'n;
'P_Primary_cancerSkin_2582'n='P_Primary_cancerSkin'n;
'P_Primary_cancerSoft_Tiss_2582'n='P_Primary_cancerSoft_Tissue_Sarc'n;
'P_Primary_cancerUrothelia_2582'n='P_Primary_cancerUrothelial'n;
'P_Primary_cancerUterus_2582'n='P_Primary_cancerUterus'n;
   /*------------------------------------------*/

/*---------------------------------------------------------
  The options statement below should be placed
  before the data step when submitting this code.
---------------------------------------------------------*/
options VALIDMEMNAME=EXTEND VALIDVARNAME=ANY;
   /*------------------------------------------
   Generated SAS Scoring Code
     Date             : December 16, 2024, 02:48:21 AM
     Locale           : en_US
     Model Type       : Linear Regression
     Interval variable: Age (Y)
     Interval variable: BMI (kg/m^2)
     Interval variable: Height (m)
     Interval variable: Weight (kg)
     Response variable: Age (Y)
     ------------------------------------------*/
   /*---------------------------------------------------------
     Generated SAS Scoring Code
     Date: 16Dec2024:02:48:20
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

   array _xrow_854_0_{4} _temporary_;
   array _beta_854_0_{4} _temporary_ (   -219.296087338211
           5.00252576081424
           169.280263422583
          -1.76929250186259);

   /*------------------------------------------*/
   /*Missing values in model variables result  */
   /*in missing values for the prediction.     */
   if missing('BMI (kg/m^2)'n) 
      or missing('Weight (kg)'n) 
      or missing('Height (m)'n) 
      then do;
         _badval_ = 1;
         goto skip_854_0;
   end;
   /*------------------------------------------*/

   do _i_=1 to 4; _xrow_854_0_{_i_} = 0; end;

   _xrow_854_0_[1] = 1;

   _xrow_854_0_[2] = 'BMI (kg/m^2)'n;

   _xrow_854_0_[3] = 'Height (m)'n;

   _xrow_854_0_[4] = 'Weight (kg)'n;

   do _i_=1 to 4;
      _linp_ + _xrow_854_0_{_i_} * _beta_854_0_{_i_};
   end;

   skip_854_0:
   label P_Age__Y_ = 'Predicted: Age (Y)';
   if (_badval_ eq 0) and not missing(_linp_) then do;
      P_Age__Y_ = _linp_;
   end; else do;
      _linp_ = .;
      P_Age__Y_ = .;
   end;
   /*------------------------------------------*/
   /*_VA_DROP*/ drop 'P_Age__Y_'n;
      'P_Age__Y__854'n='P_Age__Y_'n;
   /*------------------------------------------*/
