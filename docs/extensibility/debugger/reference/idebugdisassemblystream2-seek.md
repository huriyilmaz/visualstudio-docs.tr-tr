---
title: IDebugDisassemblyStream2::Seek | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732079"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Okuma işaretçisini sökme akışındaki okundu işaretçisini belirli bir konuma göre belirli sayıda yönerge taşır.

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
[içinde] Arama işlemini başlatmak için göreli konumu belirten [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) numaralandırmadeğeri.

`pCodeContext`\
[içinde] Arama işleminin göreli olduğu kod bağlamını temsil eden [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi. Bu parametre `dwSeekStart`  =  `SEEK_START_CODECONTEXT`yalnızca; aksi takdirde, bu parametre yoksayılır ve null bir değer olabilir.

`uCodeLocationId`\
[içinde] Arama işleminin göreli olduğu kod konumu tanımlayıcısı. Bu parametre kullanılırsa; `dwSeekStart`  =  `SEEK_START_CODELOCID` aksi takdirde, bu parametre yoksayılır ve 0 olarak ayarlanabilir. Kod konum tanımlayıcısının açıklaması için [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) yönteminin Açıklamalar bölümüne bakın.

`iInstructions`\
[içinde] Belirtilen konuma göre hareket etmek için `dwSeekStart`talimat sayısı. Bu değer geriye doğru hareket etmek için negatif olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döndürür. Arama `S_FALSE` pozisyonu kullanılabilir yönergeler listesinin ötesinde bir noktaya geldiyse döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Arama, listenin başlangıcından önce bir konuma olsaydı, okuma konumu listedeki ilk yönergeye ayarlanır. See listenin sonundan sonra bir konuma olsaydı, okuma konumu listedeki son yönergeye ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
