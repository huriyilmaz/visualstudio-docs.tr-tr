---
title: 'Idebugdynamicfieldcomplus:: GetTypeFromTypeDef | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypeFromTypeDef
- IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e212f53467c25ca6084eaa5a91b37031baedf4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731238"
---
# <a name="idebugdynamicfieldcomplusgettypefromtypedef"></a>IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
Belirteci verilen bir tür alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetTypeFromTypeDef(
   ULONG32       ulAppDomainID,
   GUID          guidModule,
   _mdToken      tokClass,
   IDebugField** ppType
);
```

```csharp
int GetTypeFromTypeDef(
   uint            ulAppDomainID,
   Guid            guidModule,
   int             tokClass,
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parametreler
`ulAppDomainID`\
'ndaki Uygulama etki alanının tanımlayıcısı.

`guidModule`\
'ndaki Modülün benzersiz tanıtıcısı.

`tokClass`\
'ndaki Türü temsil eden belirteç.

`ppType`\
dışı Türü içeren bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
