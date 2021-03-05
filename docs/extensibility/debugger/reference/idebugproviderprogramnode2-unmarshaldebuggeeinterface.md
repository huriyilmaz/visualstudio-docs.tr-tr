---
description: İşlem sınırları genelinde belirtilen bir arabirimi edinir.
title: 'IDebugProviderProgramNode2:: Unmarshaldebuggeeınterface | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f51484ae1e9acbb9b94fe546f8157145673e22f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167873"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
İşlem sınırları genelinde belirtilen bir arabirimi edinir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parametreler
`riid`\
'ndaki Elde edilecek arabirimin GUID 'ı.

`ppvObject`\
dışı İstenen arabirimi uygulayan nesneyi döndürür. [C++] Bu, doğrudan istenen arabirim türüne dönüşebilir. [C#] <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> istenen arabirimi almak için yöntemini kullanın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, hata ayıklama altyapısı işlem alanında çalışırken [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ve hata ayıklamakta olan programın kendi işlem alanında çalıştığı durumlarda kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
