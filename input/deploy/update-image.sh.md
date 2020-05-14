## update-image.sh
```
image=需填写
token=需填写
project_id=需填写

docker pull registry.gitlab.meiguipai.com/gaogao1030/nginx:master
git fetch --prune

branch=$(git branch 2>/dev/null | grep '^*' | colrm 1 2)

r_branch=$(git branch -r | grep "^  origin/${branch}$" | colrm 1 2)

echo "Current Branch: ${branch}"
echo "Remote Branch: ${r_branch}"

if [ ! $r_branch ]; then
  echo "Faild to local deploy. that no remote branch: ${branch}"
  echo "[Tips] Push branch before local deploy"
  exit
fi

if [ ! $1 ]; then
  ENV="beta"
else
  ENV=$1
fi

if [ ! $NO_BUILD ]; then
  RELEASE_MODE=remote APP_ENV=$ENV npm run build
fi

docker build -f Local.Dockerfile -t $image .

docker tag $image "${image}:${ENV}"
docker push $image:$ENV

curl -X POST \
  -F token=$token \
  -F "ref=${branch}" \
  -F "variables[LOCAL_DEPLOY]=true" \
  -F "variables[CI_ENVIRONMENT_SLUG]=${ENV}" \
  https://gitlab.meiguipai.com/api/v4/projects/$id/trigger/pipeline
```
