---
description: Bir program veya programa hata ayıklama altyapısı (DE) iliştirir.
title: 'IDebugEngine2:: Attach | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38275cc623fcb8b30646c9d84ef194f584369ef2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093918"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Bir program veya programa hata ayıklama altyapısı (DE) iliştirir. Aynı işlem sırasında SDM 'nin üzerinde çalıştığı zaman, oturum hata ayıklama Yöneticisi (SDM) tarafından çağırılır.

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
'ndaki İliştirilebilecek programları temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesneleri dizisi. Bunlar bağlantı noktası programlarıdır.

`rgpProgramNodes`\
'ndaki Her program için bir tane olmak üzere program düğümlerini temsil eden bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesneleri dizisi. Bu dizideki program düğümleri ile aynı programları temsil eder `pProgram` . Program düğümleri, ' nin iliştirilecek programları belirleyebilmesi için verilir.

`celtPrograms`\
'ndaki `pProgram` Ve dizilerindeki program ve/veya program düğümlerinin sayısı `rgpProgramNodes` .

`pCallback`\
'ndaki Hata ayıklama olaylarını SDM 'ye göndermek için kullanılacak [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`dwReason`\
'ndaki [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) numaralandırmasından bu programları ekleme nedeninizi belirten bir değer. Daha fazla bilgi için, açıklamalar bölümüne bakın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir programa eklemek için aşağıdaki gibi üç neden vardır:

- `ATTACH_REASON_LAUNCH` Kullanıcı kendisini içeren işlemi başlatduğundan DE, ' ın programa iliştirdiğini gösterir.

- `ATTACH_REASON_USER` Kullanıcının açıkça bir programa (veya bir program içeren işlem) iliştirmeyi istediğini gösterir.

- `ATTACH_REASON_AUTO` aynı anda belirli bir işlemdeki diğer programlarda hata ayıklaması yapıldığından DE belirli bir programa ekleme olduğunu gösterir. Bu, otomatik iliştirme olarak da adlandırılır.

  Bu yöntem çağrıldığında, DE bu olayların sırayla gönderilmesi gerekir:

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (hata ayıklama altyapısının belirli bir örneği için henüz gönderilmezse)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   Ayrıca, iliştirme nedeni ise, `ATTACH_REASON_LAUNCH` de [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) olayını göndermelidir.

   Ayrıca, hata ayıklamakta olan programa karşılık gelen [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesini aldıktan sonra, herhangi bir özel arabirim için sorgulanabilecek.

   Veya tarafından verilen dizide bir program düğümünün yöntemlerini çağırmadan önce, `pProgram` `rgpProgramNodes` gerekli olduğunda kimliğe bürünme, `IDebugProgram2` Program düğümünü temsil eden arabirimde etkinleştirilmelidir. Ancak normalde bu adım gerekli değildir. Daha fazla bilgi için bkz. [güvenlik sorunları](../../../extensibility/debugger/security-issues.md).

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
