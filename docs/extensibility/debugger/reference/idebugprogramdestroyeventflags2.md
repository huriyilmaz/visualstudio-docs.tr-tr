---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722497"
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
