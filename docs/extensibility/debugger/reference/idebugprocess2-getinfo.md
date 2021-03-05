---
description: İşlemin açıklamasını alır.
title: 'IDebugProcess2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6e6b8e0c14cee960d1991ae4f5a482f66e89465
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169216"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
İşlemin açıklamasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>Parametreler
`Fields`\
'ndaki [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) Numaralandırmadaki, parametrenin hangi alanlarının doldurulacağını belirten değerlerin bir birleşimi `pProcessInfo` .

`pProcessInfo`\
dışı İşlemin açıklamasıyla doldurulmuş bir [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
