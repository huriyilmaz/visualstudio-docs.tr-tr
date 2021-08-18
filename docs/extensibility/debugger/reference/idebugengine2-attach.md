---
description: Bir program veya programlara hata ayıklama altyapısı (DE) iliştirer.
title: IDebugEngine2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f733dc1ad1ee3e87c5d28721a308c22f3fc2e0fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119171"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Bir program veya programlara hata ayıklama altyapısı (DE) iliştirer. DE işlem sırasında SDM'ye çalıştırıldıklarında oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>Parametreler
`pProgram`\
[in] Ekli programları [temsil eden bir IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesneleri dizisi. Bunlar bağlantı noktası programlarıdır.

`rgpProgramNodes`\
[in] Program düğümlerini [temsil eden bir IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesneleri dizisi, her program için bir tane. Bu dizideki program düğümleri, içinde olduğu gibi aynı programları temsil `pProgram` ediyor. PROGRAM düğümleri, DE'nin iliştirilen programları tanımlay için verilir.

`celtPrograms`\
[in] ve dizileri içinde program ve/veya program `pProgram` `rgpProgramNodes` düğümlerinin sayısı.

`pCallback`\
[in] SDM'ye hata ayıklama olayları göndermek için kullanılacak [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`dwReason`\
[in] Bu programların [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) belirten bir değerdir. Daha fazla bilgi için Açıklamalar bölümüne bakın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir programa eklemenin üç nedeni vardır:

- `ATTACH_REASON_LAUNCH` , kullanıcı onu içeren işlemi başlattığı için DE'nin programa ekli olduğunu gösterir.

- `ATTACH_REASON_USER` , kullanıcının de'den bir programa (veya program içeren işleme) eklemesi için açıkça istekte olduğunu gösterir.

- `ATTACH_REASON_AUTO` DE'nin belirli bir işlemde diğer programlarda zaten hata ayıklarken belirli bir programa ekli olduğunu gösterir. Bu, otomatik ekleme olarak da adlandırılan bir durum.

  Bu yöntem çağrıldı olduğunda, DE'nin bu olayları sırayla göndermesi gerekir:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (hata ayıklama altyapısının belirli bir örneği için henüz gönderilmedi ise)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Ayrıca, eklemenin nedeni ise `ATTACH_REASON_LAUNCH` DE'nin [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) olayı göndermesi gerekir.

   DE, hata ayıklanan programa [karşılık gelen IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesini alır, herhangi bir özel arabirim için sorgulandırabilirsiniz.

   veya tarafından verilen dizideki bir program düğümünün yöntemlerini çağırmadan önce, gerekirse kimliğe bürünme, program düğümünü temsil eden `pProgram` `rgpProgramNodes` `IDebugProgram2` arabirimde etkinleştirilmelidir. Ancak normalde bu adım gerekli değildir. Daha fazla bilgi için [bkz. Güvenlik Sorunları.](../../../extensibility/debugger/security-issues.md)

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
