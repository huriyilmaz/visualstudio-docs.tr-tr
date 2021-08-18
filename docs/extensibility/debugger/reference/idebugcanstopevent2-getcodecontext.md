---
description: Bu olayın konumunu açıklayan kod bağlamını alır.
title: IDebugCanStopEvent2::GetCodeContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bdb7f4865174548247c91a5fc5c268ef419af1a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079850"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
Bu olayın konumunu açıklayan kod bağlamını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCodeContext( 
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parametreler
`ppCodeContext`\
[out] Geçerli kod [konumunu temsil eden IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Çoğu çalışma zamanı mimarisinde kod bağlamı, bir programın yürütme akışında belirli bir yönergeyi işaret alan bir adres olarak düşünebilirsiniz.

 Kaynak kod satırlarına yönelen belge bağlamını almak için [GetDocumentContext yöntemini çağırmanız](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
