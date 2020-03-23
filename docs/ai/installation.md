---
title: AI Araçlarını Yükleme
description: Visual Studio için AI Tools nasıl yüklenir açıklar
keywords: ai, görsel stüdyo
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: c1160c68c79dd595e82ecf761c6e441ecc906f62
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75915809"
---
# <a name="installation"></a>Yükleme

AI için Visual Studio Tools, Windows 64 bit işletim sistemlerine yüklenebilir.

## <a name="install-visual-studio-tools-for-ai"></a>AI için Visual Studio Araçları Yükleyin

Bu uzantı Visual Studio 2015 ve Visual Studio 2017, Community sürümü veya üstü ile çalışır.

Araçları [Visual Studio Marketplace'ten](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017)veya Visual Studio'dan indirebilirsiniz:

1. **Araç** > **Uzantıları ve Güncelleştirmeleri'ni**seçin.

   ![Visual Studio'da Uzantılar ve Güncellemeler menüsü](media/installation/extensions.png)

2. **Uzantılar ve Güncelleştirmeler** iletişim kutusunda, sol tarafta **Çevrimiçi'yi** seçin.
3. Sağ üst köşedeki arama kutusuna "ai için araçlar" yazın veya girin.
4. Sonuçlardan **AI için Visual Studio Tools'u** seçin.
5. **İndir'i**tıklatın.

## <a name="prepare-your-local-machine"></a>Yerel makinenizi hazırlayın

Yerel bilgisayarınızda derin öğrenme modellerini eğitmeden önce, geçerli ön koşulların yüklü olduğundan emin olun. Buna, NVIDIA GPU'nuz için en son sürücülere ve kitaplıklardan emin olmak da dahildir (varsa). Ayrıca, NumPy, SciPy gibi Python ve Python kitaplıklarını ve Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch ve Chainer gibi uygun derin öğrenme çerçevelerini de yüklediğinizden emin olun Proje.

> [!NOTE]
> Aşağıdaki alt bölümlerdeki yazılım girişi ana sayfalarından alınmıştır.

### <a name="nvidia-gpu-driver"></a>NVIDIA GPU sürücüsü

Derin öğrenme çerçeveleri, makinelerin gerçek yapay zekaya doğru bir hızda, doğrulukta ve ölçekle öğrenmelerine izin vermek için NVIDIA GPU'dan yararlanır. Bilgisayarınızda NVIDIA GPU kartları varsa, [NVIDIA Sürücü Yüklemelerine](https://www.nvidia.com/Download/index.aspx) bakın veya en son sürücüyü yüklemek için bir işletim sistemi güncelleştirmesi deneyin.

### <a name="cuda"></a>Cuda

[CUDA,](https://developer.nvidia.com/cuda-zone) NVIDIA tarafından icat edilen paralel bir bilgi işlem platformu ve programlama modelidir. GPU'nun gücünden yararlanarak bilgisayar performansında önemli artışlar sağlar. Şu anda, CUDA Toolkit 8.0 derin öğrenme çerçeveleri tarafından gereklidir.

CUDA yüklemek için

- Bu [siteyi](https://developer.nvidia.com/cuda-80-ga2-download-archive)ziyaret edin, CUDA indirin ve yükleyin.
- CUDA çalışma zamanı kitaplıklarını yüklediğinizden emin olun ve ardından %PATH% veya $Path ortam değişkenine CUDA ikili yolunu ekleyin.
- Windows'da bu yol varsayılan olarak "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin" olur.

![Windows'a CUDA yükleme](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (CUDA Deep Nöral Ağ kütüphanesi) NVIDIA tarafından derin sinir ağları için ilkel bir GPU hızlandırılmış kütüphane. cuDNN v6 en son derin öğrenme çerçeveleri tarafından gereklidir.

cuDNN yüklemek için:

- En son paketi indirmek ve yüklemek için [NVIDIA Geliştiricisini](https://developer.nvidia.com/rdp/cudnn-download) ziyaret edin.
- CuDNN ikilisini içeren dizini %PATH% veya $Path ortam değişkenine eklediğinizden emin olun.
- Windows'da cudnn64_6.dll'yi "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin" olarak kopyalayabilirsiniz.

> [!NOTE]
> CNTK 2.0 ve TensorFlow 1.2.1 gibi önceki derin öğrenme çerçevelerinin cuDNN v5.1'e ihtiyacı vardır. Ancak, birden çok cuDNN sürümlerini birlikte yükleyebilirsiniz.

### <a name="python"></a>Python

Python, derin öğrenme uygulamaları için birincil programlama dili olmuştur. **64 bit** Python dağıtımı gereklidir ve [Python 3.5.4](https://www.python.org/downloads/release/python-354/) en iyi uyumluluk için önerilir.

### <a name="to-install-python-on-windows"></a>Python'u Windows'a yüklemek için

- Python başlatıcısını yalnızca kendiniz için yüklemenizi ve Python'u %PATH% ortam değişkenine eklemenizi öneririz.
- Python'da yazılmış yazılım paketlerini yüklemek ve yönetmek için paket yönetim sistemi olan pip'i yüklemekten emin olun.

Derin öğrenme çerçeveleri kendi kurulum için pip güveniyor.

![Windows'a Python'u yükleme](media/installation/install_python_win.png)

Daha sonra Python 3.5'in doğru yüklenip yüklenmediğini doğrulamamız ve bir terminalde aşağıdaki komutları uygulayarak pip'i en son sürüme yükseltmemiz gerekir:

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **Macos**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Python Görsel Stüdyo'da

Python, Visual Studio'da uzantılar aracılığıyla tam olarak desteklenir.
Daha fazla bilgi [için Visual Studio Tools için Python'u](../python/installing-python-support-in-visual-studio.md) yükleme hakkında daha fazla bilgi edinin.

### <a name="numpy-and-scipy"></a>Sayısal ve SciPy

- **NumPy,** küçük çok boyutlu diziler için çok fazla hızdan ödün vermeden büyük çok boyutlu rasgele kayıt dizilerini verimli bir şekilde işlemek için tasarlanmış genel amaçlı bir dizi işleme paketidir.

- **SciPy** (telaffuz "Sigh Pie") matematik, bilim ve mühendislik için açık kaynak yazılım, NumPy bağlı. Sürüm 1.0.0'dan başlayarak, SciPy şimdi Windows için resmi önceden oluşturulmuş tekerlek paketi vardır.

NumPy ve SciPy'yi yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Yukarıdaki komut, varolan eski veya resmi olmayan (örneğin Windows http://www.lfd.uci.edu/~gohlke/pythonlibs/ için gelen üçüncü taraf paketleri) NumPy ve SciPy'yi en son resmi paketlere yükseltir.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Bilişsel Araç Seti (CNTK)

[Microsoft Cognitive Toolkit,](https://cntk.ai) yönlendirilmiş bir grafik aracılığıyla sinir ağlarını bir dizi hesaplama adımı olarak tanımlayan birleşik bir derin öğrenme araç setidir. CNTK hem Python hem de BrainScript programlama dillerini destekler.

> [!NOTE]
> CNTK şu anda macOS'u desteklemiyor.

CNTK Python paketini yüklemek [için CNTK'nin nasıl yüklenir olduğunu](/cognitive-toolkit/Setup-CNTK-on-your-machine)görün.

### <a name="tensorflow"></a>TensorFlow

[TensorFlow,](https://www.tensorflow.org/) veri akışı grafiklerini kullanarak sayısal hesaplama için açık kaynak kodlu bir yazılım kitaplığıdır. Ayrıntılı kurulum için [buraya](https://www.tensorflow.org/install/) bakın.

> [!NOTE]
> Sürüm 1.2 itibariyle TensorFlow artık macOS için GPU desteği sağlamaz.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) hafif, modüler ve ölçeklenebilir derin öğrenme çerçevesidir. Orijinal Caffe üzerine inşa, Caffe2 akılda ifade, hız ve modülerlik ile tasarlanmıştır.

Şu anda, önceden inşa edilmiş Caffe2 python tekerlek paketi mevcut değildir.

Kaynak koddan oluşturmak için [burayı](https://caffe2.ai/docs/getting-started.html) ziyaret edin.

### <a name="mxnet"></a>MXNet

[Apache MXNet (kuluçka)](https://mxnet.incubator.apache.org/) hem verimlilik hem de esneklik için tasarlanmış derin bir öğrenme çerçevesidir. Verimliliği ve üretkenliği en üst düzeye çıkarmak için [sembolik ve zorunlu programlamayı](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) **karıştırmanızı** sağlar.

MXNet'i yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

- GPU ile

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- GPU olmadan

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras,](https://keras.io/) Python ile yazılmış, CNTK, TensorFlow veya Theano'nun üzerinde çalışan üst düzey bir sinir ağları API'si. Hızlı deney emerek geliştirilmiştir. Mümkün olan en az gecikme ile fikirden sonuca geçebilmek iyi bir araştırma yapmanın anahtarıdır.

Keras'ı yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano,](http://deeplearning.net/software/theano/) çok boyutlu dizileri verimli bir şekilde içeren matematiksel ifadeleri tanımlamanızı, optimize etmenizi ve değerlendirmenizi sağlayan bir Python kitaplığıdır.

Theano'yu yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/) iki üst düzey özellik sağlayan bir python paketidir:

- Güçlü GPU ivmesi ile tensör hesaplaması (numpy gibi)
- Bant tabanlı otograd sistemi üzerine inşa edilmiş Derin Sinir Ağları

PyTorch'u yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

- **Windows**

  Henüz resmi bir tekerlek paketi yok. [Anaconda](https://anaconda.org/pytorch/repo?type=all) veya [University of California'dan](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch)üçüncü taraf paketi indirebilirsiniz.

  - Ev dizininize sıkıştırın, örneğin, *C:\Users\test\pytorch*.
  - %PYTHONPATH% ortam değişkenine *C:\Users\test\pytorch\Lib\site paketleri* ekleyin.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **Macos**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > macOS ikilileri CUDA'yı desteklemiyor, CUDA gerekiyorsa kaynaktan yükleyin

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Bu tek paket hem GPU hem de CPU'yu destekler.

Son olarak, Windows olmayan torchvision yükleyin:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer,](https://chainer.org/) esnekliği hedefleyen Python tabanlı bir derin öğrenme çerçevesidir. Sinir ağları oluşturmak ve eğitmek için nesne yönelimli üst düzey API'lerin yanı sıra, tanım-by-run yaklaşımına (dinamik hesaplamalı grafikler olarak da bilinir) dayalı otomatik farklılaşma API'leri sağlar.

CUDA desteğini etkinleştirmek için [CuPy'yi](https://github.com/cupy/cupy)yükleyin:

```bash
pip3.5 install cupy
```

> [!NOTE]
> Windows'da CuPy'yi CUDA 8.0 ile derlemek için [Visual Studio'nun](https://visualstudio.microsoft.com/) 2015 sürümüne veya [Microsoft Visual C++ Build Tools'a](https://visualstudio.microsoft.com/visual-cpp-build-tools/) ihtiyacınız vardır.

Chainer'ı yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install chainer==3.0.0
```
