---
title: Bir tensorflow modelini yerel olarak eğitin
description: Visual Studio için AI Tools'ta yerel olarak bir tensorflow modeli çalıştırın
keywords: ai, visual studio, tensorflow, yerel
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 43ce126baeb96efcaab3c40bac912274ee1cd8c7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72777438"
---
# <a name="train-a-tensorflow-model-locally"></a>TensorFlow modelini yerel olarak eğitin

Bu hızlı başlangıçta, AI için Visual Studio Tools'ta yerel olarak [MNIST](http://yann.lecun.com/exdb/mnist/) veri seti ne olacaksa bir TensorFlow modelini eğiteceğiz.

MNIST veritabanında 60.000 örnekten oluşan bir eğitim kümesi ve 10.000 el yazısı basamak örneği bir test kümesi vardır.

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce aşağıdakileri yüklediğinizden emin olun:

### <a name="google-tensorflow"></a>Google TensorFlow

Bir terminalde aşağıdaki komutu çalıştırın:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>Sayısal ve SciPy
[NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) ve [SciPy'yi](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy)yükleyin.

### <a name="download-sample-code"></a>Örnek kodu indirin
TensorFlow, CNTK, Theano ve daha fazla sınanmaya başlamak için örnekler içeren bu [GitHub deposunu](https://github.com/Microsoft/samples-for-ai) indirin.

## <a name="open-solution-and-train-model"></a>Açık çözüm ve tren modeli

- Visual Studio'u başlatın ve **Dosya > Açık > Projesi/Çözümü'nü**seçin.

- İndirilen örnek deposundan **Tensorflow Örnekleri** klasörünü seçin ve **TensorflowExamples.sln** dosyasını açın.

   ![Projeyi açma](media/tensorflow-local/open-project.png)

   ![Açık çözüm](media/tensorflow-local/open-solution.png)

- **Çözüm Gezgini'nde**MNIST projesini bulun, sağ tıklayın ve **Başlangıç Projesi olarak Ayarla'yı**seçin.

- **Başlat**'a tıklayın.

- Çıktı konsola yazdırılır.

   ![Konsoldan örnek çıktı](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Bulutta bir TensorFlow modelini eğitin](tensorflow-vm.md)
