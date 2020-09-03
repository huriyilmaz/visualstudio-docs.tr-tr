---
title: Yerel koddaki Iş parçacıkları hata ayıklama ipuçları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 7dde94e28f378f0630a78f32ae5e58533729ce0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729002"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Yerel Kod İş Parçacıklarında Hata Ayıklama İpuçları
Yerel koddaki iş parçacıklarında hata ayıklarken kullanabileceğiniz bazı ipuçları şunlardır:

- `@TIB` **İzleme** penceresinde veya **QuickWatch** Iletişim kutusunda yazarak iş parçacığı bilgi bloğunun içeriğini görüntüleyebilirsiniz.

- Geçerli iş parçacığının son hata kodunu `@Err` **izleme** penceresinde veya **QuickWatch** iletişim kutusunda girerek görüntüleyebilirsiniz.

- C çalışma zamanı kitaplıkları (CRT) işlevleri, çok iş parçacıklı bir uygulamada hata ayıklamak için yararlı olabilir. Daha fazla bilgi için bkz. [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Ayrıca bkz.
- [Çok İş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)