---
title: IDebugThread2::SetNextStatement | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b390e5c021fa069ae3fb09eef1978caaf9cc8ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718656"
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
İleride kullanım için ayrılmış; null değerine ayarlanır.

`pCodeContext`\
[içinde] Yürütülmek üzere olan kod konumunu ve içeriğini açıklayan bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Aşağıdaki tablo diğer olası değerleri gösterir.

|Değer|Açıklama|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Sonraki deyim, çerçeve yığınının üzerinde daha derin bir yığın çerçevesi olamaz.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Sonraki deyim yığındaki herhangi bir çerçeveyle ilişkili değildir.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Bazı hata ayıklama motorları bir özel durum sonra bir sonraki deyimi ayarlayamaz.|

## <a name="remarks"></a>Açıklamalar
 Yönerge işaretçisi, yürütülecek bir sonraki yönergeyi veya deyimi gösterir. Bu yöntem, kaynak kodu satırını yeniden denemek veya yürütmeyi başka bir işlevde devam etmeye zorlamak için kullanılır, örneğin.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
