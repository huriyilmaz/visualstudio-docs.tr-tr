---
description: Bu yöntem, bir programı hata ayıklama motorları (DEs) ve oturum hata ayıklama Yöneticisi için kullanılabilir hale getirir.
title: IDebugProgramPublisher2::P ublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a99f79d9a9f8b087720a86dc6184b69715bf15c3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096095"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Bu yöntem, bir programı hata ayıklama motorları (DEs) ve oturum hata ayıklama Yöneticisi için kullanılabilir hale getirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

## <a name="parameters"></a>Parametreler
`Engines`\
'ndaki Bu programı başlatabileceği veya bu programa ekleyebileceğiniz DEs için GUID dizisi.

`szFriendlyName`\
'ndaki Program için kolay ad (Bu, kullanıcıya sunulan menülerde veya iletişim kutularında görünür).

`pDebuggeeInterface`\
[in] `IUnknown` program arabirimi (Bu değer programı benzersiz bir şekilde tanımlamak için bir tanımlama bilgisi olarak kullanılır; Bu aynı değer programı "yayımdan kaldırmak" için kullanılır)

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir programı artık hata ayıklama için kullanılamaz hale getirmek için, [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)' ı çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
