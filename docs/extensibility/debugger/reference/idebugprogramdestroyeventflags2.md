---
description: Bir hata ayıklama oturumunu sonlandırdığınızda, Visual Studio Kullanıcı arabiriminin varsayılan davranışını geçersiz kılmak için bir hata ayıklama altyapısı sağlar.
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02b2d934c2a556d3556d494368145e52a8c97394
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168198"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Bir hata ayıklama oturumunu sonlandırdığınızda, bir hata ayıklama altyapısının Kullanıcı arabiriminin varsayılan davranışını geçersiz kılmasını sağlar [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, hata ayıklama motorları tarafından uygulanır. Bir işlemin kullanım ömrü boyunca birden fazla program oluşturup bozmasına neden olabilecek konaklar için yararlıdır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProgramDestroyEventFlags2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Program yok etme bayraklarını alır.|

## <a name="remarks"></a>Açıklamalar
 Kullanıcı arabiriminin varsayılan davranışı, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] tüm programlar bir program yok etme olayı gönderdikten sonra tasarım moduna geri dönmeyecektir. Bu arabirim bir hata ayıklama altyapısının bu davranışı değiştirmesini sağlar.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
