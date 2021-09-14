---
description: Uygulama etki alanı için tanımlayıcıyı alır.
title: 'IDebugAlias2:: Getappdomainıd | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20be3f4abaa53dd6d65770142935003db7b211ab
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627621"
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
dışı Uygulama etki alanı tanımlayıcısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Uygulama etki alanı tanımlayıcısı, uygulama her yeniden başlatıldığında ve yeni bir uygulama etki alanı oluşturulduğunda değişir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
