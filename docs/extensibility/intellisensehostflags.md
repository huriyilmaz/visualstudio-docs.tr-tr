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
ms.openlocfilehash: 4ca23fb8a388619afda5b23f437a87627e05baea
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725092"
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

|Üyeler|Description|
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
