# peoplenet-tao-toolkit
peoplenet-tao-toolkit は、NVIDIA TAO TOOLKIT を用いて PeopleNet の AIモデル最適化を行うマイクロサービスです。  

## 動作環境
- NVIDIA 
    - TAO TOOLKIT
- PeopleNet
- Docker
- TensorRT Runtime

## 動作手順

### engineファイルの生成
PeopleNet のAIモデルをデバイスに最適化するため、ResNet34 における PeopleNet の .etlt ファイルを engine file に変換します。
engine fileへの変換は、Makefile に記載された以下のコマンドにより実行できます。

```
tao-convert:
	docker exec -it tao-tool-kit tao-converter -k tlt_encode -d 3,544,960 -e /app/src/saved.engine /app/src/resnet34_peoplenet_pruned.etlt 
```

## 相互依存関係にあるマイクロサービス  
本マイクロサービスで最適化された PeopleNet の AIモデルを Deep Stream 上で動作させる手順は、[peoplenet-deepstream](https://github.com/latonaio/peoplenet-deepstream)を参照してください。  


