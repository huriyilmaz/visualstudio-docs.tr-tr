---
title: Yığın çerçeveleri | Microsoft Docs
description: Bu makalede, Visual Studio 'daki hata ayıklayıcı mimarisinde bir yığın çerçevesinin tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b0c54292d79b119fc36c9eff3f0f3519c92a4205
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079401"
---
# <a name="stack-frames"></a>Yığın çerçeveleri
Hata ayıklayıcı mimarisinde *yığın çerçevesi*:

- , Bir iş parçacığının Yürütme bağlamını sağlayan bir yığın soyutlamasıdır. Bir iş parçacığı her zaman bir işlev içinde yürütülür. Yığın çerçevesi, işlevin yerel değişkenlerini ve bağımsız değişkenlerini barındırır. Visual Studio ile hata ayıklamak için, hata ayıklaması yapılan dilin veya ortamın yığın çerçevelerini desteklemesi gerekir.

- Hem tanımlayabilir hem de tanımlayabilir ve ilişkili iş parçacığını döndürebilir. Yığın çerçevesi, geçerli yönerge işaretçisini ve ilişkili belgeleri ve ifade değerlendirme bağlamlarını temsil eden kod bağlamını de döndürebilir.

- , Yerel değişkenlerin ve bağımsız değişkenlerin adını, türünü ve değerini tanımlayan ve çeşitli IDE hata ayıklama pencereleri içinde görüntülenen özelliklere sahiptir.

- , Genellikle bir hata ayıklama altyapısı (DE) veya sanal makine tarafından bir iş parçacığı yürütmenin sonucu olarak oluşturulan bir [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
