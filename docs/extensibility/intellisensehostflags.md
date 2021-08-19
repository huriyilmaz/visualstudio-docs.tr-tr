---
title: IntelliSenseHostFlags | Microsoft Docs
description: IntelliSenseHostFlags numaralandırması, IntelliSense ana bilgisayar bayraklarını belirtir. Bu makalede, Enum değerleri açıklanmaktadır.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050253"
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
|`IHF_READONLYCONTEXT`|Bağlam arabelleği salt okunurdur.|
|`IHF_NOSEPARATESUBJECT`|Konu metni yok. Bağlam arabelleği IntelliSense-target (anlamına gelir `!IHF_READONLYCONTEXT` ) içerir.|
|`IHF_SINGLELINESUBJECT`|Konu metni çok satırlı özellikli değil.|
|`IHF_FORCECOMMITTOCONTEXT`|Aynı `CanCommitIntoReadOnlyBuffer` .|
|`IHF_OVERTYPE`|Düzenlemenin (konu veya bağlamda) üzerine yazma modunda yapılması gerekir.|

## <a name="requirements"></a>Gereksinimler
 SingleFileeditor. IDL

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.TextManager.Interop>
