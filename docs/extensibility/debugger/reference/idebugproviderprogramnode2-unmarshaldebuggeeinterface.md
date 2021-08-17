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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 585f05969f0bf987abd6db67fae826ba00e916a6eb279989042087a499b757b5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402382"
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
