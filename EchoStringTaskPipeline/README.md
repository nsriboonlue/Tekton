# Create a base pipeline and task to take in param and echo

kubectl apply -f tasks.yaml

kubectl apply -f pipeline.yaml

tkn pipeline start hello-pipeline \
    --showlog  \
    -p message="Hello Tekton!"
