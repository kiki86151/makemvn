# How to create a maven repository for your github project step by step

## Clone your project in a separate folder

(note: replace `ORGANIZATION` and `PROJECT`)

`git clone git clone git@github.com:ORGANIZATION/PROJECT.git my-repository`

## Cd into it

`cd my-repository`

## Create a new branch (here named repository)

`git branch repository`

## Switch to that branch

`git checkout repository`

## Remove all files

`rm -rf file1 file2 file3 .. etc`

## Install your jar in that directory

(note: replace `YOUR_GROUP`, `YOUR_ARTIFACT`, `YOUR_VERSION` and `YOUR_JAR_FILE`)

```bash
mvn install:install-file -DgroupId=YOUR_GROUP -DartifactId=YOUR_ARTIFACT -Dversion=YOUR_VERSION -Dfile=YOUR_JAR_FILE -Dpackaging=jar -DgeneratePom=true -DlocalRepositoryPath=.  -DcreateChecksum=true
```

`YOUR_JAR_FILE` should point to an existent jar file, this is why it's best to create your repository branch in a different folder, so you can reference the existing jar in `/your/project/path/target/artifact-x.y.z.jar`

## Add all generated files, commit and push

`git add -A . && git commit -m "released version X.Y.Z"`

`git push origin repository`

## Reference your jar from a different project

The repository url you just created is https://raw.github.com/YOUR_ORGANIZATION/YOUR_ARTIFACT/repository/
