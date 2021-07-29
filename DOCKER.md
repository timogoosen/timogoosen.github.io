###  Docker


### MultiArch Builds

* [Docker build cache sharing on multi hosts with Buildkit buildx](https://medium.com/titansoft-engineering/docker-build-cache-sharing-on-multi-hosts-with-buildkit-and-buildx-eb8f7005918e)
* [Build Multi Arch Images with EC2 Gravitron](https://www.inqdo.com/docker-images-with-aws-graviton/?lang=en)


#### Cheathseets:

* [Cleanup Docker images and containers locally](https://gist.github.com/beeman/aca41f3ebd2bf5efbd9d7fef09eac54d)
* [Ultimate Docker Cheat Sheet by Ruan Bekker](https://gist.github.com/ruanbekker/4e8e4ca9b82b103973eaaea4ac81aa5f)

### Dockerfile Optimizations:




* [Optimizing Your Dockerfiles](https://www.ginkgobioworks.com/2020/05/18/optimizing-your-dockerfile/)
* [Optimize your Dockerfile in your Typescript project](https://javascript.plainenglish.io/optimize-the-dockerfile-in-your-node-js-project-53acbe1eb859)


### Reclaim space

If you are on Mac and docker is taking up lots of space then run this:


```

docker run --privileged --pid=host docker/desktop-reclaim-space

```