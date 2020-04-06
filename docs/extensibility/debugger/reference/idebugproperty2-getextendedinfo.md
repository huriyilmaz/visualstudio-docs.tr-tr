---
title: IDebugProperty2::GetExtendedInfo | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721494"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Özellik için genişletilmiş bilgi alır.

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
[içinde] Alınacak genişletilmiş bilgi türünü belirleyen GUID. Ayrıntılar için Açıklamalar'a bakın.

`pExtendedInfo`\
[çıkış] Genişletilmiş `VARIANT` özellik bilgilerini almak için kullanılabilecek bir (C++) veya nesne (C#) döndürür. Örneğin, bu parametre bir `IUnknown` [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) arabirimi için sorgulanabilecek bir arabirim döndürebilir. Ayrıntılar için Açıklamalar'a bakın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde hata kodu döndürür. Alınacak `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` uzatılmış bilgi yoksa döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemini arayarak alınmasına kendini ödünç vermeyen bilgileri almak amacıyla vardır.

 Aşağıdaki GUID'ler genellikle bu yöntemle tanınır (AD herhangi bir derlemede kullanılamadığından GUID değerleri C# için belirtilir). Dahili kullanım için ek GUID'ler oluşturulabilir.

|Adı|GUID|Açıklama|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11d0-b47f-00a024a1dd2}|Belgeye `IUnknown` bir arabirim döndürür. Genellikle, [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) arabirimi bu `IUnknown` arabirimden elde edilebilir.|
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Belge `IUnknown` bağlamına bir arabirim döndürür. Genellikle, [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimi bu `IUnknown` arabirimden elde edilebilir.|
|guidCustomViewerDesteklenen|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Genellikle bir ifade değerlendiricisi tarafından uygulanan özel bir görüntüleyicinin CLSID'sini içeren bir dize döndürür.|
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Bu özellik yönetilen bir kod yerel adresi temsil ediyorsa, istenen yuva numarasını temsil eden 32 bitlik bir sayı döndürür.|
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Özellik nesnesi ile ilişkili değişkenin imzasını içeren bir dize döndürür.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
