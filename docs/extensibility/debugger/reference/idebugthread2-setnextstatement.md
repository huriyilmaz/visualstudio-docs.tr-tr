---
description: Geçerli yönerge işaretçisini verilen kod bağlamına ayarlar.
title: IDebugThread2::SetNextStatement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19029364411df0fa086b6821f4a7107072845a4edafbf17a7904f08aef3c9871
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402096"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Geçerli yönerge işaretçisini verilen kod bağlamına ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parametreler
`pStackFrame`\
Gelecekteki kullanım için ayrılmıştır; null değere ayarlanır.

`pCodeContext`\
[in] Yürütülecek kod konumunu ve bağlamını açıklayan [bir IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Aşağıdaki tabloda diğer olası değerler yer alır.

|Değer|Açıklama|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Sonraki deyim, çerçeve yığınında daha derin bir yığın çerçevesinde olamaz.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Sonraki deyim yığında herhangi bir çerçeveyle ilişkili değildir.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Bazı hata ayıklama altyapıları bir özel durum sonrasında sonraki deyimi ayaramaz.|

## <a name="remarks"></a>Açıklamalar
 Yönerge işaretçisi, yürütülecek sonraki yönergeyi veya deyimi gösterir. Bu yöntem, bir kaynak kodu satırı yeniden denemek veya yürütmeyi başka bir işlevde devam etmek için zorlamak için kullanılır, örneğin.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
