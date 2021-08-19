---
description: Dil ve satıcı tanımlayıcıları verilen kullanılabilir ifade değerlendiricileri numaralandırır.
title: 'IDebugSettingsCallback2:: Trmees | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 06a2c2572c1c4109cee4bdda5f5483be58a52f0f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118456"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Dil ve satıcı tanımlayıcıları verilen kullanılabilir ifade değerlendiricileri numaralandırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>Parametreler
`celtBuffer`\
'ndaki Arabellekteki öğe sayısı `pceltEEs` .

`rgguidLang`\
[in, out] Programlama dili için benzersiz tanımlayıcı.

`rgguidVendor`\
[in, out] Satıcı için benzersiz tanımlayıcı.

`pceltEEs`\
[in, out] Değerlendiricileri ifadesinin dizisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
