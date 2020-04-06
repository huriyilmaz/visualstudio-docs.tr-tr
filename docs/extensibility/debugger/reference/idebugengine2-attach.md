---
title: IDebugEngine2::Ekle | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731212"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Bir programa veya programlara hata ayıklama altyapısı (DE) bağlar. DE, SDM'de işlem sırasında çalışırken oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Parametreler
`pProgram`\
[içinde] Eklenecek programları temsil eden bir dizi [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi. Bunlar bağlantı noktası programları.

`rgpProgramNodes`\
[içinde] Program düğümlerini temsil eden, her program için bir tane olan [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesneleri dizisi. Bu dizideki program düğümleri , 'deki `pProgram`gibi aynı programları temsil eder. Program düğümleri, DE'nin eklenecek programları tanımlayabilmesi için verilir.

`celtPrograms`\
[içinde] Dizilerde ve dizilerde program `pProgram` ve/veya `rgpProgramNodes` program düğümlerinin sayısı.

`pCallback`\
[içinde] Hata ayıklama olaylarını SDM'ye göndermek için kullanılacak [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`dwReason`\
[içinde] Bu programların eklenmesinin nedenini belirten [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) numaralandırma değeri. Daha fazla bilgi için Açıklamalar bölümüne bakın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir programa iliştirilmanın üç nedeni vardır:

- `ATTACH_REASON_LAUNCH`kullanıcı programa iliştirdiği için DE'nin programa iliştirdiğini gösterir.

- `ATTACH_REASON_USER`kullanıcının bir programa (veya program içeren işleme) eklemek için DE'yi açıkça istediğini gösterir.

- `ATTACH_REASON_AUTO`belirli bir işlemdeki diğer programların hata ayıklama zaten olduğundan DE belirli bir programa iliştiriyor gösterir. Buna otomatik ekleme de denir.

  Bu yöntem çağrıldığında, DE'nin bu olayları sırayla göndermesi gerekir:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (hata ayıklama motorunun belirli bir örneği için gönderilmemişse)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Buna ek olarak, iliştirme nedeni `ATTACH_REASON_LAUNCH`ise, DE [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) olay göndermek gerekiyor.

   DE, debugged olan programa karşılık gelen [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesi aldıktan sonra, herhangi bir özel arabirim için sorgulanabilir.

   Tarafından verilen dizideki bir program düğümünün `pProgram` yöntemlerini çağırmadan önce veya `rgpProgramNodes`gerekirse, program `IDebugProgram2` düğümünün temsil ettiği arabirimde kimliğe bürünme etkinleştirilmelidir. Normalde, ancak, bu adım gerekli değildir. Daha fazla bilgi için [Güvenlik Sorunları'na](../../../extensibility/debugger/security-issues.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
