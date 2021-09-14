---
description: Belge bağlamını verilen sayıda deyim veya satır olarak kaydırır.
title: 'IDebugDocumentContext2:: Seek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d18e00071d23e22ed2cbd99f9b88f95c13aee253
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635006"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Belge bağlamını verilen sayıda deyim veya satır olarak kaydırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parametreler
`nCount`\
'ndaki Belge bağlamına bağlı olarak ileredilecek deyim veya satır sayısı.

`ppDocContext`\
dışı Yeni konuma sahip yeni bir [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
