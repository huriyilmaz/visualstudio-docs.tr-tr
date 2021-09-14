---
description: Belirtilen hata ayıklama motorları için otomatik eklemeye izin vermez.
title: 'IDebugCoreServer3:: Enableoto Iliştirme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f72f0586d2d393d265aac0220b7c0c1faa64d49
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725247"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Belirtilen hata ayıklama motorları için otomatik eklemeye izin vermez.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parametreler
`rgguidSpecificEngines`\
'ndaki Her hata ayıklama altyapısının otomatik iliştirme olarak işaretleneceği GUID dizisi.

`celtSpecificEngines`\
'ndaki İçinde belirtilen altyapı sayısı `rgguidSpecificEngines` .

`pszStartPageUrl`\
'ndaki Otomatik iliştirme sırasında kullanılacak başlangıç URL 'SI.

`pbstrSessionID`\
dışı Otomatik olarak eklenen oturumun KIMLIĞI.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür. Bir hata kodu `E_AUTO_ATTACH_NOT_REGISTERED` , otomatik iliştirme sınıf fabrikasının kaydedilmemiş olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
 Belirtilen URL ile ilişkili bir program başlatıldığında, belirtilen hata ayıklama motorları otomatik olarak başlatılır ve eklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
