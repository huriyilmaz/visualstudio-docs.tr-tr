---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732916"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Belirtilen hata ayıklama motorları için otomatik ekleme sağlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parametreler
`rgguidSpecificEngines`\
[içinde] Otomatik bağlama olarak işaretlemek için her hata ayıklama altyapısı için GUID dizisi.

`celtSpecificEngines`\
[içinde] 'de `rgguidSpecificEngines`belirtilen motor sayısı.

`pszStartPageUrl`\
[içinde] Otomatik takma yaparken kullanılacak başlangıç URL'si.

`pbstrSessionID`\
[çıkış] Otomatik olarak iliştirilen oturumun kimliği.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde hata kodu döndürür. Bir hata `E_AUTO_ATTACH_NOT_REGISTERED`kodu, otomatik ekleme sınıfı fabrika kayıtlı olmadığını gösterir.

## <a name="remarks"></a>Açıklamalar
 Belirtilen URL ile ilişkili bir program başlatıldığında, belirtilen hata ayıklama motorları otomatik olarak başlatılır ve eklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
