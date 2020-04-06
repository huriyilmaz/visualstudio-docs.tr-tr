---
title: IDebugAlias2::GetAppDomainId | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca8f2311b58fc7e73f9eb4f4c14f993c88b9a62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736408"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Uygulama etki alanı için tanımlayıcıyı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Parametreler
`pappDomainId`\
[çıkış] Uygulama etki alanı tanımlayıcısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Uygulama yeniden başlatıldığında ve yeni bir uygulama etki alanı oluşturulduğunda uygulama etki alanı tanımlayıcısı değişir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
