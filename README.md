 library()
> library(dplyr)

Attaching package: ‘dplyr’

The following objects are masked from ‘package:stats’:

    filter, lag

The following objects are masked from ‘package:base’:

    intersect, setdiff, setequal, union

> fileurl<-"https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
> download.file(fileurl,destfile = "cleaningdataweek4.zip", method="curl")
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 59.6M  100 59.6M    0     0  2545k      0  0:00:24  0:00:24 --:--:-- 3285k
> 
> unzip(cleaningdataweek4.zip)
Error in unzip(cleaningdataweek4.zip) : 
  object 'cleaningdataweek4.zip' not found
> unzip("cleaningdataweek4.zip")
> list.files("F:/RWork/Cleaning Data Week 4/UCI HAR Dataset")
[1] "activity_labels.txt" "features.txt"        "features_info.txt"  
[4] "README.txt"          "test"                "train"              
> 

pathdata = file.path("F:/RWork/Cleaning Data Week 4", "UCI HAR Dataset")
> files=list.files(pathdata,recursive = TRUE)
> files
 [1] "activity_labels.txt"                         
 [2] "features.txt"                                
 [3] "features_info.txt"                           
 [4] "README.txt"                                  
 [5] "test/Inertial Signals/body_acc_x_test.txt"   
 [6] "test/Inertial Signals/body_acc_y_test.txt"   
 [7] "test/Inertial Signals/body_acc_z_test.txt"   
 [8] "test/Inertial Signals/body_gyro_x_test.txt"  
 [9] "test/Inertial Signals/body_gyro_y_test.txt"  
[10] "test/Inertial Signals/body_gyro_z_test.txt"  
[11] "test/Inertial Signals/total_acc_x_test.txt"  
[12] "test/Inertial Signals/total_acc_y_test.txt"  
[13] "test/Inertial Signals/total_acc_z_test.txt"  
[14] "test/subject_test.txt"                       
[15] "test/X_test.txt"                             
[16] "test/y_test.txt"                             
[17] "train/Inertial Signals/body_acc_x_train.txt" 
[18] "train/Inertial Signals/body_acc_y_train.txt" 
[19] "train/Inertial Signals/body_acc_z_train.txt" 
[20] "train/Inertial Signals/body_gyro_x_train.txt"
[21] "train/Inertial Signals/body_gyro_y_train.txt"
[22] "train/Inertial Signals/body_gyro_z_train.txt"
[23] "train/Inertial Signals/total_acc_x_train.txt"
[24] "train/Inertial Signals/total_acc_y_train.txt"
[25] "train/Inertial Signals/total_acc_z_train.txt"
[26] "train/subject_train.txt"                     
[27] "train/X_train.txt"                           
[28] "train/y_train.txt"                           
> files=list.files(pathdata)
> files
[1] "activity_labels.txt" "features.txt"        "features_info.txt"  
[4] "README.txt"          "test"                "train"              
> files=list.files(pathdata,recursive=TRUE)
> files
 [1] "activity_labels.txt"                         
 [2] "features.txt"                                
 [3] "features_info.txt"                           
 [4] "README.txt"                                  
 [5] "test/Inertial Signals/body_acc_x_test.txt"   
 [6] "test/Inertial Signals/body_acc_y_test.txt"   
 [7] "test/Inertial Signals/body_acc_z_test.txt"   
 [8] "test/Inertial Signals/body_gyro_x_test.txt"  
 [9] "test/Inertial Signals/body_gyro_y_test.txt"  
[10] "test/Inertial Signals/body_gyro_z_test.txt"  
[11] "test/Inertial Signals/total_acc_x_test.txt"  
[12] "test/Inertial Signals/total_acc_y_test.txt"  
[13] "test/Inertial Signals/total_acc_z_test.txt"  
[14] "test/subject_test.txt"                       
[15] "test/X_test.txt"                             
[16] "test/y_test.txt"                             
[17] "train/Inertial Signals/body_acc_x_train.txt" 
[18] "train/Inertial Signals/body_acc_y_train.txt" 
[19] "train/Inertial Signals/body_acc_z_train.txt" 
[20] "train/Inertial Signals/body_gyro_x_train.txt"
[21] "train/Inertial Signals/body_gyro_y_train.txt"
[22] "train/Inertial Signals/body_gyro_z_train.txt"
[23] "train/Inertial Signals/total_acc_x_train.txt"
[24] "train/Inertial Signals/total_acc_y_train.txt"
[25] "train/Inertial Signals/total_acc_z_train.txt"
[26] "train/subject_train.txt"                     
[27] "train/X_train.txt"                           
[28] "train/y_train.txt"                           

xtrain = read.table(file.path(pathdata, "train", "X_train.txt"),header = FALSE)
> xtrain
         V1          V2         V3         V4         V5         V6
1 0.2885845 -0.02029417 -0.1329051 -0.9952786 -0.9831106 -0.9135264
          V7         V8        V9        V10        V11        V12
1 -0.9951121 -0.9831846 -0.923527 -0.9347238 -0.5673781 -0.7444125
        V13       V14       V15        V16        V17       V18        V19
1 0.8529474 0.6858446 0.8142628 -0.9655228 -0.9999446 -0.999863 -0.9946122
         V20        V21      V22        V23        V24        V25       V26
1 -0.9942308 -0.9876139 -0.94322 -0.4077471 -0.6793375 -0.6021219 0.9292935
         V27       V28         V29       V30        V31       V32
1 -0.8530111 0.3599098 -0.05852638 0.2568915 -0.2248476 0.2641057
          V33       V34        V35      V36        V37       V38       V39
1 -0.09524563 0.2788514 -0.4650846 0.491936 -0.1908836 0.3763139 0.4351292
        V40       V41        V42       V43        V44        V45       V46
1 0.6607903 0.9633961 -0.1408397 0.1153749 -0.9852497 -0.9817084 -0.877625
         V47        V48        V49       V50        V51       V52       V53
1 -0.9850014 -0.9844162 -0.8946774 0.8920545 -0.1612655 0.1246598 0.9774363
         V54        V55       V56       V57        V58        V59
1 -0.1232134 0.05648273 -0.375426 0.8994686 -0.9709052 -0.9755104
         V60        V61        V62 V63 V64       V65       V66       V67
1 -0.9843254 -0.9888491 -0.9177426  -1  -1 0.1138061 -0.590425 0.5911463
         V68       V69        V70       V71        V72    V73        V74
1 -0.5917735 0.5924693 -0.7454488 0.7208617 -0.7123724 0.7113 -0.9951116
        V75        V76       V77       V78       V79       V80        V81
1 0.9956749 -0.9956676 0.9916527 0.5702216 0.4390273 0.9869131 0.07799634
          V82         V83        V84      V85       V86        V87
1 0.005000803 -0.06783081 -0.9935191 -0.98836 -0.993575 -0.9944876
         V88        V89        V90        V91        V92       V93
1 -0.9862066 -0.9928183 -0.9851801 -0.9919942 -0.9931189 0.9898347
        V94       V95       V96        V97        V98        V99      V100
1 0.9919569 0.9905192 -0.993522 -0.9999349 -0.9998204 -0.9998785 -0.994364
        V101       V102       V103       V104       V105 V106      V107
1 -0.9860249 -0.9892336 -0.8199492 -0.7930464 -0.8888529    1 -0.220747
       V108      V109      V110        V111      V112      V113      V114
1 0.6368308 0.3876436 0.2414015 -0.05225285 0.2641772 0.3734395 0.3417775
        V115      V116       V117       V118       V119       V120
1 -0.5697912 0.2653988 -0.4778749 -0.3853005 0.03364394 -0.1265108
          V121        V122      V123       V124       V125       V126
1 -0.006100849 -0.03136479 0.1077254 -0.9853103 -0.9766234 -0.9922053
        V127       V128       V129       V130      V131       V132     V133
1 -0.9845863 -0.9763526 -0.9923616 -0.8670437 -0.933786 -0.7475662 0.847308
       V134      V135       V136       V137       V138       V139
1 0.9148953 0.8308405 -0.9671843 -0.9995783 -0.9993543 -0.9997634
        V140      V141       V142       V143      V144       V145
1 -0.9834381 -0.978614 -0.9929656 0.08263168 0.2022676 -0.1687567
        V146       V147      V148       V149 V150       V151      V152
1 0.09632324 -0.2749851 0.4986442 -0.2203169    1 -0.9729714 0.3166545
       V153      V154      V155      V156      V157      V158      V159
1 0.3757264 0.7233992 -0.771112 0.6902132 -0.331831 0.7095838 0.1348734
       V160       V161        V162       V163       V164       V165
1 0.3010995 -0.0991674 -0.05551737 -0.0619858 -0.9921107 -0.9925193
        V166       V167       V168      V169       V170       V171
1 -0.9920553 -0.9921648 -0.9949416 -0.992619 -0.9901558 -0.9867428
        V172      V173      V174      V175       V176       V177       V178
1 -0.9920416 0.9944288 0.9917558 0.9893519 -0.9944534 -0.9999375 -0.9999535
        V179       V180       V181      V182      V183      V184       V185
1 -0.9999229 -0.9922997 -0.9969389 -0.992243 -0.589851 -0.688459 -0.5721069
       V186      V187      V188        V189      V190       V191      V192
1 0.2923763 -0.361998 0.4055427 -0.03900695 0.9892838 -0.4145605 0.3916025
       V193      V194     V195      V196      V197      V198        V199
1 0.2822509 0.9272698 -0.57237 0.6916192 0.4682898 -0.131077 -0.08715969
       V200       V201       V202       V203       V204       V205
1 0.3362475 -0.9594339 -0.9505515 -0.9579929 -0.9463052 -0.9925557
        V206       V207       V208       V209       V210        V211
1 -0.9594339 -0.9984928 -0.9576374 -0.2325816 -0.1731787 -0.02289666
        V212      V213       V214       V215       V216       V217
1 0.09483157 0.1918171 -0.9594339 -0.9505515 -0.9579929 -0.9463052
        V218       V219       V220       V221       V222       V223
1 -0.9925557 -0.9594339 -0.9984928 -0.9576374 -0.2325816 -0.1731787
         V224       V225      V226       V227       V228       V229
1 -0.02289666 0.09483157 0.1918171 -0.9933059 -0.9943364 -0.9945004
       V230       V231       V232       V233       V234       V235
1 -0.992784 -0.9912085 -0.9933059 -0.9998919 -0.9929337 -0.8634148
       V236       V237       V238        V239       V240       V241
1 0.2830852 -0.2373087 -0.1054322 -0.03821231 -0.9689591 -0.9643352
        V242       V243       V244       V245       V246       V247
1 -0.9572448 -0.9750599 -0.9915537 -0.9689591 -0.9992865 -0.9497658
        V248      V249       V250      V251     V252       V253       V254
1 0.07257904 0.5725114 -0.7386022 0.2125778 0.433405 -0.9942478 -0.9913676
       V255       V256      V257       V258      V259       V260       V261
1 -0.993143 -0.9889356 -0.993486 -0.9942478 -0.999949 -0.9945472 -0.6197676
       V262       V263       V264       V265       V266       V267
1 0.2928405 -0.1768892 -0.1457792 -0.1240723 -0.9947832 -0.9829841
        V268       V269      V270      V271       V272       V273      V274
1 -0.9392687 -0.9954217 -0.983133 -0.906165 -0.9968886 -0.9845193 -0.932082
        V275       V276       V277       V278       V279       V280
1 -0.9937563 -0.9831629 -0.8850542 -0.9939619 -0.9934461 -0.9234277
        V281       V282       V283       V284      V285       V286
1 -0.9747327 -0.9999684 -0.9996891 -0.9948915 -0.995926 -0.9897089
        V287       V288       V289       V290 V291 V292 V293      V294
1 -0.9879912 -0.9463569 -0.9047478 -0.5913025   -1   -1   -1 0.2524829
       V295        V296      V297       V298       V299       V300
1 0.1318358 -0.05205025 0.1420506 -0.1506825 -0.2205469 -0.5587385
       V301         V302       V303       V304       V305       V306
1 0.2467687 -0.007415521 -0.9999628 -0.9999865 -0.9999791 -0.9999624
        V307       V308       V309       V310       V311       V312
1 -0.9999322 -0.9997251 -0.9996704 -0.9999858 -0.9999687 -0.9999769
        V313       V314       V315       V316       V317       V318
1 -0.9998697 -0.9997761 -0.9999712 -0.9999193 -0.9996568 -0.9998605
       V319      V320       V321       V322       V323       V324
1 -0.999867 -0.999863 -0.9997378 -0.9997322 -0.9994926 -0.9998136
        V325       V326       V327      V328       V329       V330
1 -0.9996818 -0.9998394 -0.9997382 -0.999612 -0.9996872 -0.9998386
        V331       V332      V333       V334       V335       V336
1 -0.9935923 -0.9994758 -0.999662 -0.9996423 -0.9992934 -0.9978922
        V337       V338       V339       V340       V341       V342
1 -0.9959325 -0.9951464 -0.9947399 -0.9996883 -0.9989246 -0.9956713
        V343       V344       V345       V346       V347       V348
1 -0.9948773 -0.9994544 -0.9923325 -0.9871699 -0.9896961 -0.9958207
        V349       V350       V351       V352       V353       V354
1 -0.9909363 -0.9970517 -0.9938055 -0.9905187 -0.9969928 -0.9967369
        V355       V356       V357       V358       V359      V360
1 -0.9919752 -0.9932417 -0.9983491 -0.9911084 -0.9598854 -0.990515
        V361       V362       V363       V364       V365       V366 V367
1 -0.9999347 -0.9998205 -0.9998845 -0.9930263 -0.9913734 -0.9962396   -1
  V368 V369 V370  V371 V372      V373     V374      V375       V376
1   -1   -1    1 -0.24   -1 0.8703845 0.210697 0.2637079 -0.7036858
        V377       V378       V379       V380       V381       V382
1 -0.9037425 -0.5825736 -0.9363101 -0.5073447 -0.8055359 -0.9999865
        V383       V384       V385       V386       V387       V388
1 -0.9999796 -0.9999748 -0.9999551 -0.9999186 -0.9996401 -0.9994833
        V389       V390       V391      V392       V393       V394
1 -0.9999609 -0.9999823 -0.9999707 -0.999811 -0.9994847 -0.9999808
        V395       V396       V397       V398       V399       V400
1 -0.9998519 -0.9999326 -0.9998999 -0.9998244 -0.9998598 -0.9997275
        V401       V402       V403       V404       V405       V406
1 -0.9997288 -0.9995671 -0.9997652 -0.9999002 -0.9998149 -0.9997098
        V407       V408       V409       V410       V411       V412
1 -0.9995961 -0.9998522 -0.9998221 -0.9993999 -0.9997656 -0.9999585
        V413       V414       V415       V416       V417       V418
1 -0.9999495 -0.9998385 -0.9998135 -0.9987805 -0.9985778 -0.9996197
        V419       V420       V421       V422       V423       V424
1 -0.9999836 -0.9998281 -0.9986807 -0.9998442 -0.9999279 -0.9865744
        V425       V426       V427       V428       V429       V430
1 -0.9817615 -0.9895148 -0.9850326 -0.9738861 -0.9940349 -0.9865308
        V431      V432       V433       V434       V435       V436
1 -0.9836164 -0.992352 -0.9804984 -0.9722709 -0.9949443 -0.9975686
        V437       V438       V439       V440       V441       V442
1 -0.9840851 -0.9943354 -0.9852762 -0.9998637 -0.9996661 -0.9999346
        V443       V444       V445       V446       V447      V448 V449
1 -0.9903439 -0.9948357 -0.9944116 -0.7124023 -0.6448424 -0.838993   -1
  V450 V451       V452       V453     V454      V455      V456     V457
1   -1   -1 -0.2575489 0.09794711 0.547151 0.3773112 0.1340915 0.273372
         V458       V459       V460      V461       V462       V463
1 -0.09126183 -0.4843465 -0.7828507 -0.999865 -0.9999318 -0.9999729
        V464       V465       V466      V467       V468       V469
1 -0.9999702 -0.9999301 -0.9999586 -0.999929 -0.9999847 -0.9998633
        V470       V471       V472       V473      V474       V475
1 -0.9999681 -0.9999361 -0.9999536 -0.9998644 -0.999961 -0.9994537
        V476       V477       V478       V479       V480      V481
1 -0.9999781 -0.9999915 -0.9999901 -0.9999686 -0.9998066 -0.998346
        V482       V483       V484       V485       V486       V487
1 -0.9989612 -0.9996187 -0.9999893 -0.9999354 -0.9983875 -0.9996426
        V488       V489       V490       V491       V492       V493
1 -0.9999727 -0.9999554 -0.9999763 -0.9999058 -0.9999855 -0.9999372
        V494       V495       V496       V497       V498       V499
1 -0.9997512 -0.9990723 -0.9999275 -0.9999516 -0.9999058 -0.9998927
        V500      V501       V502       V503      V504       V505
1 -0.9994443 -0.999941 -0.9999586 -0.9521547 -0.956134 -0.9488701
        V506       V507       V508       V509       V510       V511
1 -0.9743206 -0.9257218 -0.9521547 -0.9982852 -0.9732732 -0.6463764
        V512        V513      V514       V515       V516      V517
1 -0.7931035 -0.08843612 -0.436471 -0.7968405 -0.9937257 -0.993755
        V518       V519       V520       V521       V522       V523 V524
1 -0.9919757 -0.9933647 -0.9881754 -0.9937257 -0.9999184 -0.9913637   -1
        V525      V526       V527     V528       V529       V530       V531
1 -0.9365079 0.3469885 -0.5160801 -0.80276 -0.9801349 -0.9613094 -0.9736534
        V532       V533       V534       V535       V536       V537 V538
1 -0.9522638 -0.9894981 -0.9801349 -0.9992403 -0.9926555 -0.7012914   -1
        V539      V540      V541       V542       V543       V544
1 -0.1289889 0.5861564 0.3746046 -0.9919904 -0.9906975 -0.9899408
        V545       V546       V547       V548       V549       V550 V551
1 -0.9924478 -0.9910477 -0.9919904 -0.9999368 -0.9904579 -0.8713058   -1
         V552       V553       V554       V555       V556       V557
1 -0.07432303 -0.2986764 -0.7103041 -0.1127543 0.03040037 -0.4647614
         V558       V559      V560        V561
1 -0.01844588 -0.8412468 0.1799406 -0.05862692
 [ reached 'max' / getOption("max.print") -- omitted 7351 rows ]

ytrain = read.table(file.path(pathdata, "train", "y_train.txt"),header = FALSE)
subject_train = read.table(file.path(pathdata, "train", "subject_train.txt"),header = FALSE)
> xtest = read.table(file.path(pathdata, "test", "X_test.txt"),header = FALSE)
> ytest = read.table(file.path(pathdata, "test", "y_test.txt"),header = FALSE)
> subject_test = read.table(file.path(pathdata, "test", "subject_test.txt"),header = FALSE)
> features = read.table(file.path(pathdata, "features.txt"),header = FALSE)
> head(features)
  V1                V2
1  1 tBodyAcc-mean()-X
2  2 tBodyAcc-mean()-Y
3  3 tBodyAcc-mean()-Z
4  4  tBodyAcc-std()-X
5  5  tBodyAcc-std()-Y
6  6  tBodyAcc-std()-Z
> 
activityLabels = read.table(file.path(pathdata, "activity_labels.txt"),header = FALSE)
> colnames(xtrain) = features[,2]
> colnames(ytrain) = "activityId"
colnames(subject_train) = "subjectId"
> colnames(xtest) = features[,2]
 colnames(ytest) = "activityId"
> colnames(subject_test) = "subjectId"
colnames(activityLabels) <- c('activityId','activityType')
mrg_train = cbind(ytrain, subject_train, xtrain)
mrg_test = cbind(ytest, subject_test, xtest)
> final = rbind(mrg_train, mrg_test)
 colNames = colnames(final)
> mean_and_std = (grepl("activityId" , colNames) | grepl("subjectId" , colNames) | grepl("mean.." , colNames) | grepl("std.." , colNames))
> setForMeanAndStd <- final[ , mean_and_std == TRUE]
> View(setForMeanAndStd)
> setWithActivityNames = merge(setForMeanAndStd, activityLabels, by='activityId', all.x=TRUE)


XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

features <- read.table("UCI HAR Dataset/features.txt", col.names = c("n","functions"))
View(features)
> activities <- read.table("UCI HAR Dataset/activity_labels.txt", col.names = c("code", "activity"))
> View(activities)
> subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt", col.names = "subject")
> View(subject_test)
> x_test <- read.table("UCI HAR Dataset/test/X_test.txt", col.names = features$functions)
> View(x_test)
 y_test <- read.table("UCI HAR Dataset/test/y_test.txt", col.names = "code")
> subject_train <- read.table("UCI HAR Dataset/train/subject_train.txt", col.names = "subject")
> x_train <- read.table("UCI HAR Dataset/train/X_train.txt", col.names = features$functions)
> y_train <- read.table("UCI HAR Dataset/train/y_train.txt", col.names = "code")
> View(x_train)

X <- rbind(x_train, x_test)
> View(X)
> Y <- rbind(y_train, y_test)
> Subject <- rbind(subject_train, subject_test)
> Merged_Data <- cbind(Subject, Y, X)

TidyData <- Merged_Data %>% select(subject, code, contains("mean"), contains("std"))
TidyData$code <- activities[TidyData$code, 2]
names(TidyData)[2] = "activity"
> names(TidyData)<-gsub("Acc", "Accelerometer", names(TidyData))
> names(TidyData)<-gsub("Gyro", "Gyroscope", names(TidyData))
> names(TidyData)<-gsub("BodyBody", "Body", names(TidyData))
> names(TidyData)<-gsub("Mag", "Magnitude", names(TidyData))
> names(TidyData)<-gsub("^t", "Time", names(TidyData))
> names(TidyData)<-gsub("^f", "Frequency", names(TidyData))
 names(TidyData)<-gsub("tBody", "TimeBody", names(TidyData))
> names(TidyData)<-gsub("-mean()", "Mean", names(TidyData), ignore.case = TRUE)
> names(TidyData)<-gsub("-std()", "STD", names(TidyData), ignore.case = TRUE)
> names(TidyData)<-gsub("-freq()", "Frequency", names(TidyData), ignore.case = TRUE)
> names(TidyData)<-gsub("angle", "Angle", names(TidyData))
> names(TidyData)<-gsub("gravity", "Gravity", names(TidyData))

 FinalData <- TidyData %>%
+     group_by(subject, activity) %>%
+     summarise_all(funs(mean))
Warning message:
`funs()` was deprecated in dplyr 0.8.0.
Please use a list of either functions or lambdas: 

  # Simple named list: 
  list(mean = mean, median = median)

  # Auto named with `tibble::lst()`: 
  tibble::lst(mean, median)

  # Using lambdas
  list(~ mean(., trim = .2), ~ median(., na.rm = TRUE))
This warning is displayed once every 8 hours.
Call `lifecycle::last_warnings()` to see where this warning was generated. 
> View(FinalData)
write.table(FinalData, "FinalData.txt", row.name=FALSE)

str(FinalData)
grouped_df [180 x 88] (S3: grouped_df/tbl_df/tbl/data.frame)
 $ subject                                           : int [1:180] 1 1 1 1 1 1 2 2 2 2 ...
 $ activity                                          : chr [1:180] "LAYING" "SITTING" "STANDING" "WALKING" ...
 $ TimeBodyAccelerometer.mean...X                    : num [1:180] 0.222 0.261 0.279 0.277 0.289 ...
 $ TimeBodyAccelerometer.mean...Y                    : num [1:180] -0.04051 -0.00131 -0.01614 -0.01738 -0.00992 ...
 $ TimeBodyAccelerometer.mean...Z                    : num [1:180] -0.113 -0.105 -0.111 -0.111 -0.108 ...
 $ TimeGravityAccelerometer.mean...X                 : num [1:180] -0.249 0.832 0.943 0.935 0.932 ...
 $ TimeGravityAccelerometer.mean...Y                 : num [1:180] 0.706 0.204 -0.273 -0.282 -0.267 ...
 $ TimeGravityAccelerometer.mean...Z                 : num [1:180] 0.4458 0.332 0.0135 -0.0681 -0.0621 ...
 $ TimeBodyAccelerometerJerk.mean...X                : num [1:180] 0.0811 0.0775 0.0754 0.074 0.0542 ...
 $ TimeBodyAccelerometerJerk.mean...Y                : num [1:180] 0.003838 -0.000619 0.007976 0.028272 0.02965 ...
 $ TimeBodyAccelerometerJerk.mean...Z                : num [1:180] 0.01083 -0.00337 -0.00369 -0.00417 -0.01097 ...
 $ TimeBodyGyroscope.mean...X                        : num [1:180] -0.0166 -0.0454 -0.024 -0.0418 -0.0351 ...
 $ TimeBodyGyroscope.mean...Y                        : num [1:180] -0.0645 -0.0919 -0.0594 -0.0695 -0.0909 ...
 $ TimeBodyGyroscope.mean...Z                        : num [1:180] 0.1487 0.0629 0.0748 0.0849 0.0901 ...
 $ TimeBodyGyroscopeJerk.mean...X                    : num [1:180] -0.1073 -0.0937 -0.0996 -0.09 -0.074 ...
 $ TimeBodyGyroscopeJerk.mean...Y                    : num [1:180] -0.0415 -0.0402 -0.0441 -0.0398 -0.044 ...
 $ TimeBodyGyroscopeJerk.mean...Z                    : num [1:180] -0.0741 -0.0467 -0.049 -0.0461 -0.027 ...
 $ TimeBodyAccelerometerMagnitude.mean..             : num [1:180] -0.8419 -0.9485 -0.9843 -0.137 0.0272 ...
 $ TimeGravityAccelerometerMagnitude.mean..          : num [1:180] -0.8419 -0.9485 -0.9843 -0.137 0.0272 ...
 $ TimeBodyAccelerometerJerkMagnitude.mean..         : num [1:180] -0.9544 -0.9874 -0.9924 -0.1414 -0.0894 ...
 $ TimeBodyGyroscopeMagnitude.mean..                 : num [1:180] -0.8748 -0.9309 -0.9765 -0.161 -0.0757 ...
 $ TimeBodyGyroscopeJerkMagnitude.mean..             : num [1:180] -0.963 -0.992 -0.995 -0.299 -0.295 ...
 $ FrequencyBodyAccelerometer.mean...X               : num [1:180] -0.9391 -0.9796 -0.9952 -0.2028 0.0382 ...
 $ FrequencyBodyAccelerometer.mean...Y               : num [1:180] -0.86707 -0.94408 -0.97707 0.08971 0.00155 ...
 $ FrequencyBodyAccelerometer.mean...Z               : num [1:180] -0.883 -0.959 -0.985 -0.332 -0.226 ...
 $ FrequencyBodyAccelerometer.meanFreq...X           : num [1:180] -0.1588 -0.0495 0.0865 -0.2075 -0.3074 ...
 $ FrequencyBodyAccelerometer.meanFreq...Y           : num [1:180] 0.0975 0.0759 0.1175 0.1131 0.0632 ...
 $ FrequencyBodyAccelerometer.meanFreq...Z           : num [1:180] 0.0894 0.2388 0.2449 0.0497 0.2943 ...
 $ FrequencyBodyAccelerometerJerk.mean...X           : num [1:180] -0.9571 -0.9866 -0.9946 -0.1705 -0.0277 ...
 $ FrequencyBodyAccelerometerJerk.mean...Y           : num [1:180] -0.9225 -0.9816 -0.9854 -0.0352 -0.1287 ...
 $ FrequencyBodyAccelerometerJerk.mean...Z           : num [1:180] -0.948 -0.986 -0.991 -0.469 -0.288 ...
 $ FrequencyBodyAccelerometerJerk.meanFreq...X       : num [1:180] 0.132 0.257 0.314 -0.209 -0.253 ...
 $ FrequencyBodyAccelerometerJerk.meanFreq...Y       : num [1:180] 0.0245 0.0475 0.0392 -0.3862 -0.3376 ...
 $ FrequencyBodyAccelerometerJerk.meanFreq...Z       : num [1:180] 0.02439 0.09239 0.13858 -0.18553 0.00937 ...
 $ FrequencyBodyGyroscope.mean...X                   : num [1:180] -0.85 -0.976 -0.986 -0.339 -0.352 ...
 $ FrequencyBodyGyroscope.mean...Y                   : num [1:180] -0.9522 -0.9758 -0.989 -0.1031 -0.0557 ...
 $ FrequencyBodyGyroscope.mean...Z                   : num [1:180] -0.9093 -0.9513 -0.9808 -0.2559 -0.0319 ...
 $ FrequencyBodyGyroscope.meanFreq...X               : num [1:180] -0.00355 0.18915 -0.12029 0.01478 -0.10045 ...
 $ FrequencyBodyGyroscope.meanFreq...Y               : num [1:180] -0.0915 0.0631 -0.0447 -0.0658 0.0826 ...
 $ FrequencyBodyGyroscope.meanFreq...Z               : num [1:180] 0.010458 -0.029784 0.100608 0.000773 -0.075676 ...
 $ FrequencyBodyAccelerometerMagnitude.mean..        : num [1:180] -0.8618 -0.9478 -0.9854 -0.1286 0.0966 ...
 $ FrequencyBodyAccelerometerMagnitude.meanFreq..    : num [1:180] 0.0864 0.2367 0.2846 0.1906 0.1192 ...
 $ FrequencyBodyAccelerometerJerkMagnitude.mean..    : num [1:180] -0.9333 -0.9853 -0.9925 -0.0571 0.0262 ...
 $ FrequencyBodyAccelerometerJerkMagnitude.meanFreq..: num [1:180] 0.2664 0.3519 0.4222 0.0938 0.0765 ...
 $ FrequencyBodyGyroscopeMagnitude.mean..            : num [1:180] -0.862 -0.958 -0.985 -0.199 -0.186 ...
 $ FrequencyBodyGyroscopeMagnitude.meanFreq..        : num [1:180] -0.139775 -0.000262 -0.028606 0.268844 0.349614 ...
 $ FrequencyBodyGyroscopeJerkMagnitude.mean..        : num [1:180] -0.942 -0.99 -0.995 -0.319 -0.282 ...
 $ FrequencyBodyGyroscopeJerkMagnitude.meanFreq..    : num [1:180] 0.176 0.185 0.334 0.191 0.19 ...
 $ Angle.TimeBodyAccelerometerMean.Gravity.          : num [1:180] 0.021366 0.027442 -0.000222 0.060454 -0.002695 ...
 $ Angle.TimeBodyAccelerometerJerkMean..GravityMean. : num [1:180] 0.00306 0.02971 0.02196 -0.00793 0.08993 ...
 $ Angle.TimeBodyGyroscopeMean.GravityMean.          : num [1:180] -0.00167 0.0677 -0.03379 0.01306 0.06334 ...
 $ Angle.TimeBodyGyroscopeJerkMean.GravityMean.      : num [1:180] 0.0844 -0.0649 -0.0279 -0.0187 -0.04 ...
 $ Angle.X.GravityMean.                              : num [1:180] 0.427 -0.591 -0.743 -0.729 -0.744 ...
 $ Angle.Y.GravityMean.                              : num [1:180] -0.5203 -0.0605 0.2702 0.277 0.2672 ...
 $ Angle.Z.GravityMean.                              : num [1:180] -0.3524 -0.218 0.0123 0.0689 0.065 ...
 $ TimeBodyAccelerometer.std...X                     : num [1:180] -0.928 -0.977 -0.996 -0.284 0.03 ...
 $ TimeBodyAccelerometer.std...Y                     : num [1:180] -0.8368 -0.9226 -0.9732 0.1145 -0.0319 ...
 $ TimeBodyAccelerometer.std...Z                     : num [1:180] -0.826 -0.94 -0.98 -0.26 -0.23 ...
 $ TimeGravityAccelerometer.std...X                  : num [1:180] -0.897 -0.968 -0.994 -0.977 -0.951 ...
 $ TimeGravityAccelerometer.std...Y                  : num [1:180] -0.908 -0.936 -0.981 -0.971 -0.937 ...
 $ TimeGravityAccelerometer.std...Z                  : num [1:180] -0.852 -0.949 -0.976 -0.948 -0.896 ...
 $ TimeBodyAccelerometerJerk.std...X                 : num [1:180] -0.9585 -0.9864 -0.9946 -0.1136 -0.0123 ...
 $ TimeBodyAccelerometerJerk.std...Y                 : num [1:180] -0.924 -0.981 -0.986 0.067 -0.102 ...
 $ TimeBodyAccelerometerJerk.std...Z                 : num [1:180] -0.955 -0.988 -0.992 -0.503 -0.346 ...
 $ TimeBodyGyroscope.std...X                         : num [1:180] -0.874 -0.977 -0.987 -0.474 -0.458 ...
 $ TimeBodyGyroscope.std...Y                         : num [1:180] -0.9511 -0.9665 -0.9877 -0.0546 -0.1263 ...
 $ TimeBodyGyroscope.std...Z                         : num [1:180] -0.908 -0.941 -0.981 -0.344 -0.125 ...
 $ TimeBodyGyroscopeJerk.std...X                     : num [1:180] -0.919 -0.992 -0.993 -0.207 -0.487 ...
 $ TimeBodyGyroscopeJerk.std...Y                     : num [1:180] -0.968 -0.99 -0.995 -0.304 -0.239 ...
 $ TimeBodyGyroscopeJerk.std...Z                     : num [1:180] -0.958 -0.988 -0.992 -0.404 -0.269 ...
 $ TimeBodyAccelerometerMagnitude.std..              : num [1:180] -0.7951 -0.9271 -0.9819 -0.2197 0.0199 ...
 $ TimeGravityAccelerometerMagnitude.std..           : num [1:180] -0.7951 -0.9271 -0.9819 -0.2197 0.0199 ...
 $ TimeBodyAccelerometerJerkMagnitude.std..          : num [1:180] -0.9282 -0.9841 -0.9931 -0.0745 -0.0258 ...
 $ TimeBodyGyroscopeMagnitude.std..                  : num [1:180] -0.819 -0.935 -0.979 -0.187 -0.226 ...
 $ TimeBodyGyroscopeJerkMagnitude.std..              : num [1:180] -0.936 -0.988 -0.995 -0.325 -0.307 ...
 $ FrequencyBodyAccelerometer.std...X                : num [1:180] -0.9244 -0.9764 -0.996 -0.3191 0.0243 ...
 $ FrequencyBodyAccelerometer.std...Y                : num [1:180] -0.834 -0.917 -0.972 0.056 -0.113 ...
 $ FrequencyBodyAccelerometer.std...Z                : num [1:180] -0.813 -0.934 -0.978 -0.28 -0.298 ...
 $ FrequencyBodyAccelerometerJerk.std...X            : num [1:180] -0.9642 -0.9875 -0.9951 -0.1336 -0.0863 ...
 $ FrequencyBodyAccelerometerJerk.std...Y            : num [1:180] -0.932 -0.983 -0.987 0.107 -0.135 ...
 $ FrequencyBodyAccelerometerJerk.std...Z            : num [1:180] -0.961 -0.988 -0.992 -0.535 -0.402 ...
 $ FrequencyBodyGyroscope.std...X                    : num [1:180] -0.882 -0.978 -0.987 -0.517 -0.495 ...
 $ FrequencyBodyGyroscope.std...Y                    : num [1:180] -0.9512 -0.9623 -0.9871 -0.0335 -0.1814 ...
 $ FrequencyBodyGyroscope.std...Z                    : num [1:180] -0.917 -0.944 -0.982 -0.437 -0.238 ...
 $ FrequencyBodyAccelerometerMagnitude.std..         : num [1:180] -0.798 -0.928 -0.982 -0.398 -0.187 ...
 $ FrequencyBodyAccelerometerJerkMagnitude.std..     : num [1:180] -0.922 -0.982 -0.993 -0.103 -0.104 ...
 $ FrequencyBodyGyroscopeMagnitude.std..             : num [1:180] -0.824 -0.932 -0.978 -0.321 -0.398 ...
 $ FrequencyBodyGyroscopeJerkMagnitude.std..         : num [1:180] -0.933 -0.987 -0.995 -0.382 -0.392 ...
 - attr(*, "groups")= tibble [30 x 2] (S3: tbl_df/tbl/data.frame)
  ..$ subject: int [1:30] 1 2 3 4 5 6 7 8 9 10 ...
  ..$ .rows  : list<int> [1:30] 
  .. ..$ : int [1:6] 1 2 3 4 5 6
  .. ..$ : int [1:6] 7 8 9 10 11 12
  .. ..$ : int [1:6] 13 14 15 16 17 18
  .. ..$ : int [1:6] 19 20 21 22 23 24
  .. ..$ : int [1:6] 25 26 27 28 29 30
  .. ..$ : int [1:6] 31 32 33 34 35 36
  .. ..$ : int [1:6] 37 38 39 40 41 42
  .. ..$ : int [1:6] 43 44 45 46 47 48
  .. ..$ : int [1:6] 49 50 51 52 53 54
  .. ..$ : int [1:6] 55 56 57 58 59 60
  .. ..$ : int [1:6] 61 62 63 64 65 66
  .. ..$ : int [1:6] 67 68 69 70 71 72
  .. ..$ : int [1:6] 73 74 75 76 77 78
  .. ..$ : int [1:6] 79 80 81 82 83 84
  .. ..$ : int [1:6] 85 86 87 88 89 90
  .. ..$ : int [1:6] 91 92 93 94 95 96
  .. ..$ : int [1:6] 97 98 99 100 101 102
  .. ..$ : int [1:6] 103 104 105 106 107 108
  .. ..$ : int [1:6] 109 110 111 112 113 114
  .. ..$ : int [1:6] 115 116 117 118 119 120
  .. ..$ : int [1:6] 121 122 123 124 125 126
  .. ..$ : int [1:6] 127 128 129 130 131 132
  .. ..$ : int [1:6] 133 134 135 136 137 138
  .. ..$ : int [1:6] 139 140 141 142 143 144
  .. ..$ : int [1:6] 145 146 147 148 149 150
  .. ..$ : int [1:6] 151 152 153 154 155 156
  .. ..$ : int [1:6] 157 158 159 160 161 162
  .. ..$ : int [1:6] 163 164 165 166 167 168
  .. ..$ : int [1:6] 169 170 171 172 173 174
  .. ..$ : int [1:6] 175 176 177 178 179 180
  .. ..@ ptype: int(0) 
  ..- attr(*, ".drop")= logi TRUE
