---
title: IDebugProgramEx2::Ekle | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722382"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Bir programa oturum ekle.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Parametreler
`pCallback`\
[içinde] Ekli hata ayıklama altyapısının olayları gönderdiği geri arama işlevini temsil eden [bir IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`dwReason`\
[içinde] Ekleme işleminin nedenini açıklayan [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) numaralandırma değeri.

`pSession`\
[içinde] Programa eklenen oturumu benzersiz olarak tanımlayan bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde bir hata kodu döndürür. Program zaten `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` bağlıysa, bu yöntem döndürülmelidir.

## <a name="remarks"></a>Açıklamalar
 Programı içeren bağlantı noktası, `pSession` programa hangi oturumun bağlanmaya çalıştığını belirlemek için değeri kullanabilir. Örneğin, bir bağlantı noktası bir anda bir işleme yalnızca bir hata ayıklama oturumu eklemek için izin veriyorsa, bağlantı noktası aynı oturumun işlemdeki diğer programlara zaten bağlı olup olmadığını belirleyebilir.

> [!NOTE]
> Geçirilen `pSession` arabirim, yalnızca bir çerez olarak ele alınacaktır, bu programa bağlanan oturum hata ayıklama yöneticisini benzersiz olarak tanımlayan bir değer; sağlanan arabirimdeki yöntemlerin hiçbiri işlevsel değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
