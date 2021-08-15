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
ms.openlocfilehash: e2dffe0a53383343c6990b2b19eeead2bb200893e1c97662d8afb4cb44c3812f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121310899"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Yerel Kod İş Parçacıklarında Hata Ayıklama İpuçları
Yerel koddaki iş parçacıklarında hata ayıklarken kullanabileceğiniz bazı ipuçları şunlardır:

- `@TIB` **İzleme** penceresinde veya **QuickWatch** Iletişim kutusunda yazarak iş parçacığı bilgi bloğunun içeriğini görüntüleyebilirsiniz.

- Geçerli iş parçacığının son hata kodunu `@Err` **izleme** penceresinde veya **QuickWatch** iletişim kutusunda girerek görüntüleyebilirsiniz.

- C Run-Time kitaplıkları (CRT) işlevleri çok iş parçacıklı bir uygulamada hata ayıklamak için yararlı olabilir. Daha fazla bilgi için bkz. [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)