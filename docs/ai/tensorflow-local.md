---
title: Tensorflow modelini yerel olarak eğitin
description: Tensorflow modelini yerel olarak AI Tools for Visual Studio
keywords: ai, visual studio, tensorflow, yerel
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: d1e27999af1c467f0231c28a6f1ea53fb4c466a6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037570"
---
# <a name="train-a-tensorflow-model-locally"></a>TensorFlow modelini yerel olarak eğitin

Bu hızlı başlangıçta, AI için yerel olarak [MNIST](http://yann.lecun.com/exdb/mnist/) veri kümesiyle bir TensorFlow Visual Studio Araçları eğitacağız.

MNIST veritabanında 60.000 örnekli bir eğitim kümesi ve el yazısı basamaklardan 10.000 örnekli bir test kümesi vardır.

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce, aşağıdakilerin yüklü olduğundan emin olmak için:

### <a name="google-tensorflow"></a>Google TensorFlow

Terminalde aşağıdaki komutu çalıştırın:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy ve SciPy
[NumPy ve](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) [SciPy'yi yükleyin.](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy)

### <a name="download-sample-code"></a>Örnek kodu indirme
TensorFlow GitHub, CNTK, Theano ve daha fazlası genelinde derin öğrenmeyi öğrenmeye başlamaya yönelik örnekler içeren bu depoyu indirin. [](https://github.com/Microsoft/samples-for-ai)

## <a name="open-solution-and-train-model"></a>Çözümü açma ve modeli eğitma

- Dosya Visual Studio'ı **açın ve Dosya >/Çözüm'> Project Aç'ı seçin.**

- İndirilen **örnek deposundan Tensorflow** Örnekleri klasörünü seçin ve **TensorflowExamples.sln dosyasını** açın.

   ![Projeyi açma](media/tensorflow-local/open-project.png)

   ![Çözümü açma](media/tensorflow-local/open-solution.png)

- içinde MNIST projesini **bulun Çözüm Gezgini** tıklayın ve Başlangıç Olarak Ayarla'yı **Project.**

- **Başlat**'a tıklayın.

- Çıkış konsolda yazdırılır.

   ![Konsoldan örnek çıktı](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Bulutta TensorFlow modelini eğitme](tensorflow-vm.md)
