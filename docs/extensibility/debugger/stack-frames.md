---
title: Yığın Çerçeveleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712837"
---
# <a name="stack-frames"></a>Yığın çerçeveleri
Hata ayıklama mimarisinde, *yığın çerçevesi:*

- Bir iş parçacığının yürütme bağlamını sağlayan bir yığının soyutlamamı. Bir iş parçacığı her zaman bir işlev içinde yürütür. Yığın çerçevesi, işlevin yerel değişkenlerini ve bağımsız değişkenlerini tutar. Visual Studio ile hata ayıklamak için, hata ayıklanan dil veya ortam yığın çerçevelerini desteklemelidir.

- Hem kendini tanımlayabilir hem de açıklayabilir ve ilişkili iş parçacığı döndürebilir. Yığın çerçevesi, geçerli yönerge işaretçisini ve ilişkili belge ve ifade değerlendirme bağlamlarını temsil eden kod bağlamını da döndürebilir.

- Yerel değişkenlerin ve bağımsız değişkenlerin adını, türünü ve değerini açıklayan ve çeşitli IDE hata ayıklama pencerelerinde görünen özelliklere sahiptir.

- Genellikle bir hata ayıklama motoru (DE) veya sanal makine tarafından bir iş parçacığı yürütme sonucu oluşturulan bir [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama bağlamları](../../extensibility/debugger/debugger-contexts.md)
- [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Hata ayıklama motoru](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
