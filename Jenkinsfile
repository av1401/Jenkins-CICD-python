node{
stage ("Checkout"){
checkout scm
}
stage ("Testing"){
try{
sh 'python3 test.py'
}catch (err){

currentBuild.result="FAILURE"
error("Test failed: ${err})


}
}

if (env.CHANGE_ID && ( currentBuild.result== null || currentBuild.result=="SUCCESS"){

stage("Approval"){

input message :"Test case passed wanna approve?", ok : "Merge"

echo "Now merging with Github"
}
}

}
