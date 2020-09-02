---
title: Yerel koddaki Iş parçacıkları hata ayıklama ipuçları | Microsoft Docs
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
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c299d3585d9089f8525c2ec7f470601797cc3a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684867"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Yerel Kod İş Parçacıklarında Hata Ayıklama İpuçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yerel koddaki iş parçacıklarında hata ayıklarken kullanabileceğiniz bazı ipuçları şunlardır:  
  
- `@TIB` **İzleme** penceresinde veya **QuickWatch** Iletişim kutusunda yazarak iş parçacığı bilgi bloğunun içeriğini görüntüleyebilirsiniz.  
  
- Geçerli iş parçacığının son hata kodunu `@Err` **izleme** penceresinde veya **QuickWatch** iletişim kutusunda girerek görüntüleyebilirsiniz.  
  
- C çalışma zamanı kitaplıkları (CRT) işlevleri, çok iş parçacıklı bir uygulamada hata ayıklamak için yararlı olabilir. Daha fazla bilgi için bkz. [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
