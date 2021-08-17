---
description: Hata ayıklama oturumunu sona ererken hata ayıklama altyapısının Visual Studio kullanıcı arabiriminin varsayılan davranışını geçersiz kmasına olanak sağlar.
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 17c9cf3f910a1d94bf8a2972bb0615dd6f2e3b5762e99ae2eebff53c7a94611f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338754"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Hata ayıklama oturumunu sona ererken kullanıcı arabiriminin varsayılan davranışını geçersiz [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] kılmak için hata ayıklama altyapısını sağlar.

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim hata ayıklama altyapıları tarafından uygulanır. Bir işlem ömrü boyunca birden çok program oluşturan ve yok eden konaklar için yararlıdır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugProgramDestroyEventFlags2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Program yok etme bayraklarını alın.|

## <a name="remarks"></a>Açıklamalar
 Kullanıcı arabiriminin varsayılan davranışı, tüm programlar bir program yok etme olayı [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] gönderdikten sonra tasarım moduna geri dönmektir. Bu arabirim, hata ayıklama altyapısının bu davranışı değiştirmesini sağlar.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
