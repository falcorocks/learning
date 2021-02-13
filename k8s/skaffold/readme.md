# Skaffold

Skaffold greatly eases development of kubernetes container based applications by
avoiding the need to manually stop/rebuild/redeploy your images.
* `skaffold init` helps you declare your "stack" of in a `skaffold.yaml`.
* `skaffold.yaml` ties together all your kubernetes manifests in one single file.
* `skaffold run` will `kubectl apply` all the manifests. It is the same as `docker-compose up -d`.
* `skaffold dev` is where the advantage over compose lies. It will do the same as `skaffold run` but it will also
   - display the logs (so the same as `docker-compose up`)
   - monitor the files related to the manifests (including application logic that is copied in the dockerfile)
   and automatically trigger a rebuild when changes are detected.

`Skaffold dev` is one of the main reasons why I am migrating from docker-compose to kubernetes! You don't always want to trigger a rebuild, so you can also configure skaffold to simply sync a directory. In `docker-compose` you would do this with a volume mount, which is less elegant and less portable.

IMHO `skaffold run` is also a nicer way to ask others to deploy your applications compared to using kubectl directly (especially with a large amount of manifests)...

### install

* mac/linux: `brew install skaffold`


### prerequisites

* docker
* kubernetes

### resources
* https://skaffold.dev
* https://www.youtube.com/watch?v=8_Ozfa7JLEs
* https://www.youtube.com/watch?v=j37yZLPWijw&t=1210s

```bash
$ skaffold dev
$ kubectl port-forward service/hello-service 7777:5000
# in a new terminal
$ curl :7777
Hello, World!
```