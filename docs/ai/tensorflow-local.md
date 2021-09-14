---
title: TensorFlow modelini yerel olarak eğitme
description: Visual Studio için AI araçlarında yerel olarak bir TensorFlow modeli çalıştırın
keywords: AI, Visual Studio, TensorFlow, yerel
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633313"
---
# <a name="train-a-tensorflow-model-locally"></a>TensorFlow modelini yerel olarak eğitme

bu hızlı [başlangıçta, bir](http://yann.lecun.com/exdb/mnist/) tensorflow modelini aı için Visual Studio Araçları yerel olarak yerel bir şekilde eğeceğiz.

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
tensorflow, CNTK, theano ve daha fazlası arasında derin öğrenime başlarken örnekleri içeren bu [GitHub depoyu](https://github.com/Microsoft/samples-for-ai) indirin.

## <a name="open-solution-and-train-model"></a>Çözüm açın ve modeli eğitme

- Visual Studio başlatın ve **dosya > seçin > Project/çözüm açın**.

- İndirilen örnek deposundan **TensorFlow örnekleri** klasörünü seçin ve **tensorflowexamples. sln** dosyasını açın.

   ![Projeyi açma](media/tensorflow-local/open-project.png)

   ![Çözümü aç](media/tensorflow-local/open-solution.png)

- **Çözüm Gezgini** içindeki mnist projesini bulun, sağ tıklayın ve **Başlangıç Project olarak ayarla**' yı seçin.

- **Başlat**'a tıklayın.

- Çıktı konsolunda yazdırılır.

   ![Konsoldan örnek çıkış](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Bulutta TensorFlow modelini eğitme](tensorflow-vm.md)
