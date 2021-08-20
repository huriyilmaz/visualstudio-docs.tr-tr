---
description: Disassembly akışında belirtilen konuma göre belirli sayıdaki yönergelerin okuma işaretçisini taşır.
title: IDebugDisassemblyStream2::Seek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2dc5c80d58ceb3efbf7007178252dadcb66a0692
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127304"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Disassembly akışında belirtilen konuma göre belirli sayıdaki yönergelerin okuma işaretçisini taşır.

## <a name="syntax"></a>Sözdizimi

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
[in] Arama [işleminin SEEK_START](../../../extensibility/debugger/reference/seek-start.md) konumunu belirten bir değerdir.

`pCodeContext`\
[in] Arama işlemi için göreli kod bağlamını temsil eden [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi. Bu parametre yalnızca ; aksi `dwSeekStart`  =  `SEEK_START_CODECONTEXT` takdirde, bu parametre yoksayılır ve null değer olabilirse kullanılır.

`uCodeLocationId`\
[in] Arama işlemi göreli kod konumu tanımlayıcısı. Bu parametre kullanılır; `dwSeekStart`  =  `SEEK_START_CODELOCID` aksi takdirde, bu parametre yoksayılır ve 0 olarak ayarlanır. Kod konumu tanımlayıcısının açıklaması için [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) yönteminin Açıklamalar bölümüne bakın.

`iInstructions`\
[in] içinde belirtilen konuma göre hareket etmek için yönergelerin `dwSeekStart` sayısı. Bu değer geriye doğru hareket etmek için negatif olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Arama `S_FALSE` konumu, kullanılabilir yönergeler listesinin ötesinde bir noktaya gelinse döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Arama, listenin başlangıcından önceki bir konuma ayarlanmışsa, okuma konumu listenin ilk yönergesi olarak ayarlanır. Görme, listenin sonundan sonra bir konuma ayarlanmışsa, okuma konumu listede son yönergeye ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
