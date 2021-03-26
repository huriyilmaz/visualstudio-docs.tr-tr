---
description: Geçerli yönerge işaretçisini verilen kod bağlamına ayarlar.
title: 'IDebugThread2:: Setnextdeyimizi | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5dd6bd027a9938b7dce855742cc351180498bb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081171"
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
Gelecekte kullanılmak üzere ayrılmıştır; null değere ayarlayın.

`pCodeContext`\
'ndaki Yürütülmesi ve bağlamı için kod konumunu açıklayan bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda olası diğer değerler gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Sonraki ifade, çerçeve yığınında daha derin bir yığın çerçevesinde olamaz.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Sonraki ifade, yığındaki herhangi bir kareyle ilişkili değildir.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Bazı hata ayıklama motorları bir özel durumdan sonra sonraki ifadeyi ayarlayamıyor.|

## <a name="remarks"></a>Açıklamalar
 Yönerge işaretçisi, yürütülecek bir sonraki yönergeyi veya ifadeyi gösterir. Bu yöntem, kaynak kodu satırını yeniden denemek veya yürütmeye zorlamak için, örneğin başka bir işlevde devam etmek için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
