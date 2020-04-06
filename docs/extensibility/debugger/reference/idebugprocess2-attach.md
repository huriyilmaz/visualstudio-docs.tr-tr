---
title: IDebugProcess2::Ekle | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724186"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Oturum hata ayıklama yöneticisini (SDM) işleme bağlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parametreler
`pCallback`\
[içinde] Hata ayıklama olay bildirimi için kullanılan bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`rgguidSpecificEngines`\
[içinde] İşlemde çalışan programları hata ayıklamak için kullanılacak hata ayıklama motorları guids bir dizi. Bu parametre null değeri olabilir. Ayrıntılar için Açıklamalar'a bakın.

`celtSpecificEngines`\
[içinde] `rgguidSpecificEngines` Dizideki hata ayıklama motorlarının sayısı ve `rghrEngineAttach` dizinin boyutu.

`rghrEngineAttach`\
[içinde, dışarı] Hata ayıklama motorları tarafından döndürülen bir dizi HRESULT kodu. Bu dizinin boyutu `celtSpecificEngines` parametrede belirtilir. Her kod genellikle `S_OK` ya `S_ATTACH_DEFERRED`da . İkincisi, DE'nin şu anda hiçbir programa bağlı olmadığını gösterir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Aşağıdaki tablo diğer olası değerleri gösterir.

|Değer|Açıklama|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Belirtilen işlem hata ayıklama işlemine zaten bağlı.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Ekleme işlemi sırasında bir güvenlik ihlali oluştu.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Bir masaüstü işlemi hata ayıklama eklenemez.|

## <a name="remarks"></a>Açıklamalar
 Bir işleme iliştirilmesi, `rgguidSpecificEngines` dizide belirtilen hata ayıklama motorları (DE) tarafından debubed ilerleyebilir bu işlemde çalışan tüm programlara SDM bağlanır. Parametreyi `rgguidSpecificEngines` null değerine ayarlayın `GUID_NULL` veya işlemdeki tüm programlara eklemek üzere diziye ekleyin.

 İşlemde oluşan tüm hata ayıklama olayları verilen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesine gönderilir. SDM bu yöntemi aradığında bu `IDebugEventCallback2` nesne sağlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
