### Environment
Export env:
```console
conda env export --no-builds > environment.yml
```
### USAGE
Run triton server
```console
$ docker run --rm -p8000:8000 -p8001:8001 -p8002:8002 -v$PWD/model_repository:/models nvcr.io/nvidia/tritonserver:22.07-py3 tritonserver --model-repository=/models 
```
Test 
```console
$  python image_client.py -m densenet_onnx -c 3 -s INCEPTION -i http -u localhost:8000 data
```
Check health metric
[Link](https://github.com/triton-inference-server/server/blob/main/docs/user_guide/metrics.md)
```console
$ curl localhost:8002/metrics -o heath.txt
```
