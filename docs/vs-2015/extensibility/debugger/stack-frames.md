---
title: Yığın çerçeveleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423393"
---
# <a name="stack-frames"></a>Yığın Çerçeveleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklayıcı mimarisi açısından bir **yığın çerçevesi**:  
  
- , Bir iş parçacığının Yürütme bağlamını sağlayan bir yığın soyutlamasıdır. Bir iş parçacığı her zaman bir işlev içinde yürütülür. Yığın çerçevesi, işlevin yerel değişkenlerini ve onun bağımsız değişkenlerini barındırır. Visual Studio ile hata ayıklamak için, hata ayıklaması yapılan dilin veya ortamın yığın çerçevelerini desteklemesi gerekir.  
  
- Hem tanımlayabilir hem de tanımlayabilir ve ilişkili iş parçacığını döndürebilir. Yığın çerçevesi Ayrıca, geçerli yönerge işaretçisini temsil eden kod bağlamını ve ilgili belge ve ifade değerlendirme bağlamlarını da döndürebilir.  
  
- , Yerel değişkenlerin ve bağımsız değişkenlerin adını, türünü ve değerini tanımlayan ve çeşitli IDE hata ayıklama pencereleri içinde görüntülenen özelliklere sahiptir.  
  
- , Genellikle bir hata ayıklama altyapısı (DE) veya sanal makine tarafından bir iş parçacığı yürütmenin sonucu olarak oluşturulan bir [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabirimi tarafından temsil edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)   
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)   
 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
