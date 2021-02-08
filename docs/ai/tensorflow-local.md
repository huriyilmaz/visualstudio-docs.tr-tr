---
title: TensorFlow modelini yerel olarak eğitme
description: Visual Studio için AI araçları 'nda yerel olarak bir TensorFlow modeli çalıştırma
keywords: AI, Visual Studio, TensorFlow, yerel
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 0ceb21701958630c8b783d5b6850c5e0a0ab229a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841386"
---
# <a name="train-a-tensorflow-model-locally"></a>TensorFlow modelini yerel olarak eğitme

Bu hızlı [Başlangıçta, Visual Studio Tools for AI](http://yann.lecun.com/exdb/mnist/) içinde yerel olarak bir TensorFlow modeli kullanarak bir mamici veri kümesiyle eğeceğiz.

MNIST veritabanı, 60.000 örnek bir eğitim kümesine ve el yazısı rakamlarının bir dizi 10.000 örneklerine sahiptir.

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce, aşağıdakilerin yüklü olduğundan emin olun:

### <a name="google-tensorflow"></a>Google TensorFlow

Bir terminalde aşağıdaki komutu çalıştırın:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>Sayısal tuş takımı ve SciPy
[Sayısal tuş, y](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) ve [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy)'yi yükler.

### <a name="download-sample-code"></a>Örnek kodu indir
TensorFlow, CNTK, Theano ve daha fazlası arasında derin öğrenime Başlarken örnekleri içeren bu [GitHub deposunu](https://github.com/Microsoft/samples-for-ai) indirin.

## <a name="open-solution-and-train-model"></a>Çözüm açın ve modeli eğitme

- Visual Studio 'Yu başlatın ve **> projesi/çözümü açmak > dosya**' yı seçin.

- İndirilen örnek deposundan **TensorFlow örnekleri** klasörünü seçin ve **tensorflowexamples. sln** dosyasını açın.

   ![Projeyi açma](media/tensorflow-local/open-project.png)

   ![Çözümü aç](media/tensorflow-local/open-solution.png)

- **Çözüm Gezgini** içindeki mnist projesini bulun, sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

- **Başlat**'a tıklayın.

- Çıktı konsolunda yazdırılır.

   ![Konsoldan örnek çıkış](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Bulutta TensorFlow modelini eğitme](tensorflow-vm.md)
