---
title: Yığın Çerçeveleri | Microsoft Docs
description: Bu makalede, Visual Studio'de hata ayıklayıcı mimarisinde yığın çerçevesinin tanımı ve Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: dc6c10f00f12d1ee8df9918530a3b04d6ba5ef4e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102871"
---
# <a name="stack-frames"></a>Yığın çerçeveleri
Hata ayıklayıcısı mimarisinde bir *yığın çerçevesi:*

- Bir iş parçacığının yürütme bağlamını sağlayan bir yığının soyutlamadır. İş parçacığı her zaman bir işlevin içinde yürütülür. Yığın çerçevesi, işlevin yerel değişkenlerini ve işlevin bağımsız değişkenlerini tutar. Hata ayıklama ile hata ayıklamak Visual Studio, hata ayıklanacak dil veya ortamın yığın çerçevelerini desteklemesi gerekir.

- Hem kendisini tanımlayabilir hem de tanımlayabilir ve ilişkili iş parçacığını geri getirebilirsiniz. Bir yığın çerçevesi, geçerli yönerge işaretçisini ve ilişkili belge ve ifade değerlendirme bağlamlarını temsil eden kod bağlamını da geri getirebilirsiniz.

- Yerel değişkenlerin ve bağımsız değişkenlerin adını, türünü ve değerini açıklayan ve çeşitli IDE hata ayıklama pencerelerinde görünen özellikleri vardır.

- Genellikle bir iş parçacığı yürütmenin bir sonucu olarak bir hata ayıklama altyapısı (DE) veya sanal makine tarafından oluşturulan [bir IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabirimiyle temsil edilen.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı bağlamları](../../extensibility/debugger/debugger-contexts.md)
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
