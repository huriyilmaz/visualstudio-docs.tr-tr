---
title: 'IDebugDisassemblyStream2:: Seek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732079"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Ayırma akışındaki okuma işaretçisini, belirtilen bir konuma göre verilen sayıda yönergeye kaydırır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Parametreler
`dwSeekStart`\
'ndaki Arama işlemini başlatmak için göreli konumu belirten [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) numaralandırmasından bir değer.

`pCodeContext`\
'ndaki Arama işleminin göreli olduğu kod bağlamını temsil eden [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi. Bu parametre yalnızca ise kullanılır `dwSeekStart`  =  `SEEK_START_CODECONTEXT` ; Aksi takdirde, bu parametre yok sayılır ve null bir değer olabilir.

`uCodeLocationId`\
'ndaki Arama işleminin göreli olduğu kod konumu tanımlayıcısı. Bu parametre ise kullanılır `dwSeekStart`  =  `SEEK_START_CODELOCID` ; Aksi takdirde, bu parametre yok sayılır ve 0 olarak ayarlanabilir. Kod konumu tanımlayıcısının açıklaması için [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) yöntemi için açıklamalar bölümüne bakın.

`iInstructions`\
'ndaki İçinde belirtilen konuma göre taşınacak yönergelerin sayısı `dwSeekStart` . Bu değer geriye doğru ilerlemek için negatif olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Arama konumunun kullanılabilir yönergeler listesinin ötesinde bir noktaya olup olmadığını döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Arama, listenin başlangıcından önceki bir konuma ise, okuma konumu listedeki ilk yönergeye ayarlanır. Liste, listenin sonundan sonraki bir konuma ise, okuma konumu listedeki son yönergeye ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
