---
title: yerel koddaki iş parçacıkları hata ayıklama için İpuçları | Microsoft Docs
description: Visual Studio çoklu iş parçacıklı uygulamalarda hata ayıklaması yapıyorsanız yerel koddaki iş parçacıklarında hata ayıklama ipuçları listesini okuyun.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: c621d35554095eb676a478ed78887fe41c4fed31
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090297"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Yerel Kod İş Parçacıklarında Hata Ayıklama İpuçları
Yerel koddaki iş parçacıklarında hata ayıklarken kullanabileceğiniz bazı ipuçları şunlardır:

- `@TIB` **İzleme** penceresinde veya **QuickWatch** Iletişim kutusunda yazarak iş parçacığı bilgi bloğunun içeriğini görüntüleyebilirsiniz.

- Geçerli iş parçacığının son hata kodunu `@Err` **izleme** penceresinde veya **QuickWatch** iletişim kutusunda girerek görüntüleyebilirsiniz.

- C Run-Time kitaplıkları (CRT) işlevleri çok iş parçacıklı bir uygulamada hata ayıklamak için yararlı olabilir. Daha fazla bilgi için bkz. [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)