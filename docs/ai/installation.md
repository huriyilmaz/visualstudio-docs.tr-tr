---
title: AI Araçlarını Yükleme
description: Visual Studio için AI Araçlarının nasıl yük Visual Studio
keywords: ai, visual studio
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 5e8867064e4392cdbf3c2dbc72810ddf22f0cded
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633374"
---
# <a name="installation"></a>Yükleme

Visual Studio Araçları 64 bit işletim sistemlerine Windows için kullanılabilir.

## <a name="install-visual-studio-tools-for-ai"></a>AI Visual Studio Araçları yükleme

Bu uzantı, Visual Studio 2015 ve Visual Studio 2017, Community veya daha yeni sürümlerle çalışır.

Araçları marketten veya Visual Studio [marketten](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017)Visual Studio:

1. Araç **Uzantıları**  >  **ve Güncelleştirmeler'i seçin.**

   ![Visual Studio'deki Uzantılar ve Güncelleştirmeler menüsü](media/installation/extensions.png)

2. Uzantılar **ve Güncelleştirmeler** iletişim kutusunda, **sol taraftan** Çevrimiçi'yi seçin.
3. Sağ üst köşedeki arama kutusuna "ai araçları" yazın veya girin.
4. Sonuçlardan **Visual Studio Araçları için AI'yi** seçin.
5. **İndir**'i seçin.

## <a name="prepare-your-local-machine"></a>Yerel makinenizi hazırlama
Derin öğrenme modellerini yerel bilgisayarınızda eğitmeden önce, geçerli önkoşulların yüklü olduğundan emin olun. Buna NVIDIA GPU'nız (varsa) için en son sürücülere ve kitaplıklara sahip olduğundan emin olun. Ayrıca NumPy, SciPy gibi Python ve Python kitaplıklarını ve projeniz içinde kullanmayı planlamış olduğu Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch ve Chainer gibi uygun derin öğrenme çerçevelerini de yüklemiş olduğundan emin olursunuz.

> [!NOTE]
> Aşağıdaki alt bölümlerde yer alan yazılım tanıtımı, giriş sayfalarından alıntılandı.

### <a name="nvidia-gpu-driver"></a>NVIDIA GPU sürücüsü

Derin öğrenme çerçeveleri, makinelerin hızla, doğrulukla öğrenmesine ve gerçek yapay zekaya doğru ölçeklendirerek NVIDIA GPU'nun avantajını kullanır. Bilgisayarınızda NVIDIA GPU kartları varsa NVIDIA Sürücü [İndirmeleri'ne bakın](https://www.nvidia.com/Download/index.aspx) veya en son sürücüyü yüklemek için bir işletim sistemi güncelleştirmesi deneyin.

### <a name="cuda"></a>CUDA

[CUDA,](https://developer.nvidia.com/cuda-zone) NVIDIA tarafından bir paralel bilgi işlem platformu ve programlama modelidir. GPU'nun gücüyle işlem performansında önemli artışlar sağlar. Şu anda derin öğrenme çerçeveleri CUDA Toolkit 8.0'a ihtiyaçmektedir.

CUDA'yı yüklemek için

- Bu [siteyi ziyaret](https://developer.nvidia.com/cuda-80-ga2-download-archive)edin, CUDA'yı indirin ve yükleyin.
- CUDA çalışma zamanı kitaplıklarını yükleyin ve ardından %PATH% veya $Path ortam değişkenine CUDA ikili yolunu ekleyin.
- Bu Windows yol varsayılan olarak "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin" şeklindedir.

![CuDA'yı Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (CUDA Derin Sinir Ağı kitaplığı), NVIDIA tarafından derin sinir ağları için GPU hızlandırmalı temel öğeler kitaplığıdır. cuDNN v6, en son derin öğrenme çerçeveleri için gereklidir.

cuDNN yüklemek için:

- En son paketi indirip yüklemek için [NVIDIA](https://developer.nvidia.com/rdp/cudnn-download) Developer'ı ziyaret edin.
- cuDNN ikilisi içeren dizini %PATH% veya $Path emin olun.
- Bu Windows" cudnn64_6.dll "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin" dizinine kopyalayabiliyoruz.

> [!NOTE]
> CNTK 2.0 ve TensorFlow 1.2.1 gibi önceki derin öğrenme çerçevelerine cuDNN v5.1 gerekir. Ancak, birden çok cuDNN sürümünü birlikte yükleyebilirsiniz.

### <a name="python"></a>Python

Python, derin öğrenme uygulamaları için birincil programlama dilidir. **64 bit** Python dağıtımı gereklidir ve en iyi [uyumluluk için Python 3.5.4](https://www.python.org/downloads/release/python-354/) önerilir.

### <a name="to-install-python-on-windows"></a>Python'i Windows

- Python başlatıcısını yalnızca kendiniz yüklemenizi ve Python'u %PATH% ortam değişkenine eklemenizi öneririz.
- Python'da yazılmış yazılım paketlerini yüklemek paket yönetim sistemi yönetmek için gerekli olan pip'i yükleyebilirsiniz.

Derin öğrenme çerçeveleri kendi yüklemeleri için pip'i temel almaktadır.

![Windows üzerinde Python’ı yükleme](media/installation/install_python_win.png)

Ardından Python 3.5'in doğru yük olup olmadığını doğrulamamız ve terminalde aşağıdaki komutları yürüterek pip'i en son sürüme yükseltmemiz gerekir:

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **macOS**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Visual Studio üzerinde Python

Python, uzantılar aracılığıyla Visual Studio tam olarak de destekler.
Daha fazla bilgi için [Python'Visual Studio Araçları](../python/installing-python-support-in-visual-studio.md) yükleme hakkında daha fazla bilgi edinebilirsiniz.

### <a name="numpy-and-scipy"></a>NumPy ve SciPy

- **NumPy,** küçük çok boyutlu diziler için çok fazla hızdan ödün vermeden rastgele kayıtların büyük çok boyutlu dizilerini verimli bir şekilde işlemek için tasarlanmış genel amaçlı bir dizi işleme paketidir.

- **SciPy** ("Sigh Pie" olarak okunur), NumPy'ye bağlı olarak matematik, bilim ve mühendislik için açık kaynak bir yazılımdır. Sürüm 1.0.0'dan başlayarak, SciPy'nin artık yeni sürümler için önceden oluşturulmuş resmi Windows.

NumPy ve SciPy'yi yüklemek için terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Yukarıdaki komut, mevcut eski veya resmi olmayan (örneğin, Windows için üçüncü taraf http://www.lfd.uci.edu/~gohlke/pythonlibs/ paketleri) NumPy ve SciPy'yi en son resmi sürümlere yükseltmektedir.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

Bu [Microsoft Cognitive Toolkit,](https://cntk.ai) sinir ağlarını yönlendiren bir grafik aracılığıyla bir dizi hesaplama adımı olarak tanımlayan birleşik bir derin öğrenme araç setidir. CNTK Python ve BrainScript programlama dillerini destekler.

> [!NOTE]
> CNTK macOS'u desteklemez.

Python CNTK yüklemek için [bkz.](/cognitive-toolkit/Setup-CNTK-on-your-machine)CNTK.

### <a name="tensorflow"></a>TensorFlow

[TensorFlow,](https://www.tensorflow.org/) veri akışı grafiklerini kullanarak sayısal hesaplamaya yönelik bir açık kaynak yazılım kitaplığıdır. Ayrıntılı yükleme [için](https://www.tensorflow.org/install/) buraya bakın.

> [!NOTE]
> Sürüm 1.2'den sonra TensorFlow artık macOS için GPU desteğine sahip değildir.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) hafif, modüler ve ölçeklenebilir bir derin öğrenme çerçevesidir. Caffe2, özgün Caffe'nin üzerine inşa edildiklerinde ifade, hız ve modülerlik ile tasarlanmıştır.

Şu anda önceden oluşturulmuş Caffe2 python tekerlek paketi yoktur.

Kaynak [kodundan](https://caffe2.ai/docs/getting-started.html) derlemek için buraya ziyaret edin.

### <a name="mxnet"></a>MXNet

[Apache MXNet (incubating),](https://mxnet.incubator.apache.org/) hem verimlilik hem de esneklik için tasarlanmış bir derin öğrenme çerçevesidir. Verimliliği ve üretkenliği **en üst** [düzeye çıkarmak için sembolik ve](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) koruyucu programlamayı karıştırmanıza olanak sağlar.

MXNet'i yüklemek için terminalde aşağıdaki komutu çalıştırın:

- GPU ile

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- GPU olmadan

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras,](https://keras.io/) Python'da yazılmış ve CNTK, TensorFlow veya Theano üzerinde çalıştırabilen üst düzey bir sinir ağları API'dir. Hızlı denemeyi etkinleştirmeye odaklanarak geliştirilmiştir. Mümkün olan en az gecikmeyle fikirden sonuç elde etmek, iyi bir araştırma yapmak için çok önemli.

Keras'ı yüklemek için terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano,](http://deeplearning.net/software/theano/) çok boyutlu dizileri içeren matematiksel ifadeleri verimli bir şekilde tanımlamanızı, iyileştirmenizi ve değerlendirmenizi sağlayan bir Python kitaplığıdır.

Theano'yu yüklemek için terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch,](https://pytorch.org/) iki üst düzey özellik sağlayan bir Python paketidir:

- Güçlü GPU hızlandırmalı tensor hesaplaması (numpy gibi)
- Bant tabanlı bir otomatik derecelendirme sistemi üzerinde yerleşik Derin Sinir Ağları

PyTorch'ı yüklemek için terminalde aşağıdaki komutu çalıştırın:

- **Windows**

  Henüz resmi bir tekerlek paketi yoktur. [Anaconda](https://anaconda.org/pytorch/repo?type=all) veya California Üniversitesi'nden bir üçüncü taraf [paketi indirebilirsiniz.](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch)

  - Bunu giriş dizininize,örneğin, *C:\Users\test\pytorch dizinine sıkıştırabilirsiniz.*
  - %PYTHONPATH% *ortam değişkenine C:\Users\test\pytorch\Lib\site-packages* ekleyin.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **macOS**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > macOS ikilileri CUDA'yı desteklemez, CUDA gerekirse kaynaktan yükleyin

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Bu tek paket hem GPU hem de CPU'yu destekler.

Son olarak, özel olmayan bir Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer,](https://chainer.org/) esnekliği hedef alan Python tabanlı bir derin öğrenme çerçevesidir. Nöral ağları oluşturmak ve eğitmek için tek tek tanımlama yaklaşımına (dinamik hesaplama grafları olarak da bilinir) ve nesne odaklı üst düzey API'lere dayalı otomatik ayrım API'leri sağlar.

CUDA desteğini etkinleştirmek için [CuPy'yi yükleyin:](https://github.com/cupy/cupy)

```bash
pip3.5 install cupy
```

> [!NOTE]
> Bu Windows CuPy'yi CUDA 8.0 ile derlemek için [Visual Studio](https://visualstudio.microsoft.com/) veya [Microsoft Visual C++ Derleme](https://visualstudio.microsoft.com/visual-cpp-build-tools/) Araçları'nın 2015 sürümüne ihtiyacınız vardır.

Chainer'ı yüklemek için terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install chainer==3.0.0
```
