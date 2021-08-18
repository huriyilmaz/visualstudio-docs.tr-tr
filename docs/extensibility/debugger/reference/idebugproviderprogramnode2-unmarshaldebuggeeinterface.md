---
description: İşlem sınırları arasında belirtilen bir arabirimi elde edin.
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs
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
ms.openlocfilehash: a17ef182c3b480ce2fa2809c2258a7509d30b14b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071064"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
İşlem sınırları arasında belirtilen bir arabirimi elde edin.

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
[in] Elde edilen arabirimin GUID'si.

`ppvObject`\
[out] İstenen arabirimi uygulayan nesneyi döndürür. [C++] Bu, doğrudan istenen arabirim türüne atilebilir. [C#] istenen <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> arabirimi almak için yöntemini kullanın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, hata ayıklama altyapısı işlem alanı içinde çalıştırıldıklarında ve hata ayıklama yapılan program kendi [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] işlem alanı içinde çalıştırıldıklarında kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
