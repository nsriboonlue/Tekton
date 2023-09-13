# Use Tekton CD Catalog

kubectl apply -f tasks.yaml

tkn hub install task git-clone --version 0.8
kubectl apply -f pvc.yaml
kubectl apply -f pipeline.yaml

tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch="main" \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    --showlog
	
tkn pipelinerun ls

tkn pipelinerun logs --last