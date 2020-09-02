---
title: 'Nasıl yapılır: yönetilen kodda Iş parçacığı adı ayarlama | Microsoft Docs'
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
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b800fbd2f39d75f110a059c70b87a203eb72e7d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157678"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Nasıl Yapılır: Yönetilen Kodda İş Parçacığı Adı Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'nun herhangi bir sürümünde iş parçacığı adlandırması mümkündür. İş parçacığı adlandırması **, iş parçacıkları penceresinde iş** parçacıklarını izlemek için yararlıdır. İş **parçacıkları** penceresi Visual Studio Express sürümlerinde kullanılamadığından, iş parçacığı adlandırması Express sürümlerinde çok az yardımcı programdır.  
  
 Yönetilen kodda bir iş parçacığı adı ayarlamak için <xref:System.Threading.Thread.Name%2A> özelliğini kullanın.  
  
## <a name="example"></a>Örnek  
  
```  
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
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Nasıl Yapılır: Yerel Kodda İş Parçacığı Adı Ayarlama](../debugger/how-to-set-a-thread-name-in-native-code.md)
