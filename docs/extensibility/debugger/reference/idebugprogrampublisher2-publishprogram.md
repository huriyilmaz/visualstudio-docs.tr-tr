---
title: IDebugProgramPublisher2::PublishProgram | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20de162bdc3be2cc4771c9746b13c40a1e140a96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721678"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Bu yöntem, hata ayıklama motorları (DEs) ve oturum hata ayıklama yöneticisi için bir program kullanılabilir hale getirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

## <a name="parameters"></a>Parametreler
`Engines`\
[içinde] Bu programı başlatabilen veya ekleyen D'ler için bir dizi GUID.

`szFriendlyName`\
[içinde] Programın dostu adı (bu kullanıcıya sunulan menülerde veya iletişim lerde görünür).

`pDebuggeeInterface`\
[içinde] `IUnknown` program için arayüz (bu değer programı benzersiz tanımlamak için bir çerez olarak kullanılır; bu aynı değer programı "yayımlamamak" için kullanılır)

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir programı hata ayıklama için artık kullanılamıyor yapmak için [Yayımlama Programı'nı](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
