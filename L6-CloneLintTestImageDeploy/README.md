# Deploy to Kubernetes / OpenShift

tkn hub install task git-clone
tkn hub install task flake8
kubectl apply -f tasks.yaml
kubectl apply -f pvc.yaml
tkn clustertask ls

look for openshift-client

kubectl apply -f pipeline.yaml

tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch=main \
    -p app-name=hitcounter \
    -p build-image=image-registry.openshift-image-registry.svc:5000/$SN_ICR_NAMESPACE/tekton-lab:latest \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    --showlog
	
kubectl get all -l app=hitcounter