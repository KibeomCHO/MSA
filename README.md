# MSA

# 1. GitRepository생성.
* cf) git clone https://github.com/xxxxxx/MSA

# 2. Pc나 실습서버에 Clone
```
git clone https://github.com/xxxxxx/MSA
```

# 3. Docker Image만들기.
## Sample docker build  구하기.
```
cd
git clone https://github.com/nowage/dockers
```

# 4. MyDocker Image만들기.
```
cd
cp -r dockers/nginx2/ MSA/nginx
cd MSA/nginx/
docker build --rm -t xxxxxx/nginx:0.1 .
```

# 5. Docker image push
```
docker login
docker push xxxxxx/nginx:0.1
```

# 6. yaml artifact 만들기.
```
echo "---" >> n1.yml
kubectl create deploy --image=kibeomcho/nginx:0.1 n1 --port=80 --dry-run=client -o yaml >> n1.yml
echo "---" >> n1.yml
kubectl expose deploy n1 --type="NodePort" --port 80 >> n1.yml
```
* console로 yml파일 가져 오기.[실습용 Console서버에서 구현.]
```
cd ~/MSA
cd n1
mkdir n1
cd n1
scp vm01:/home/ubuntu/n1.yaml ./

```

7. github로 push
```
git add -A
git commit -m "initial commit"
git push
````

8. Namespace생성
* vm01
```
kubectl create namespace n1
```

9. argocd UI접근해서
* Create new
* Sync
