---
title: 'Nasıl yapılır: Görselleştiriciyi test etme ve hata ayıklama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a0d2fdcd0685b83f63e9354b96146c1c869b355
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732400"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Test Etme ve Hata Ayıklama
Görselleştirici yazdıktan sonra hata ayıklaması yapmanız ve test etmeniz gerekir.

Görselleştirici test etmenin bir yolu, Visual Studio 'ya yüklenerek hata ayıklayıcı penceresinden çağırarak. (Bkz. [nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md).) Bunu yaparsanız, hata ayıklayıcının ilk örneğinde çalışan görselleştiricisi eklemek ve hatalarını ayıklamak için Visual Studio 'nun ikinci bir örneğini kullanmanız gerekir.

Görselleştirici hata ayıklamanın daha kolay bir yolu, Görselleştirici bir test sürücüsünden çalıştırılmaktır. Görselleştiricisi API 'Leri, *görselleştiricisi geliştirme Konağı*olarak adlandırılan böyle bir sürücü oluşturmayı kolaylaştırır.

### <a name="to-create-a-visualizer-development-host"></a>Görselleştiricisi geliştirme konağı oluşturmak için

1. Hata ayıklayıcı tarafı sınıfınıza, <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> nesnesi oluşturan ve Show metodunu çağıran statik bir yöntem ekleyin:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Konağı oluşturmak için kullanılan parametreler, Görselleştirici (`objectToVisualize`) ve hata ayıklayıcı tarafı sınıfının türü içinde gösterilecek veri nesnesidir.

2. @No__t_0 çağırmak için aşağıdaki ifadeyi ekleyin. Görselleştiriciyi bir sınıf kitaplığında oluşturduysanız, sınıf kitaplığını çağırmak için bir yürütülebilir dosya oluşturmanız ve bu ifadeyi çalıştırılabilirinize yerleştirmeniz gerekir:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Daha kapsamlı bir örnek için bkz. [Izlenecek yol: bir Görselleştirici C#yazma ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek Yol: C# ile Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Nasıl Yapılır: Görselleştirici Yükleme](../debugger/how-to-install-a-visualizer.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
