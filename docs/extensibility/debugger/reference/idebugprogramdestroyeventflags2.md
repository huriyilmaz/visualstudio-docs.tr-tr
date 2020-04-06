---
title: IDebugProgramDestroyEventFlags2 | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722497"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Hata ayıklama oturumunu sonladiğinizde [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ui varsayılan davranışını geçersiz kılmak için hata ayıklama altyapısı sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim hata ayıklama motorları tarafından uygulanır. Bir işlemin ömrü boyunca birden çok program oluşturup yok edebilecek ana bilgisayarlar için yararlıdır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugProgramDestroyEventFlags2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Programı alır bayrakları yok.|

## <a name="remarks"></a>Açıklamalar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Kullanıcı Arabirimi'nin varsayılan davranışı, tüm programlar bir programı yok etme olayını gönderdikten sonra tasarım moduna geri dönmektir. Bu arabirim, hata ayıklama altyapısının bu davranışı değiştirmesini sağlar.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
