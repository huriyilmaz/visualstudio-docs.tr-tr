---
title: 'Nasıl yapılır: Görselleştiriciyi test etme ve hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18261d9e8c6c7d3f65dea7c72439b29f4e2e0df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176500"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Test Etme ve Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştirici yazdıktan sonra hata ayıklaması yapmanız ve test etmeniz gerekir.  
  
 Görselleştirici test etmenin bir yolu, Visual Studio 'ya yüklenerek hata ayıklayıcı penceresinden çağırarak. (Bkz. [nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md).) Bunu yaparsanız, hata ayıklayıcının ilk örneğinde çalışan görselleştiricisi eklemek ve hatalarını ayıklamak için Visual Studio 'nun ikinci bir örneğini kullanmanız gerekir.  
  
 Görselleştirici hata ayıklamanın daha kolay bir yolu, Görselleştirici bir test sürücüsünden çalıştırılmaktır. Görselleştiricisi API 'Leri, *görselleştiricisi geliştirme Konağı*olarak adlandırılan böyle bir sürücü oluşturmayı kolaylaştırır.  
  
### <a name="to-create-a-visualizer-development-host"></a>Görselleştiricisi geliştirme konağı oluşturmak için  
  
1. Hata ayıklayıcı tarafı sınıfınıza, bir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> nesnesi oluşturan ve Show yöntemini çağıran statik bir yöntem ekleyin:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Konağı oluşturmak için kullanılan parametreler, Görselleştirici ( `objectToVisualize` ) ve hata ayıklayıcı tarafı sınıfının türü içinde gösterilecek veri nesnesidir.  
  
2. Çağırmak için aşağıdaki ifadeyi ekleyin `TestShowVisualizer` . Görselleştiriciyi bir sınıf kitaplığında oluşturduysanız, sınıf kitaplığını çağırmak için bir yürütülebilir dosya oluşturmanız ve bu ifadeyi çalıştırılabilirinize yerleştirmeniz gerekir:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Daha kapsamlı bir örnek için bkz. [Izlenecek yol: C# dilinde Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: C 'de Görselleştirici Yazma #](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)   
 [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
