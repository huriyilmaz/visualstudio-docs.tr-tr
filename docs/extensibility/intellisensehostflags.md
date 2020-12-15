---
title: IntelliSenseHostFlags | Microsoft Docs
description: IntelliSenseHostFlags numaralandırması, IntelliSense ana bilgisayar bayraklarını belirtir. Bu makalede, Enum değerleri açıklanmaktadır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b206cc4aa7c1ff388d6868fa8a0533d15da094ff
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487510"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
IntelliSense ana bilgisayar bayraklarını belirtir.

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

|Üyeler|Description|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Bağlam arabelleği salt okunurdur.|
|`IHF_NOSEPARATESUBJECT`|Konu metni yok. Bağlam arabelleği IntelliSense-target (anlamına gelir `!IHF_READONLYCONTEXT` ) içerir.|
|`IHF_SINGLELINESUBJECT`|Konu metni çok satırlı özellikli değil.|
|`IHF_FORCECOMMITTOCONTEXT`|Aynı `CanCommitIntoReadOnlyBuffer` .|
|`IHF_OVERTYPE`|Düzenlemenin (konu veya bağlamda) üzerine yazma modunda yapılması gerekir.|

## <a name="requirements"></a>Gereksinimler
 SingleFileeditor. IDL

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.TextManager.Interop>
