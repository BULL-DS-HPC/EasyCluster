# EasySlurm
Wrapper Command Line for Slurm Scheduler
```
[root-zara-pts12] ~ # smpp -h

 Usage : /usr/bin/smpp [-v] [-u login] [-s status] [-p partition] [ -n node ]
 Usage : /usr/bin/smpp -c by_xxx
 Usage : /usr/bin/smpp -j jobid [-o format,format,format]
 Usage : /usr/bin/smpp -N nodelist [-o format,format,format]
 Usage : /usr/bin/smpp [-J login] [-S starttime] [-E endtime] [-o format,format,...] 

 -v 	 Niveau de verbosité
 -u 	 Affichage des jobs en machine pour un utilisateur ( '-u my' affiche mes jobs )
 -s 	 Affichage des jobs en machine par status ( run / pend / other ) 
 -p 	 Affichage des jobs en machine par partition ( cn/bm/gn/all/mix/ )
 -n 	 Affichage des jobs en machine par node ( node1,node2,... / node[1-5] )
 -c 	 Affichage du nombre de jobs en machine trier ( by_user / by_part / by_qos )
 -j 	 Affichage du status d'un job 
 -J 	 Historique des jobs d'un utilisateur 
 -N 	 Historique des jobs sur des noeuds ( /!\ par defaut affichage depuis la date du jour )
 -S 	 Historique des jobs apres cette date YYYY-MM-DD[THH:MM[:SS]] 
 -E 	 Historique des jobs avant cette date YYYY-MM-DD[THH:MM[:SS]]
 -o 	 Modification du format de sortie :

    		 AllocCPUS       Account       AssocID       AveCPU
    		 AveCPUFreq      AvePages      AveRSS        AveVMSize
    		 BlockID         Cluster       Comment       ConsumedEnergy
    		 CPUTime         CPUTimeRAW    DerivedExitCode Elapsed
    		 Eligible        End           ExitCode      GID
    		 Group           JobID         JobName       Layout
    		 MaxPages        MaxPagesNode  MaxPagesTask  MaxRSS
    		 MaxRSSNode      MaxRSSTask    MaxVMSize     MaxVMSizeNode
    		 MaxVMSizeTask   MinCPU        MinCPUNode    MinCPUTask
    		 NCPUS           NNodes        NodeList      NTasks
    		 Priority        Partition     QOSRAW        ReqCPUS
    		 Reserved        ResvCPU       ResvCPURAW    Start
    		 State           Submit        Suspended     SystemCPU
    		 Timelimit       TotalCPU      UID           User
    		 UserCPU         WCKey         WCKeyID
```
```
[root-zara-pts12] ~ # smpp

  [Cluster - zara ( slurm version 17.11.2 )] 

       JOBID     PART                  QOS            NAME       USER      STATE         TIME    TIMELIMIT           START_TIME    NODES             NODELIST
  ---------- -------- -------------------- --------------- ---------- ----------   ----------   ---------- -------------------- -------- --------------------
    13457081       bm              bm_long           job01     login1    RUNNING     23:36:17   4-17:21:00  2018-12-05T10:21:29        1             zbm0018
    13457082       bm              bm_long           job07     login2    RUNNING     20:23:02   4-17:21:00  2018-12-05T13:34:44        1             zbm0162
    13464889       cn               cnlong           job09     login4    PENDING         0:00   3-00:00:00                  N/A       96 (QOSMaxCpuPerUserLim
    13479802       cn               cn_all          job011     login5    PENDING         0:00   3-00:00:00                  N/A        4 (QOSMaxCpuPerUserLim
  13460004_1       cn               cn_all           job0U     login6 COMPLETING     17:45:33     20:00:00  2018-12-05T15:50:01        1             zcn0055

```
```
[root-zara-pts12] ~ # smqinfo 

  [Cluster - zara ( slurm version 17.11.2 )]  

                     Name   Priority  GraceTime PreemptMode UsageFactor GrpJobs GrpSubmit MaxJobs  MaxCPUs MaxNodes     MaxWall       GrpTRES 
     -------------------- ---------- ---------- ----------- ----------- ------- --------- ------- -------- -------- ----------- ------------- 
                   normal          0   00:00:00     cluster    1.000000       0         0                                                     
                 cn_short        100   00:00:00     cluster    1.000000                                                08:00:00               
                all_short        100   00:00:00     cluster    1.000000                                                08:00:00               
                       gn        100   00:00:00     cluster    1.000000                                                08:00:00       cpu=460 
 
```
```
[root-zara-pts12] ~ # cce_mpinfo 

  [Cluster - zara ( slurm version 17.11.2 )]  

                               ------------------  NODE ------------------ ------------------   CPU ------------------
      Name   Priority    State      Total       Down       Used       Free      Total       Down       Used       Free       Taux                          Nodes
  --------   -------- -------- ---------- ---------- ---------- ---------- ---------- ---------- ---------- ---------- ---------- ------------------------------
        cn         1*       UP       1164          3       1078         83      32592        112      29276       3204     89.82%                zcn[0001-1164]
        bm          1       UP        162          0         55        107       4288          0       1387       2901     32.34%                zbm[0001-0162]
....

```
```
[root-zara-pts12] ~ # suser 

Usage : suser [-S] [-X|-Y] -u utilisateur 

	 -S 	 Utilisation screen
	 -X|Y 	 Utilisation export graphique

```
```
10:02:54 [login@zara ~]$ squota 

 Disk quota for user login ( uid 2856 ):
                                                ------------------ VOLUME ------------------                            
                             type   filesystem      usage       soft       hard        grace
                        ---------    ---------     ------      -----      -----       ------
                        USR/login         home     14.38G       300G       450G      [-----]
                           notset      scratch          -          -          -            -

```
