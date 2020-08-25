---
title: AI araçları 'nı yükler
description: Visual Studio için AI araçlarının nasıl yükleneceğini açıklar
keywords: AI, Visual Studio
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: ffa8c7634c0d97dd24ff69814ae73ad5ff12928b
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800209"
---
# <a name="installation"></a>Yükleme

Visual Studio Tools for AI, Windows 64-bit işletim sistemlerine yüklenebilir.

## <a name="install-visual-studio-tools-for-ai"></a>Visual Studio Tools for AI yüklensin

Bu uzantı, Visual Studio 2015 ve Visual Studio 2017, Community Edition veya üzeri sürümlerle birlikte kullanılabilir.

Araçları [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017)veya Visual Studio içinden indirebilirsiniz:

1. **Araçlar**  >  **Uzantılar ve Güncelleştirmeler '** i seçin.

   ![Visual Studio 'da Uzantılar ve güncelleştirmeler menüsü](media/installation/extensions.png)

2. **Uzantılar ve güncelleştirmeler** iletişim kutusunda sol taraftaki **çevrimiçi** ' i seçin.
3. Sağ üst köşedeki arama kutusuna "AI araçları" yazın veya girin.
4. Sonuçlardan **Visual Studio Tools for AI** seçin.
5. **İndir**'i seçin.

## <a name="prepare-your-local-machine"></a>Yerel makinenizi hazırlama
Yerel bilgisayarınızdaki derinlemesine öğrenme modellerini öğreticmadan önce, uygulanabilir önkoşulların yüklü olduğundan emin olun. Bu, NVıDıA GPU (varsa) için en son sürücülere ve kitaplıklara sahip olduğunuzdan emin olmanızı içerir. Ayrıca, projenizde kullanmayı planladığınız Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, keras, Theano, PyTorch ve Chainer gibi Python ve Python kitaplıklarını da yüklediğinizden emin olun.

> [!NOTE]
> Aşağıdaki alt bölümlerde yazılım tanıtımı, homepages 'ten alınmıştır.

### <a name="nvidia-gpu-driver"></a>NVıDıA GPU sürücüsü

Derin öğrenme çerçeveleri, makinelerin bir hız, doğruluk ve gerçek yapay zeka doğru ölçeklenebilmesini sağlamak için NVıDıA GPU avantajlarından yararlanır. Bilgisayarınızda NVıDıA GPU kartları varsa bkz. [NVIDIA sürücü indirmeleri](https://www.nvidia.com/Download/index.aspx) veya en son sürücüyü yüklemek için bir işletim sistemi güncelleştirmesi deneyin.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) , NVIDIA tarafından bir paralel bilgi işlem platformu ve programlama modelidir. GPU 'nun gücünden yararlanarak işlem performansının önemli artışına izin verir. Şu anda CUDA araç seti 8,0 derin öğrenme çerçeveleri için gereklidir.

CUDA 'yi yüklemek için

- Bu [siteyi](https://developer.nvidia.com/cuda-80-ga2-download-archive)ziyaret edın, CUDA indirin ve yükleyin.
- CUDA çalışma zamanı kitaplıklarını yüklediğinizden emin olun ve ardından% PATH% veya $Path ortam değişkenine CUDA ikili yolunu ekleyin.
- Windows 'da bu yol, varsayılan olarak "C:\Program Files\nvıdıa GPU bilgi Işlem araç Kit\cuda\v8.0\Bin" şeklindedir.

![Windows 'a CUDA 'yı yükler](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[Cudnn](https://developer.nvidia.com/cudnn) (CUDA derin sinir ağ kitaplığı), NVIDIA tarafından derin sinir ağlarının temel ELEMANLARıNA yönelik GPU hızlandırmalı bir kitaplıktır. cuDNN V6, en son derin öğrenme çerçeveleri için gereklidir.

CuDNN 'yi yüklemek için:

- En son paketi indirmek ve yüklemek için [NVIDIA geliştirici](https://developer.nvidia.com/rdp/cudnn-download) adresini ziyaret edin.
- CuDNN ikilisini içeren dizini% PATH% veya $Path ortam değişkenine eklemediğinizden emin olun.
- Windows 'da, cudnn64_6.dll "C:\Program Files\nvıdıa GPU bilgi Işlem araç Kit\cuda\v8.0\Bin" dizinine kopyalayabilirsiniz.

> [!NOTE]
> CNTK 2,0 ve TensorFlow 1.2.1 gibi önceki derin öğrenme çerçevelerinin cuDNN v 5.1 olması gerekir. Ancak, birden çok cuDNN sürümünü birlikte yükleyebilirsiniz.

### <a name="python"></a>Python

Python, derin öğrenme uygulamaları için birincil programlama dilidir. **64 bit** Python dağıtımı gereklidir ve en iyi uyumluluk için [Python 3.5.4](https://www.python.org/downloads/release/python-354/) önerilir.

### <a name="to-install-python-on-windows"></a>Windows 'a Python yüklemek için

- Python başlatıcısı 'nı yalnızca kendiniz için yüklemenizi ve% PATH% ortam değişkenine Python eklemeyi öneririz.
- Python 'da yazılmış yazılım paketlerini yüklemek ve yönetmek için paket yönetim sistemi PIP 'yi yüklediğinizden emin olun.

Derin öğrenme çerçeveleri kendi yüklemeleri için PIP kullanır.

![Windows üzerinde Python’ı yükleme](media/installation/install_python_win.png)

Daha sonra, Python 3,5 ' in doğru yüklenip yüklenmediğini doğrulamanız ve bir terminalde aşağıdaki komutları yürüterek PIP 'yi en son sürüme yükseltmek gerekir:

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

### <a name="python-on-visual-studio"></a>Visual Studio 'da Python

Python, Visual Studio 'da uzantılar aracılığıyla tam olarak desteklenmektedir.
Daha fazla ayrıntı için [Visual Studio Araçları Python](../python/installing-python-support-in-visual-studio.md) yüklemesi hakkında daha fazla bilgi edinin.

### <a name="numpy-and-scipy"></a>Sayısal tuş takımı ve SciPy

- **Sayısal tuş takımı** , küçük çok boyutlu diziler için çok fazla hıza ödün vermeden, rastgele kayıtların büyük ölçekli dizilerini verimli bir şekilde işlemek için tasarlanan genel amaçlı bir dizi işleme paketidir.

- **SciPy** ("sigh pasta"), bir çift yönlü y 'ye bağlı olarak matematik, bilim ve Mühendislik için açık kaynaklı yazılımdır. 1.0.0 sürümünden başlayarak, SciPy artık Windows için resmi önceden oluşturulmuş bir tekerlek paketine sahiptir.

Sayısal tuş a ve SciPy 'yi yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Yukarıdaki komut, var olan eski veya resmi olmayan (örneğin, Windows için üçüncü taraf paketleri http://www.lfd.uci.edu/~gohlke/pythonlibs/ ) sayısal tuş a ve SciPy 'yi en son resmi olanlara yükseltir.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) , yönlendirilmiş bir grafik aracılığıyla sinir ağlarını bir dizi Hesaplama adımı olarak açıklayan birleştirilmiş bir ayrıntılı öğrenme araç setidir. CNTK, Python ve BrainScript programlama dillerini destekler.

> [!NOTE]
> CNTK Şu anda macOS 'ı desteklemiyor.

CNTK Python paketini yüklemek için bkz. [cntk yüklemesi](/cognitive-toolkit/Setup-CNTK-on-your-machine).

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) , veri akışı grafiklerini kullanan sayısal hesaplama için açık kaynaklı bir yazılım kitaplığıdır. Ayrıntılı yükleme için [buraya](https://www.tensorflow.org/install/) başvurun.

> [!NOTE]
> Sürüm 1,2 itibariyle, TensorFlow artık macOS için GPU desteği sağlamaz.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) basit, modüler ve ölçeklenebilir derinlemesine bir öğrenme çerçevesidir. Özgün Caffe 'de derleme, Caffe2 ifade, hız ve modülerliği göz önünde bulundurularak tasarlanmıştır.

Şu anda önceden oluşturulmuş bir Caffe2 Python tekerlek paketi mevcut değil.

Kaynak koddan derlemek için [burayı](https://caffe2.ai/docs/getting-started.html) ziyaret edin.

### <a name="mxnet"></a>MXNet

[Apache MXNet (ınubating)](https://mxnet.incubator.apache.org/) , verimlilik ve esneklik için tasarlanan derin bir öğrenme çerçevesidir. Verimliliği ve verimliliği en üst düzeye çıkarmak için [sembolik ve kesinlik temelli programlama](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) **karışmanızı** sağlar.

MXNet ' i yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

- GPU ile

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- GPU olmadan

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) , Python 'da yazılmış, CNTK, TensorFlow veya teano üzerinde çalışan üst düzey bir sınır Networks API 'sidir. Hızlı deneme etkinleştirme konusunda bir odak ile geliştirilmiştir. İyi bir araştırma yapmak için olası en az gecikme olan anahtarla sonuçdan sonuca gidebileceksiniz.

Keras 'yi yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

Bu [, çok](http://deeplearning.net/software/theano/) boyutlu dizileri verimli bir şekilde tanımlamanıza, iyileştirmenize ve değerlendirmenize olanak tanıyan bir Python kitaplığıdır.

Ano yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[Pytorch](https://pytorch.org/) , iki üst düzey Özellik sağlayan bir Python paketidir:

- Güçlü GPU hızlandırma ile Tensor hesaplaması (sayısal tuş takımı gibi)
- Bant tabanlı bir oto sistem sisteminde oluşturulan derin sinir ağları

PyTorch 'yi yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

- **Windows**

  Henüz resmi bir tekerlek paketi yok. Bir üçüncü taraf paketini, [Anaconda](https://anaconda.org/pytorch/repo?type=all) veya [California Üniversitesi](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch)'nden indirebilirsiniz.

  - Ana dizininiz için sıkıştırmayı açın, örneğin, *C:\users\test\pytorch*.
  - % PYTHONPATH% ortam değişkenine *C:\users\test\pytorch\lib\site-Packages* ekleyin.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **macOS**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > macOS ikilileri CUDA 'yi desteklemez, CUDA gerekliyse kaynaktan yüklenir

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Bu tek paket hem GPU hem de CPU 'YU destekler.

Son olarak, Windows dışı bilgisayarlarda torchvision 'ı yüklersiniz:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) , esneklik açısından bir Python tabanlı derin öğrenme çerçevesidir. Bu, sinir ağlarını derlemek ve eğmek için nesne odaklı üst düzey API 'Lerin yanı sıra, otomatik fark temelli API 'ler sağlar (dinamik hesaplama grafikleri olarak da bilinir)

CUDA desteğini etkinleştirmek için, [cupy](https://github.com/cupy/cupy)'yi yükler:

```bash
pip3.5 install cupy
```

> [!NOTE]
> Windows 'da, CUDA 8,0 ile CuPy derlemek için [Visual Studio](https://visualstudio.microsoft.com/) 'nun 2015 sürümüne veya [Microsoft Visual C++ derleme araçlarına](https://visualstudio.microsoft.com/visual-cpp-build-tools/) ihtiyacınız vardır.

Chainer 'yi yüklemek için bir terminalde aşağıdaki komutu çalıştırın:

```bash
pip3.5 install chainer==3.0.0
```
