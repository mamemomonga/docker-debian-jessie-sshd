# debian jessie sshd on Docker
debian jessieのsshdをDockerで動かす

## build image
イメージの構築

	docker build -t mamemomonga/debian-jessie-sshd .

## start server, upload public key and connect ssh
サーバ起動、公開鍵アップロード、そしてSSH接続

	docker run -d --name debian-jessie-sshd-01 -p 2222:22 mamemomonga/debian-jessie-sshd
	cat ~/.ssh/id_rsa.pub | docker exec -i debian-jessie-sshd-01 sh -c 'cat >> /root/.ssh/authorized_keys'
	ssh -p 2222 root@localhost



