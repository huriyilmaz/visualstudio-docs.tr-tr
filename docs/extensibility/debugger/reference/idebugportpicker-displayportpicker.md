---
description: Kullanıcının bir bağlantı noktası seçmesini sağlayan, belirtilen iletişim kutusunu görüntüler.
title: Idebugportpicker::D ıplayportpicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a49c1379d2bb3946f75eddd9d80bdccdb370d3ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072318"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Kullanıcının bir bağlantı noktası seçmesini sağlayan, belirtilen iletişim kutusunu görüntüler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Parametreler
`hwndParentDialog`\
'ndaki Üst iletişim kutusu için tanıtıcı.

`pbstrPortId`\
dışı Bağlantı noktası tanımlayıcı dizesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Dönüş değeri `S_FALSE` (veya `S_OK` `BSTR` olarak ayarlandığı küme `NULL` ), kullanıcının **iptal 'e** tıkladığını gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
