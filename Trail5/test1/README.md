# 实验5_1  TensorFlow Lite 模型生成

## 安装相关类库


```python
!pip install tflite-model-maker
```

    Requirement already satisfied: tflite-model-maker in d:\software\anaconda3\lib\site-packages (0.3.4)
    Requirement already satisfied: lxml>=4.6.1 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (4.6.3)
    Requirement already satisfied: neural-structured-learning>=1.3.1 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (1.4.0)
    Requirement already satisfied: tensorflow-addons>=0.11.2 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (0.20.0)
    Requirement already satisfied: matplotlib<3.5.0,>=3.0.3 in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from tflite-model-maker) (3.4.2)
    Requirement already satisfied: urllib3!=1.25.0,!=1.25.1,<1.26,>=1.21.1 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (1.25.11)
    Requirement already satisfied: tflite-support>=0.3.1 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (0.4.0)
    Requirement already satisfied: tensorflow>=2.6.0 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (2.9.0)
    Requirement already satisfied: numba==0.53 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (0.53.0)
    Requirement already satisfied: absl-py>=0.10.0 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (1.4.0)
    
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)


​    
​    Requirement already satisfied: tensorflow-hub<0.13,>=0.7.0 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (0.12.0)
​    Requirement already satisfied: pillow>=7.0.0 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (8.4.0)
​    Requirement already satisfied: librosa==0.8.1 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (0.8.1)
​    Requirement already satisfied: Cython>=0.29.13 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (0.29.24)
​    Requirement already satisfied: flatbuffers==1.12 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (1.12)
​    Requirement already satisfied: six>=1.12.0 in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from tflite-model-maker) (1.16.0)
​    Requirement already satisfied: tensorflow-model-optimization>=0.5 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (0.7.3)
​    Requirement already satisfied: PyYAML>=5.1 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (6.0)
​    Requirement already satisfied: tensorflow-datasets>=2.1.0 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (4.9.2)
​    Requirement already satisfied: tensorflowjs>=2.4.0 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (3.18.0)
​    Requirement already satisfied: numpy>=1.17.3 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (1.20.3)
​    Requirement already satisfied: sentencepiece>=0.1.91 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (0.1.99)
​    Requirement already satisfied: fire>=0.3.1 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (0.5.0)
​    Requirement already satisfied: tf-models-official==2.3.0 in d:\software\anaconda3\lib\site-packages (from tflite-model-maker) (2.3.0)
​    Requirement already satisfied: decorator>=3.0.0 in d:\software\anaconda3\lib\site-packages (from librosa==0.8.1->tflite-model-maker) (5.1.0)
​    Requirement already satisfied: resampy>=0.2.2 in d:\software\anaconda3\lib\site-packages (from librosa==0.8.1->tflite-model-maker) (0.4.2)
​    Requirement already satisfied: soundfile>=0.10.2 in d:\software\anaconda3\lib\site-packages (from librosa==0.8.1->tflite-model-maker) (0.12.1)
​    Requirement already satisfied: packaging>=20.0 in d:\software\anaconda3\lib\site-packages (from librosa==0.8.1->tflite-model-maker) (20.9)
​    Requirement already satisfied: scikit-learn!=0.19.0,>=0.14.0 in d:\software\anaconda3\lib\site-packages (from librosa==0.8.1->tflite-model-maker) (0.24.2)
​    Requirement already satisfied: scipy>=1.0.0 in d:\software\anaconda3\lib\site-packages (from librosa==0.8.1->tflite-model-maker) (1.7.1)
​    Requirement already satisfied: joblib>=0.14 in d:\software\anaconda3\lib\site-packages (from librosa==0.8.1->tflite-model-maker) (1.1.0)
​    Requirement already satisfied: pooch>=1.0 in d:\software\anaconda3\lib\site-packages (from librosa==0.8.1->tflite-model-maker) (1.7.0)


```python
!pip install conda-repo-cli==1.0.4
```


    Requirement already satisfied: audioread>=2.0.0 in d:\software\anaconda3\lib\site-packages (from librosa==0.8.1->tflite-model-maker) (3.0.0)
    Requirement already satisfied: setuptools in d:\software\anaconda3\lib\site-packages (from numba==0.53->tflite-model-maker) (58.0.4)
    Requirement already satisfied: llvmlite<0.37,>=0.36.0rc1 in d:\software\anaconda3\lib\site-packages (from numba==0.53->tflite-model-maker) (0.36.0)
    Requirement already satisfied: google-api-python-client>=1.6.7 in d:\software\anaconda3\lib\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (2.86.0)
    Requirement already satisfied: opencv-python-headless in d:\software\anaconda3\lib\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (4.7.0.72)
    Requirement already satisfied: pandas>=0.22.0 in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (1.3.0)
    Requirement already satisfied: py-cpuinfo>=3.3.0 in d:\software\anaconda3\lib\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (9.0.0)
    Requirement already satisfied: gin-config in d:\software\anaconda3\lib\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (0.5.0)
    Requirement already satisfied: kaggle>=1.3.9 in d:\software\anaconda3\lib\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (1.5.13)
    Requirement already satisfied: dataclasses in d:\software\anaconda3\lib\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (0.6)
    Requirement already satisfied: tf-slim>=1.1.0 in d:\software\anaconda3\lib\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (1.1.0)
    Requirement already satisfied: psutil>=5.4.3 in d:\software\anaconda3\lib\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (5.8.0)
    Requirement already satisfied: google-cloud-bigquery>=0.31.0 in d:\software\anaconda3\lib\site-packages (from tf-models-official==2.3.0->tflite-model-maker) (3.10.0)
    Requirement already satisfied: termcolor in d:\software\anaconda3\lib\site-packages (from fire>=0.3.1->tflite-model-maker) (2.3.0)
    Requirement already satisfied: google-auth<3.0.0dev,>=1.19.0 in d:\software\anaconda3\lib\site-packages (from google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (2.18.0)
    Requirement already satisfied: httplib2<1dev,>=0.15.0 in d:\software\anaconda3\lib\site-packages (from google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (0.22.0)
    Requirement already satisfied: google-auth-httplib2>=0.1.0 in d:\software\anaconda3\lib\site-packages (from google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (0.1.0)
    Requirement already satisfied: google-api-core!=2.0.*,!=2.1.*,!=2.2.*,!=2.3.0,<3.0.0dev,>=1.31.5 in d:\software\anaconda3\lib\site-packages (from google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (2.11.0)
    Requirement already satisfied: uritemplate<5,>=3.0.1 in d:\software\anaconda3\lib\site-packages (from google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (4.1.1)
    Requirement already satisfied: protobuf!=3.20.0,!=3.20.1,!=4.21.0,!=4.21.1,!=4.21.2,!=4.21.3,!=4.21.4,!=4.21.5,<5.0.0dev,>=3.19.5 in d:\software\anaconda3\lib\site-packages (from google-api-core!=2.0.*,!=2.1.*,!=2.2.*,!=2.3.0,<3.0.0dev,>=1.31.5->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (4.23.1)
    Requirement already satisfied: requests<3.0.0dev,>=2.18.0 in d:\software\anaconda3\lib\site-packages (from google-api-core!=2.0.*,!=2.1.*,!=2.2.*,!=2.3.0,<3.0.0dev,>=1.31.5->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (2.26.0)
    Requirement already satisfied: googleapis-common-protos<2.0dev,>=1.56.2 in d:\software\anaconda3\lib\site-packages (from google-api-core!=2.0.*,!=2.1.*,!=2.2.*,!=2.3.0,<3.0.0dev,>=1.31.5->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (1.59.0)
    Requirement already satisfied: cachetools<6.0,>=2.0.0 in d:\software\anaconda3\lib\site-packages (from google-auth<3.0.0dev,>=1.19.0->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (5.3.0)
    Requirement already satisfied: pyasn1-modules>=0.2.1 in d:\software\anaconda3\lib\site-packages (from google-auth<3.0.0dev,>=1.19.0->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (0.3.0)
    Requirement already satisfied: rsa<5,>=3.1.4 in d:\software\anaconda3\lib\site-packages (from google-auth<3.0.0dev,>=1.19.0->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (4.9)
    Requirement already satisfied: google-cloud-core<3.0.0dev,>=1.6.0 in d:\software\anaconda3\lib\site-packages (from google-cloud-bigquery>=0.31.0->tf-models-official==2.3.0->tflite-model-maker) (2.3.2)
    Requirement already satisfied: python-dateutil<3.0dev,>=2.7.2 in d:\software\anaconda3\lib\site-packages (from google-cloud-bigquery>=0.31.0->tf-models-official==2.3.0->tflite-model-maker) (2.8.2)
    Requirement already satisfied: proto-plus<2.0.0dev,>=1.15.0 in d:\software\anaconda3\lib\site-packages (from google-cloud-bigquery>=0.31.0->tf-models-official==2.3.0->tflite-model-maker) (1.22.2)
    Requirement already satisfied: google-resumable-media<3.0dev,>=0.6.0 in d:\software\anaconda3\lib\site-packages (from google-cloud-bigquery>=0.31.0->tf-models-official==2.3.0->tflite-model-maker) (2.5.0)
    Requirement already satisfied: grpcio<2.0dev,>=1.47.0 in d:\software\anaconda3\lib\site-packages (from google-cloud-bigquery>=0.31.0->tf-models-official==2.3.0->tflite-model-maker) (1.54.0)
    Requirement already satisfied: grpcio-status<2.0dev,>=1.33.2 in d:\software\anaconda3\lib\site-packages (from google-api-core!=2.0.*,!=2.1.*,!=2.2.*,!=2.3.0,<3.0.0dev,>=1.31.5->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (1.54.0)
    Requirement already satisfied: google-crc32c<2.0dev,>=1.0 in d:\software\anaconda3\lib\site-packages (from google-resumable-media<3.0dev,>=0.6.0->google-cloud-bigquery>=0.31.0->tf-models-official==2.3.0->tflite-model-maker) (1.5.0)
    Requirement already satisfied: pyparsing!=3.0.0,!=3.0.1,!=3.0.2,!=3.0.3,<4,>=2.4.2 in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from httplib2<1dev,>=0.15.0->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (2.4.7)
    Requirement already satisfied: tqdm in d:\software\anaconda3\lib\site-packages (from kaggle>=1.3.9->tf-models-official==2.3.0->tflite-model-maker) (4.62.3)
    Requirement already satisfied: certifi in d:\software\anaconda3\lib\site-packages (from kaggle>=1.3.9->tf-models-official==2.3.0->tflite-model-maker) (2021.10.8)
    Requirement already satisfied: python-slugify in d:\software\anaconda3\lib\site-packages (from kaggle>=1.3.9->tf-models-official==2.3.0->tflite-model-maker) (5.0.2)
    Requirement already satisfied: kiwisolver>=1.0.1 in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from matplotlib<3.5.0,>=3.0.3->tflite-model-maker) (1.3.1)
    Requirement already satisfied: cycler>=0.10 in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from matplotlib<3.5.0,>=3.0.3->tflite-model-maker) (0.10.0)
    Requirement already satisfied: attrs in d:\software\anaconda3\lib\site-packages (from neural-structured-learning>=1.3.1->tflite-model-maker) (21.2.0)
    Requirement already satisfied: pytz>=2017.3 in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from pandas>=0.22.0->tf-models-official==2.3.0->tflite-model-maker) (2021.1)
    Requirement already satisfied: platformdirs>=2.5.0 in d:\software\anaconda3\lib\site-packages (from pooch>=1.0->librosa==0.8.1->tflite-model-maker) (3.5.1)
    Requirement already satisfied: pyasn1<0.6.0,>=0.4.6 in d:\software\anaconda3\lib\site-packages (from pyasn1-modules>=0.2.1->google-auth<3.0.0dev,>=1.19.0->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (0.5.0)
    Requirement already satisfied: charset-normalizer~=2.0.0 in d:\software\anaconda3\lib\site-packages (from requests<3.0.0dev,>=2.18.0->google-api-core!=2.0.*,!=2.1.*,!=2.2.*,!=2.3.0,<3.0.0dev,>=1.31.5->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (2.0.4)
    Requirement already satisfied: idna<4,>=2.5 in d:\software\anaconda3\lib\site-packages (from requests<3.0.0dev,>=2.18.0->google-api-core!=2.0.*,!=2.1.*,!=2.2.*,!=2.3.0,<3.0.0dev,>=1.31.5->google-api-python-client>=1.6.7->tf-models-official==2.3.0->tflite-model-maker) (3.2)
    Requirement already satisfied: threadpoolctl>=2.0.0 in d:\software\anaconda3\lib\site-packages (from scikit-learn!=0.19.0,>=0.14.0->librosa==0.8.1->tflite-model-maker) (2.2.0)
    Requirement already satisfied: cffi>=1.0 in d:\software\anaconda3\lib\site-packages (from soundfile>=0.10.2->librosa==0.8.1->tflite-model-maker) (1.14.6)
    Requirement already satisfied: pycparser in d:\software\anaconda3\lib\site-packages (from cffi>=1.0->soundfile>=0.10.2->librosa==0.8.1->tflite-model-maker) (2.20)
    Requirement already satisfied: wrapt>=1.11.0 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (1.12.1)
    Requirement already satisfied: keras<2.10.0,>=2.9.0rc0 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (2.9.0)
    Requirement already satisfied: h5py>=2.9.0 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (3.2.1)
    Requirement already satisfied: astunparse>=1.6.0 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (1.6.3)
    Requirement already satisfied: opt-einsum>=2.3.2 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (3.3.0)
    Requirement already satisfied: tensorflow-estimator<2.10.0,>=2.9.0rc0 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (2.9.0)
    Requirement already satisfied: typing-extensions>=3.6.6 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (3.10.0.2)
    Requirement already satisfied: keras-preprocessing>=1.1.1 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (1.1.2)
    Requirement already satisfied: gast<=0.4.0,>=0.2.1 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (0.4.0)
    Requirement already satisfied: libclang>=13.0.0 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (16.0.0)
    Requirement already satisfied: tensorflow-io-gcs-filesystem>=0.23.1 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (0.31.0)
    Requirement already satisfied: google-pasta>=0.1.1 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (0.2.0)
    Requirement already satisfied: tensorboard<2.10,>=2.9 in d:\software\anaconda3\lib\site-packages (from tensorflow>=2.6.0->tflite-model-maker) (2.9.0)
    Requirement already satisfied: wheel<1.0,>=0.23.0 in d:\software\anaconda3\lib\site-packages (from astunparse>=1.6.0->tensorflow>=2.6.0->tflite-model-maker) (0.37.0)
    Requirement already satisfied: google-auth-oauthlib<0.5,>=0.4.1 in d:\software\anaconda3\lib\site-packages (from tensorboard<2.10,>=2.9->tensorflow>=2.6.0->tflite-model-maker) (0.4.6)
    Requirement already satisfied: tensorboard-plugin-wit>=1.6.0 in d:\software\anaconda3\lib\site-packages (from tensorboard<2.10,>=2.9->tensorflow>=2.6.0->tflite-model-maker) (1.8.1)
    Requirement already satisfied: tensorboard-data-server<0.7.0,>=0.6.0 in d:\software\anaconda3\lib\site-packages (from tensorboard<2.10,>=2.9->tensorflow>=2.6.0->tflite-model-maker) (0.6.1)
    Requirement already satisfied: markdown>=2.6.8 in d:\software\anaconda3\lib\site-packages (from tensorboard<2.10,>=2.9->tensorflow>=2.6.0->tflite-model-maker) (3.4.3)
    Requirement already satisfied: werkzeug>=1.0.1 in d:\software\anaconda3\lib\site-packages (from tensorboard<2.10,>=2.9->tensorflow>=2.6.0->tflite-model-maker) (2.0.2)
    Requirement already satisfied: requests-oauthlib>=0.7.0 in d:\software\anaconda3\lib\site-packages (from google-auth-oauthlib<0.5,>=0.4.1->tensorboard<2.10,>=2.9->tensorflow>=2.6.0->tflite-model-maker) (1.3.1)
    Requirement already satisfied: importlib-metadata>=4.4 in d:\software\anaconda3\lib\site-packages (from markdown>=2.6.8->tensorboard<2.10,>=2.9->tensorflow>=2.6.0->tflite-model-maker) (4.8.1)
    Requirement already satisfied: zipp>=0.5 in d:\software\anaconda3\lib\site-packages (from importlib-metadata>=4.4->markdown>=2.6.8->tensorboard<2.10,>=2.9->tensorflow>=2.6.0->tflite-model-maker) (3.6.0)
    Requirement already satisfied: oauthlib>=3.0.0 in d:\software\anaconda3\lib\site-packages (from requests-oauthlib>=0.7.0->google-auth-oauthlib<0.5,>=0.4.1->tensorboard<2.10,>=2.9->tensorflow>=2.6.0->tflite-model-maker) (3.2.2)
    Requirement already satisfied: typeguard<3.0.0,>=2.7 in d:\software\anaconda3\lib\site-packages (from tensorflow-addons>=0.11.2->tflite-model-maker) (2.13.3)
    Requirement already satisfied: etils[enp,epath]>=0.9.0 in d:\software\anaconda3\lib\site-packages (from tensorflow-datasets>=2.1.0->tflite-model-maker) (1.2.0)
    Requirement already satisfied: tensorflow-metadata in d:\software\anaconda3\lib\site-packages (from tensorflow-datasets>=2.1.0->tflite-model-maker) (1.13.1)
    Requirement already satisfied: array-record in d:\software\anaconda3\lib\site-packages (from tensorflow-datasets>=2.1.0->tflite-model-maker) (0.2.0)
    Requirement already satisfied: toml in d:\software\anaconda3\lib\site-packages (from tensorflow-datasets>=2.1.0->tflite-model-maker) (0.10.2)
    Requirement already satisfied: promise in d:\software\anaconda3\lib\site-packages (from tensorflow-datasets>=2.1.0->tflite-model-maker) (2.3)
    Requirement already satisfied: click in d:\software\anaconda3\lib\site-packages (from tensorflow-datasets>=2.1.0->tflite-model-maker) (8.0.3)
    Requirement already satisfied: dm-tree in d:\software\anaconda3\lib\site-packages (from tensorflow-datasets>=2.1.0->tflite-model-maker) (0.1.8)
    Requirement already satisfied: importlib_resources in d:\software\anaconda3\lib\site-packages (from etils[enp,epath]>=0.9.0->tensorflow-datasets>=2.1.0->tflite-model-maker) (5.12.0)
    Requirement already satisfied: sounddevice>=0.4.4 in d:\software\anaconda3\lib\site-packages (from tflite-support>=0.3.1->tflite-model-maker) (0.4.6)
    Requirement already satisfied: pybind11>=2.6.0 in d:\software\anaconda3\lib\site-packages (from tflite-support>=0.3.1->tflite-model-maker) (2.10.4)
    Requirement already satisfied: colorama in d:\software\anaconda3\lib\site-packages (from click->tensorflow-datasets>=2.1.0->tflite-model-maker) (0.4.4)
    Requirement already satisfied: text-unidecode>=1.3 in d:\software\anaconda3\lib\site-packages (from python-slugify->kaggle>=1.3.9->tf-models-official==2.3.0->tflite-model-maker) (1.3)
    Requirement already satisfied: conda-repo-cli==1.0.4 in d:\software\anaconda3\lib\site-packages (1.0.4)
    Requirement already satisfied: clyent>=1.2.0 in d:\software\anaconda3\lib\site-packages (from conda-repo-cli==1.0.4) (1.2.2)
    Requirement already satisfied: six in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from conda-repo-cli==1.0.4) (1.16.0)
    Requirement already satisfied: requests>=2.9.1 in d:\software\anaconda3\lib\site-packages (from conda-repo-cli==1.0.4) (2.26.0)
    Requirement already satisfied: nbformat>=4.4.0 in d:\software\anaconda3\lib\site-packages (from conda-repo-cli==1.0.4) (5.1.3)
    Requirement already satisfied: pytz in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from conda-repo-cli==1.0.4) (2021.1)
    Requirement already satisfied: PyYAML>=3.12 in d:\software\anaconda3\lib\site-packages (from conda-repo-cli==1.0.4) (6.0)
    Requirement already satisfied: python-dateutil>=2.6.1 in d:\software\anaconda3\lib\site-packages (from conda-repo-cli==1.0.4) (2.8.2)
    
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)


​    
​    Requirement already satisfied: setuptools in d:\software\anaconda3\lib\site-packages (from conda-repo-cli==1.0.4) (58.0.4)
​    Requirement already satisfied: pathlib in d:\software\anaconda3\lib\site-packages (from conda-repo-cli==1.0.4) (1.0.1)
​    Requirement already satisfied: jupyter-core in d:\software\anaconda3\lib\site-packages (from nbformat>=4.4.0->conda-repo-cli==1.0.4) (4.8.1)
​    Requirement already satisfied: jsonschema!=2.5.0,>=2.4 in d:\software\anaconda3\lib\site-packages (from nbformat>=4.4.0->conda-repo-cli==1.0.4) (3.2.0)
​    Requirement already satisfied: traitlets>=4.1 in d:\software\anaconda3\lib\site-packages (from nbformat>=4.4.0->conda-repo-cli==1.0.4) (5.1.0)
​    Requirement already satisfied: ipython-genutils in d:\software\anaconda3\lib\site-packages (from nbformat>=4.4.0->conda-repo-cli==1.0.4) (0.2.0)
​    Requirement already satisfied: attrs>=17.4.0 in d:\software\anaconda3\lib\site-packages (from jsonschema!=2.5.0,>=2.4->nbformat>=4.4.0->conda-repo-cli==1.0.4) (21.2.0)
​    Requirement already satisfied: pyrsistent>=0.14.0 in d:\software\anaconda3\lib\site-packages (from jsonschema!=2.5.0,>=2.4->nbformat>=4.4.0->conda-repo-cli==1.0.4) (0.18.0)
​    Requirement already satisfied: idna<4,>=2.5 in d:\software\anaconda3\lib\site-packages (from requests>=2.9.1->conda-repo-cli==1.0.4) (3.2)
​    Requirement already satisfied: urllib3<1.27,>=1.21.1 in d:\software\anaconda3\lib\site-packages (from requests>=2.9.1->conda-repo-cli==1.0.4) (1.25.11)
​    Requirement already satisfied: charset-normalizer~=2.0.0 in d:\software\anaconda3\lib\site-packages (from requests>=2.9.1->conda-repo-cli==1.0.4) (2.0.4)
​    Requirement already satisfied: certifi>=2017.4.17 in d:\software\anaconda3\lib\site-packages (from requests>=2.9.1->conda-repo-cli==1.0.4) (2021.10.8)
​    Requirement already satisfied: pywin32>=1.0 in d:\software\anaconda3\lib\site-packages (from jupyter-core->nbformat>=4.4.0->conda-repo-cli==1.0.4) (228)



```python
!pip install anaconda-project==0.10.1
```

    Requirement already satisfied: anaconda-project==0.10.1 in d:\software\anaconda3\lib\site-packages (0.10.1)
    Requirement already satisfied: tornado>=4.2 in d:\software\anaconda3\lib\site-packages (from anaconda-project==0.10.1) (6.1)
    Requirement already satisfied: ruamel-yaml in d:\software\anaconda3\lib\site-packages (from anaconda-project==0.10.1) (0.17.26)
    Requirement already satisfied: requests in d:\software\anaconda3\lib\site-packages (from anaconda-project==0.10.1) (2.26.0)
    Requirement already satisfied: anaconda-client in d:\software\anaconda3\lib\site-packages (from anaconda-project==0.10.1) (1.9.0)
    Requirement already satisfied: conda-pack in d:\software\anaconda3\lib\site-packages (from anaconda-project==0.10.1) (0.6.0)
    Requirement already satisfied: jinja2 in d:\software\anaconda3\lib\site-packages (from anaconda-project==0.10.1) (2.11.3)
    Requirement already satisfied: nbformat>=4.4.0 in d:\software\anaconda3\lib\site-packages (from anaconda-client->anaconda-project==0.10.1) (5.1.3)
    Requirement already satisfied: PyYAML>=3.12 in d:\software\anaconda3\lib\site-packages (from anaconda-client->anaconda-project==0.10.1) (6.0)
    Requirement already satisfied: clyent>=1.2.0 in d:\software\anaconda3\lib\site-packages (from anaconda-client->anaconda-project==0.10.1) (1.2.2)
    Requirement already satisfied: setuptools in d:\software\anaconda3\lib\site-packages (from anaconda-client->anaconda-project==0.10.1) (58.0.4)
    Requirement already satisfied: pytz in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from anaconda-client->anaconda-project==0.10.1) (2021.1)
    Requirement already satisfied: python-dateutil>=2.6.1 in d:\software\anaconda3\lib\site-packages (from anaconda-client->anaconda-project==0.10.1) (2.8.2)
    Requirement already satisfied: six in c:\users\lenovo\appdata\roaming\python\python39\site-packages (from anaconda-client->anaconda-project==0.10.1) (1.16.0)
    Requirement already satisfied: jupyter-core in d:\software\anaconda3\lib\site-packages (from nbformat>=4.4.0->anaconda-client->anaconda-project==0.10.1) (4.8.1)
    Requirement already satisfied: jsonschema!=2.5.0,>=2.4 in d:\software\anaconda3\lib\site-packages (from nbformat>=4.4.0->anaconda-client->anaconda-project==0.10.1) (3.2.0)
    Requirement already satisfied: ipython-genutils in d:\software\anaconda3\lib\site-packages (from nbformat>=4.4.0->anaconda-client->anaconda-project==0.10.1) (0.2.0)
    Requirement already satisfied: traitlets>=4.1 in d:\software\anaconda3\lib\site-packages (from nbformat>=4.4.0->anaconda-client->anaconda-project==0.10.1) (5.1.0)
    Requirement already satisfied: pyrsistent>=0.14.0 in d:\software\anaconda3\lib\site-packages (from jsonschema!=2.5.0,>=2.4->nbformat>=4.4.0->anaconda-client->anaconda-project==0.10.1) (0.18.0)
    Requirement already satisfied: attrs>=17.4.0 in d:\software\anaconda3\lib\site-packages (from jsonschema!=2.5.0,>=2.4->nbformat>=4.4.0->anaconda-client->anaconda-project==0.10.1) (21.2.0)
    Requirement already satisfied: charset-normalizer~=2.0.0 in d:\software\anaconda3\lib\site-packages (from requests->anaconda-project==0.10.1) (2.0.4)
    Requirement already satisfied: certifi>=2017.4.17 in d:\software\anaconda3\lib\site-packages (from requests->anaconda-project==0.10.1) (2021.10.8)
    Requirement already satisfied: idna<4,>=2.5 in d:\software\anaconda3\lib\site-packages (from requests->anaconda-project==0.10.1) (3.2)
    Requirement already satisfied: urllib3<1.27,>=1.21.1 in d:\software\anaconda3\lib\site-packages (from requests->anaconda-project==0.10.1) (1.25.11)
    Requirement already satisfied: MarkupSafe>=0.23 in d:\software\anaconda3\lib\site-packages (from jinja2->anaconda-project==0.10.1) (1.1.1)
    Requirement already satisfied: pywin32>=1.0 in d:\software\anaconda3\lib\site-packages (from jupyter-core->nbformat>=4.4.0->anaconda-client->anaconda-project==0.10.1) (228)
    Requirement already satisfied: ruamel.yaml.clib>=0.2.7 in d:\software\anaconda3\lib\site-packages (from ruamel-yaml->anaconda-project==0.10.1) (0.2.7)


    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)
    WARNING: Ignoring invalid distribution -rotobuf (d:\software\anaconda3\lib\site-packages)


## 导入相关类库


```python
import os

import numpy as np

import tensorflow as tf
assert tf.__version__.startswith('2') # 确定导入的tf的版本是2.x版本，否则会报出AssertionError 异常

from tflite_model_maker import model_spec
from tflite_model_maker import image_classifier
from tflite_model_maker.config import ExportFormat
from tflite_model_maker.config import QuantizationConfig
from tflite_model_maker.image_classifier import DataLoader

import matplotlib.pyplot as plt
```

    d:\software\Anaconda3\lib\site-packages\tensorflow_addons\utils\tfa_eol_msg.py:23: UserWarning: 
    
    TensorFlow Addons (TFA) has ended development and introduction of new features.
    TFA has entered a minimal maintenance and release mode until a planned end of life in May 2024.
    Please modify downstream libraries to take dependencies from other repositories in our TensorFlow community (e.g. Keras, Keras-CV, and Keras-NLP). 
    
    For more information see: https://github.com/tensorflow/addons/issues/2807 
    
      warnings.warn(
    d:\software\Anaconda3\lib\site-packages\tensorflow_addons\utils\ensure_tf_install.py:53: UserWarning: Tensorflow Addons supports using Python ops for all Tensorflow versions above or equal to 2.10.0 and strictly below 2.13.0 (nightly versions are not supported). 
     The versions of TensorFlow you are currently using is 2.9.0 and is not supported. 
    Some things might work, some things might not.
    If you were to encounter a bug, do not file an issue.
    If you want to make sure you're using a tested and supported configuration, either change the TensorFlow version or the TensorFlow Addons's version. 
    You can find the compatibility matrix in TensorFlow Addon's readme:
    https://github.com/tensorflow/addons
      warnings.warn(

## 进行模型训练和测试

```python
image_path = tf.keras.utils.get_file(
      'flower_photos.tgz',
      'https://storage.googleapis.com/download.tensorflow.org/example_images/flower_photos.tgz',
      extract=True)
image_path = os.path.join(os.path.dirname(image_path), 'flower_photos')

```


```python
data = DataLoader.from_folder(image_path)
train_data, test_data = data.split(0.9)
```

    INFO:tensorflow:Load image with size: 3670, num_label: 5, labels: daisy, dandelion, roses, sunflowers, tulips.



```python
# 出现超时解决方案
inception_v3_spec = image_classifier.ModelSpec(uri='https://storage.googleapis.com/tfhub-modules/tensorflow/efficientnet/lite0/feature-vector/2.tar.gz')
model = image_classifier.create(train_data,inception_v3_spec)
```

    INFO:tensorflow:Retraining the models...
    Model: "sequential"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     hub_keras_layer_v1v2 (HubKe  (None, 1280)             3413024   
     rasLayerV1V2)                                                   
                                                                     
     dropout (Dropout)           (None, 1280)              0         
                                                                     
     dense (Dense)               (None, 5)                 6405      
                                                                     
    =================================================================
    Total params: 3,419,429
    Trainable params: 6,405
    Non-trainable params: 3,413,024
    _________________________________________________________________
    None
    Epoch 1/5


    d:\software\Anaconda3\lib\site-packages\keras\optimizers\optimizer_v2\gradient_descent.py:108: UserWarning: The `lr` argument is deprecated, use `learning_rate` instead.
      super(SGD, self).__init__(name, **kwargs)


    103/103 [==============================] - 54s 508ms/step - loss: 0.8353 - accuracy: 0.7937
    Epoch 2/5
    103/103 [==============================] - 53s 516ms/step - loss: 0.6512 - accuracy: 0.8999
    Epoch 3/5
    103/103 [==============================] - 56s 545ms/step - loss: 0.6193 - accuracy: 0.9147
    Epoch 4/5
    103/103 [==============================] - 52s 502ms/step - loss: 0.6006 - accuracy: 0.9251
    Epoch 5/5
    103/103 [==============================] - 51s 491ms/step - loss: 0.5876 - accuracy: 0.9351



```python
loss, accuracy = model.evaluate(test_data)
```

    12/12 [==============================] - 7s 455ms/step - loss: 0.6585 - accuracy: 0.8910



```python
model.export(export_dir='.') # 保存
```

    INFO:tensorflow:Assets written to: C:\Users\lenovo\AppData\Local\Temp\tmp2kjeerb2\assets


    INFO:tensorflow:Assets written to: C:\Users\lenovo\AppData\Local\Temp\tmp2kjeerb2\assets
    d:\software\Anaconda3\lib\site-packages\tensorflow\lite\python\convert.py:766: UserWarning: Statistics for quantized inputs were expected, but not specified; continuing anyway.
      warnings.warn("Statistics for quantized inputs were expected, but not "


    INFO:tensorflow:Label file is inside the TFLite model with metadata.


    INFO:tensorflow:Label file is inside the TFLite model with metadata.


    INFO:tensorflow:Saving labels in C:\Users\lenovo\AppData\Local\Temp\tmpncq984hw\labels.txt


    INFO:tensorflow:Saving labels in C:\Users\lenovo\AppData\Local\Temp\tmpncq984hw\labels.txt


    INFO:tensorflow:TensorFlow Lite model exported successfully: .\model.tflite


    INFO:tensorflow:TensorFlow Lite model exported successfully: .\model.tflite

![image-20230519105217956](./img/image-20230519105217956.png)



## 遇到的问题以及我的解决方案

### 安装 tflite-model-maker遇到的问题以及解决方案
1. 网络延时问题，出现timeout等字

+ 解决方案使用镜像源，但是使用校园网下载时间依然需要3-4h，命令如下：

```
pip install pywinauto -i http://pypi.douban.com/simple 
```

​	   以下推荐几个镜像

```
1)http://mirrors.aliyun.com/pypi/simple/ 阿里云
2)https://pypi.mirrors.ustc.edu.cn/simple/ 中国科技大学
3) http://pypi.douban.com/simple/ 豆瓣
4) https://pypi.tuna.tsinghua.edu.cn/simple/ 清华大学
5) http://pypi.mirrors.ustc.edu.cn/simple/ 中国科学技术大学
```

2. 出现类似ERROR: Cannot uninstall 'llvmlite'. It is a distutils installed project.

+ 产生的原因：要下载新版文件包，但是使用简单的uninstall命令不可以删除旧版的包，故要暴力删除

+ 解决方案：到anaconda安装目录下找到Lib的site-packages,在里面删除相应的xx**.egg-info**文件，这里是**llvmlite-0.23.1-py3.6.egg-info**

![image-20230518235933080](./img/image-20230518235933080.png)

3. check_hostname requires server_hostname类问题

+ 解决方案：**别用梯子！别用梯子！别用梯子！**

4. 出现Could not fetch URL https://pypi.xxx/simple/pip/

+ 解决方案：在命令后面加上， --trusted-host pypi.douban.com

```
pip install pywinauto -i http://pypi.douban.com/simple  --trusted-host pypi.douban.com
```



### 导入相关类库时遇到的问题，以及解决方案

1. 出现Descriptors cannot not be created directly

+ 报错内容如下

```
TypeError: Descriptors cannot not be created directly.
If this call came from a _pb2.py file, your generated code is out of date and must be regenerated with protoc >= 3.19.0.
If you cannot immediately regenerate your protos, some other possible workarounds are:
 1. Downgrade the protobuf package to 3.20.x or lower.
 2. Set PROTOCOL_BUFFERS_PYTHON_IMPLEMENTATION=python (but this will use pure-Python parsing and will be much slower).
```

+ 原因： 出现这个问题的主要原因是protobuf版本不匹配。

+ 解决方案：安装3.20.1的protobuf

![image-20230519001308973](./img/image-20230519001308973.png)

### tf生成模型的时候遇到的问题以及解决方案

1. 网络延迟问题，类似timeout等字样

+ 解决方案：

​		修改以下代码：

修改前

```
model = image_classifier.create(train_data）
```

修改后：

```
# 出现超时解决方案
inception_v3_spec = image_classifier.ModelSpec(uri='https://storage.googleapis.com/tfhub-modules/tensorflow/efficientnet/lite0/feature-vector/2.tar.gz')
model = image_classifier.create(train_data,inception_v3_spec)
```





