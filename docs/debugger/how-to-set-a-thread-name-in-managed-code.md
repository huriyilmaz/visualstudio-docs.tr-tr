---
title: Yönetilen Kod Kümesinde İş Parçacığı | Microsoft Docs
description: Birden çok iş parçacıklı uygulamada hata ayıklama sırasında yönetilen kodda iş parçacığı Visual Studio. İş parçacığı adlandırma, İş Parçacıkları penceresindeki iş parçacıklarını izlemek için kullanılır.
ms.custom: SEO-VS-2020
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 5d0ce2bdadd7ea325ef63aa3f561fa949945207295fce0ef69adabad474be6cb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379015"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Nasıl Yapılır: Yönetilen Kodda İş Parçacığı Adı Ayarlama
İş parçacığı adlandırma, iş parçacığı adlandırmanın herhangi bir Visual Studio. İş parçacığı adlandırma, İş Parçacıkları penceresindeki iş parçacıklarını izlemek **için** kullanışlıdır.

 Yönetilen kodda iş parçacığı adı ayarlamak için özelliğini <xref:System.Threading.Thread.Name%2A> kullanın.

## <a name="example"></a>Örnek

```csharp
public class Needle
{
    // This method will be called when the thread is started.
    public void Baz()
    {
        Console.WriteLine("Needle Baz is running on another thread");
    }
}

public void Main()
{
    Console.WriteLine("Thread Simple Sample");
    Needle oNeedle = new Needle();
    // Create a Thread object.
    System.Threading.Thread oThread = new System.Threading.Thread(oNeedle.Baz);
    // Set the Thread name to "MyThread".
    oThread.Name = "MyThread";
    // Starting the thread invokes the ThreadStart delegate
    oThread.Start();
}
```

```VB
Public Class Needle
    ' This method will be called when the thread is started.
    Sub Baz()
        Console.WriteLine("Needle Baz is running on another thread")
    End Sub
End Class

Sub Main()
    Console.WriteLine("Thread Simple Sample")
    Dim oNeedle As New Needle()
   ' Create a Thread object.
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)
    ' Set the Thread name to "MyThread".
    oThread.Name = "MyThread"
    ' Starting the thread invokes the ThreadStart delegate
    oThread.Start()
End Sub
```

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Nasıl Yapılır: Yerel Kodda İş Parçacığı Adı Ayarlama](../debugger/how-to-set-a-thread-name-in-native-code.md)