---
description: Özelliği için genişletilmiş bilgileri alır.
title: 'IDebugProperty2:: Gebir Deınfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad540166ff769aaa894ad4142843553951217234
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065041"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Özelliği için genişletilmiş bilgileri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>Parametreler
`guidExtendedInfo`\
'ndaki Alınacak genişletilmiş bilgilerin türünü belirleyen GUID. Ayrıntılar için bkz. açıklamalar.

`pExtendedInfo`\
dışı `VARIANT` Genişletilmiş özellik bilgilerini almak için kullanılabilecek bir (C++) veya nesne (C#) döndürür. Örneğin, bu parametre `IUnknown` bir [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) arabirimi için sorgulanabilen bir arabirim döndürebilir. Ayrıntılar için bkz. açıklamalar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür. `S_GETEXTENDEDINFO_NO_EXTENDEDINFO`Alınacak genişletilmiş bilgi yoksa döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemini çağırarak, kendisini alma amacını taşıyan bilgileri alma amacıyla mevcuttur.

 Aşağıdaki GUID 'Ler genellikle bu yöntem tarafından tanınır (ad hiçbir derlemede kullanılamadığından, C# için GUID değerleri belirtilir). İç kullanım için ek GUID 'Ler oluşturulabilir.

|Name|GUID|Description|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11D0-b47f-00a0244a1dd2}|Belgeye bir `IUnknown` arabirim döndürür. Genellikle, [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) arabirimi Bu arabirimden elde edilebilir `IUnknown` .|
|guidCodeContext|{e2fc65e-56ce-11D1-b528-00aax004a8797}|`IUnknown`Belge bağlamına bir arabirim döndürür. Genellikle, [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimi Bu arabirimden elde edilebilir `IUnknown` .|
|Guidcustomviewerdestekleniyor|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Genellikle bir ifade değerlendirici tarafından uygulanan özel bir görüntüleyicinin CLSID 'sini içeren bir dize döndürür.|
|Kılavuzu Xtendedinfoslot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Bu özellik yönetilen bir kod yerel adresini temsil ediyorsa, istenen yuva numarasını temsil eden 32 bitlik bir sayı döndürür.|
|Kılavuzu Xtendedinfosignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Property nesnesiyle ilişkili değişkenin imzasını içeren bir dize döndürür.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
