docker build --platform linux/amd64 -t museify .

docker images

docker run --name museify-container -d `
-e OPENAI_API_KEY=$((aws ssm get-parameters --region ap-northeast-2 --name "/DEV/CICD/MUSEIFY/OPENAI_API_KEY" --query "Parameters[0].Value").Trim('"')) `
-p 8501:8501 museify

docker ps
