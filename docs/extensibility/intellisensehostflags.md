---
title: IntelliSenseHostFlags | Microsoft Dokümanlar
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
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710266"
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

|Üyeler|Açıklama|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Bağlam arabelleği salt okunur.|
|`IHF_NOSEPARATESUBJECT`|Konu metni yok. Bağlam arabelleği IntelliSense-hedef `!IHF_READONLYCONTEXT`içerir (ima).|
|`IHF_SINGLELINESUBJECT`|Özne metni çok satırlı değildir.|
|`IHF_FORCECOMMITTOCONTEXT`|Aynı `CanCommitIntoReadOnlyBuffer`şey.|
|`IHF_OVERTYPE`|Düzenleme (konu veya bağlam) overtype modunda yapılmalıdır.|

## <a name="requirements"></a>Gereksinimler
 SingleFileeditor.idl

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.TextManager.Interop>
