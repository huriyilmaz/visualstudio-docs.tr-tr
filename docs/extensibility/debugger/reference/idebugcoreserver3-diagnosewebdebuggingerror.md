---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fec5b8fbe1cae18b8221702fe14443df231d8880
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732958"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Otomatik eklemenin neden başarısız olduğunu belirlemeye çalışır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parametreler
`pszUrl`\
[içinde] Şu anda kullanılmamış; her zaman null değerine ayarlanmalıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Diğer tipik iade kodları şunlardır:

|Kod|Açıklama|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Uzak sunucunun hata ayıklamayı başlatmak için neden başarısız olduğunu belirleyemiyor.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Büyük olasılıkla yetersiz izinler nedeniyle veya HATA Ayıklama fiili etkin olmadığı için uzak sunucuda hata ayıklama yapamaz.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web sunucusu kilitlendi ve hata ayıklamayı etkinleştirmek için gerekli olan HATA Ayıklama fiilini engelliyor.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
