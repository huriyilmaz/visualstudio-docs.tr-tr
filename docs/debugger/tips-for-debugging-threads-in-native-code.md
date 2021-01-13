---
title: Yerel koddaki Iş parçacıkları hata ayıklama ipuçları | Microsoft Docs
description: Visual Studio 'da çok iş parçacıklı uygulamalarda hata ayıklaması yapıyorsanız yerel koddaki iş parçacıklarında hata ayıklama ipuçları listesini okuyun.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9249e1527a7dd2ae720ab575b1d443c10b85376e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150060"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Yerel Kod İş Parçacıklarında Hata Ayıklama İpuçları
Yerel koddaki iş parçacıklarında hata ayıklarken kullanabileceğiniz bazı ipuçları şunlardır:

- `@TIB` **İzleme** penceresinde veya **QuickWatch** Iletişim kutusunda yazarak iş parçacığı bilgi bloğunun içeriğini görüntüleyebilirsiniz.

- Geçerli iş parçacığının son hata kodunu `@Err` **izleme** penceresinde veya **QuickWatch** iletişim kutusunda girerek görüntüleyebilirsiniz.

- C Run-Time kitaplıkları (CRT) işlevleri çok iş parçacıklı bir uygulamada hata ayıklamak için yararlı olabilir. Daha fazla bilgi için bkz. [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)