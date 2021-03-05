---
description: Oturum hata ayıklama yöneticisini (SDM) işleme iliştirir.
title: 'IDebugProcess2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73dbe76a32e67794736fd26595378485879b00b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161450"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Oturum hata ayıklama yöneticisini (SDM) işleme iliştirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parametreler
`pCallback`\
'ndaki Hata ayıklama olayı bildiriminde kullanılan bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`rgguidSpecificEngines`\
'ndaki İşlemde çalışan programlarda hata ayıklaması yapmak için kullanılacak hata ayıklama altyapısının GUID dizisi. Bu parametre null bir değer olabilir. Ayrıntılar için bkz. açıklamalar.

`celtSpecificEngines`\
'ndaki Dizideki hata ayıklama altyapısının sayısı `rgguidSpecificEngines` ve `rghrEngineAttach` dizinin boyutu.

`rghrEngineAttach`\
[in, out] Hata ayıklama altyapılarının döndürdüğü bir HRESULT kodları dizisi. Bu dizinin boyutu `celtSpecificEngines` parametresinde belirtilir. Her kod genellikle ya da `S_OK` olur `S_ATTACH_DEFERRED` . İkincisi, aynı anda hiçbir program için DE bağlı olduğunu gösterir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda olası diğer değerler gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Belirtilen işlem hata ayıklayıcıya zaten eklenmiş.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|İliştirme yordamı sırasında bir güvenlik ihlali oluştu.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Bir masaüstü işlemi hata ayıklayıcıya eklenemiyor.|

## <a name="remarks"></a>Açıklamalar
 Bir işleme iliştirme, SDM 'yi dizide belirtilen hata ayıklama altyapıları (DE) tarafından ayıklanabilecek bu işlemde çalışan tüm programlara iliştirir `rgguidSpecificEngines` . `rgguidSpecificEngines`Parametresini null bir değer olarak ayarlayın veya `GUID_NULL` işlemdeki tüm programlara eklemek için diziye dahil edin.

 İşlemde oluşan tüm hata ayıklama olayları verilen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesine gönderilir. `IDebugEventCallback2`SDM Bu yöntemi çağırdığında bu nesne sağlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
