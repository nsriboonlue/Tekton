# Create a base pipeline and task to take in param and echo

kubectl apply -f tasks.yaml

kubectl apply -f pipeline.yaml

tkn pipeline start cd-pipeline \
    --showlog \
    -p repo-url="https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode.git" \
    -p branch="main"