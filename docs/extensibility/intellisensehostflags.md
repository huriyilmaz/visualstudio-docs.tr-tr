---
title: IntelliSenseHostFlags | Microsoft Docs
description: IntelliSenseHostFlags numaralama, IntelliSense konak bayraklarını belirtir. Bu makalede enum değerleri açıklanmıştır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0672f7a4d8788c0efac9e11b5ae3359338791ebbf572fed0a9b12d0e185f00b8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376462"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
IntelliSense konak bayraklarını belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Parametreler

|Üyeler|Açıklama|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Bağlam arabelleği salt okunur.|
|`IHF_NOSEPARATESUBJECT`|Konu metni yok. Bağlam arabelleği IntelliSense hedefi içerir (anlamına `!IHF_READONLYCONTEXT` gelir).|
|`IHF_SINGLELINESUBJECT`|Konu metni çok satırlı değildir.|
|`IHF_FORCECOMMITTOCONTEXT`|ile `CanCommitIntoReadOnlyBuffer` aynı.|
|`IHF_OVERTYPE`|Düzenleme (konu veya bağlam) üzerine yazma modunda yapılmalı.|

## <a name="requirements"></a>Gereksinimler
 SingleFileeditor.idl

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.TextManager.Interop>
