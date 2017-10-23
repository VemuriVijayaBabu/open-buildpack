# OpenCV buildpack for Cloud Foundry

Cloud Foundry applications can blend multiple buildpacks together. If your application requires [OpenCV](https://opencv.org/), then this buildpack can help you.

If you want to learn how to make a "supply"-only buildpack for multi-buildpack support, then this is an example buildpack for you. Learn more from [Keaty Gross at CF Summit EU 2017](https://www.youtube.com/watch?v=41wEXS03U78).

```
cf v3-push sample-app-with-opencv -p fixtures/sample \
  -b https://github.com/cloudfoundry-community/opencv-buildpack \
  -b python_buildpack
```

NOTE: you may need to change `sample-app-with-opencv` to something unique if you get an error about the default route already existing on your Cloud Foundry.

During staging, you will see OpenCV being installed:

```
Successfully created container
Downloading build artifacts cache...
Downloading app package...
Downloaded app package (826B)
-----> Download go 1.9
-----> Running go build supply
-----> OpenCV Buildpack version 0.1.0
-----> Installing opencv
       Using opencv version 3.3.0
-----> Installing opencv 3.3.0
       Download [http://opencv-buildpack.s3-website-us-east-1.amazonaws.com/blobs/opencv/opencv-compiled-3.3.0.tgz]
-----> Python Buildpack version 1.7.4
-----> Supplying Python
...
```

## Building latest opencv

The [`packages/opencv`](https://github.com/cloudfoundry-community/opencv-buildpack/tree/master/packages/opencv) folder contains the instructions for compiling + uploading a binary version of OpenCV.
