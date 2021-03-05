---
description: Belgenin sınıf tanımlayıcısını alır.
title: 'IDebugDocument2:: Getdocumentclassıd | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36a95914f470d0ce095db0c0db8d1397b02be3cf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166560"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Belgenin sınıf tanımlayıcısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

## <a name="parameters"></a>Parametreler
`pclsid` dışı Belgenin sınıf KIMLIĞI olan bir GUID döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sınıf GUID 'SI, her birinin bir belgeyi temsil eden tek tek sınıfları oluşturmak için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
