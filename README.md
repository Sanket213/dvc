DVC demo

src, dvc_pipeline.txt, prams.yaml, readme.md   --- this will be initial file

1. git clone https://github.com/
2. intall requirements 
3. dvc init
4. dvc remote add -d (path name) -------------------- where you want to store the version
   dvc remote add -d local ..\..\dvc_remote 
    -- now config file will get updated
5. Copy the first command from dvc_pipeline.txt -- run -- will create yaml file
    run all first 4 commands till evaluate
6. Now eun the pipeline means dvc.yaml file
    dvc repro

dvc.lock file will be created to record the cachce version
.gitignore will be created to get the record from the local

7. dvc dag 
    above command will display the pipeline 

8. paste the below code in dvc.yaml
    run dvc plots show

plots:
- ROC:
    template: simple
    x: fpr
    y: 
        eval\live\plots\sklearn\roc\train.json:tpr
        eval\live\plots\sklearn\roc\test.json:tpr
- Confusion-Matrix:
    template: confusion
    x: actual
    y:
        eval\live\plots\sklearn\cm\train.json:predicted
        eval\live\plots\sklearn\cm\test.json:predicted
- Precision-Recall:
    template: simple
    x: recall
    y:
        eval\prc\train.json: precision
        eval\prc\test.json: precision

- eval\importance.png


9. dvc status
    git status

    git add .
    git commit -m "first version"
    git tag v1.0
    git push -u origin main
    git push --tag

10. change some parameter in params.yaml file

    then again dvc repro and step 10

11. dvc metrics diff
    to check the differnece

12. run  dvc push
    to track the data and models which will get added to  remote folder which we have created in loacl in step 4



13. git checkout v1.0 
    will show the result of particular version

    chekc by using
    dvc pull
    dvc params show
