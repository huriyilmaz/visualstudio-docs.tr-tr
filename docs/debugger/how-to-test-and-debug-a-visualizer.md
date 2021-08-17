---
title: Görselleştiriciyi Test Ve Hata Ayıklama | Microsoft Docs
description: Görselleştiriciyi test sürücüsünden (görselleştirici geliştirme ana bilgisayarı) çalıştırarak veya bir hata ayıklayıcısı penceresinden Visual Studio yükleyerek test ve hata ayıklama.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 139c0c0b2cce08d211e3d318d8ab90d0dd5a368f08004133f1ef31b3f58a257a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453392"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Test Etme ve Hata Ayıklama
Görselleştirici yazdıktan sonra hata ayıklamalı ve test etmek gerekir.

Görselleştiriciyi test etmek için bir yol, görselleştiriciyi Visual Studio hata ayıklayıcısı penceresinden çağırarak yapmaktır. [(Bkz. Nasıl: Görselleştirici Yükleme](../debugger/how-to-install-a-visualizer.md).) Bunu yaparsanız, hata ayıklayıcının ilk örneğinde çalışan görselleştiriciyi eklemek ve hata ayıklamak için Visual Studio'nin ikinci bir örneğini kullansanız gerekir.

Görselleştiricide hata ayıklamanın daha kolay bir yolu, görselleştiriciyi bir test sürücüsünden çalıştırmaktır. Görselleştirici API'leri, görselleştirici geliştirme ana bilgisayarı olarak adlandırılan böyle bir *sürücü oluşturmanızı kolaylaştırır.*

>[!NOTE]
> Şu anda test sürücüsü yalnızca görselleştirici bir uygulamanın görselleştiricisi .NET Framework desteklemektedir.

### <a name="to-create-a-visualizer-development-host"></a>Görselleştirici geliştirme ana bilgisayarı oluşturmak için

1. Hata ayıklayıcı tarafı sınıfınıza bir nesnesi oluşturan ve show yöntemini <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> çağıran statik bir yöntem dahil eder:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Ana bilgisayarı oluşturmak için kullanılan parametreler görselleştiricide ( ) ve hata ayıklayıcı yan sınıfının türünde gösterilecek `objectToVisualize` veri nesnesidir.

2. çağrısı için aşağıdaki deyimi `TestShowVisualizer` ekleyin. Görselleştiricinizi bir sınıf kitaplığında oluşturduysanız, sınıf kitaplığını çağıracak ve bu deyimi yürütülebilir dosyanıza yer alan bir yürütülebilir dosya oluşturmanız gerekir:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Daha eksiksiz bir örnek için bkz. [Kılavuz: C# ile Görselleştirici Yazma.](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek Yol: C# ile Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Nasıl kurulur: Görselleştirici Yükleme](../debugger/how-to-install-a-visualizer.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
