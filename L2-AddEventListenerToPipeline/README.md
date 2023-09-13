# Adding GitHub Triggers

kubectl apply -f tasks.yaml
kubectl apply -f pipeline.yaml

tkn task ls
tkn pipeline ls

kubectl apply -f eventlistener.yaml
tkn eventlistener ls
kubectl apply -f triggerbinding.yaml
kubectl apply -f triggertemplate.yaml

kubectl port-forward service/el-cd-listener  8090:8080

curl -X POST http://localhost:8090 \
  -H 'Content-Type: application/json' \
  -d '{"ref":"main","repository":{"url":"https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode"}}'
  
 tkn pipelinerun ls
 tkn pipelinerun logs --last