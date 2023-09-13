# Building an Image

tkn hub install task git-clone

tkn hub install task flake8
kubectl apply -f tasks.yaml

tkn clustertask ls

make sure that buildah is in there already

kubectl apply -f pipeline.yaml

kubectl apply -f pvc.yaml

tkn pipeline start cd-pipeline \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch=main \
    -p build-image=image-registry.openshift-image-registry.svc:5000/$SN_ICR_NAMESPACE/tekton-lab:latest \
    -w name=pipeline-workspace,claimName=pipelinerun-pvc \
    --showlog