### SGA Docker Container

Docker virtualization of a full SGA pipeline – using a modified .dot-verbose version of SGA to enable comparison / evaluation of the single steps in the scaffolding algorithm.

#### USAGE
1. [Install](https://docs.docker.com/installation/) Docker
2. Pull [automated build](https://docs.docker.com/docker-hub/builds/) of this image: `docker pull stpf/sga`
3. Navigate to files and run pipeline `docker run -v $(pwd):/input READ_1.fq READ_2.fq` (replace filenames accordingly).
