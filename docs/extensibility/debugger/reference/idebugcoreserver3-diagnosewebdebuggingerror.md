---
description: Otomatik eklemenin neden başarısız olduğunu belirlemeye çalışır.
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9745c3027ef9e6d86f831f4a1773c27268d90fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127382"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Otomatik eklemenin neden başarısız olduğunu belirlemeye çalışır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parametreler
`pszUrl`\
[in] Şu anda kullanılmadı; her zaman null değere ayar olmalıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Aşağıdakiler diğer tipik dönüş kodlarıdır:

|Kod|Açıklama|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Uzak sunucunun hata ayıklamayı neden başlatamay neden başarısız olduğu belirlenemedi.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Büyük olasılıkla yetersiz izinler nedeniyle veya DEBUG fiili etkinleştirilmemiş olduğundan uzak sunucuda hata ayıklanmaz.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web sunucusu kilitlendi ve hata ayıklamayı etkinleştirmek için gereken DEBUG fiilini engelliyor.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
