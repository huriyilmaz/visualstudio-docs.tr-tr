---
description: Alınacak sembol bilgisinin türünü belirtir.
title: SYMBOL_SEARCH_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b83ca25a3bd2d9f97f5646e98189f4400885be622859ea1594889f260b8b49f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448539"
---
# <a name="symbol_search_info_fields"></a>SYMBOL_SEARCH_INFO_FIELDS
Alınacak sembol bilgisinin türünü belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;
```

```csharp
public enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};

```

## <a name="fields"></a>Alanlar
 `SSIF_NONE`\
 Bayrak olmadığını gösterir

 `SSIF_VERBOSE_SEARCH_INFO`\
 Sembolleri bulmak için kullanılan tüm arama yollarını döndürür

## <a name="remarks"></a>Açıklamalar
 Bu bayraklar döndürülen bilgi miktarını öğrenmek için [Getsymbolınfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) yöntemine bir parametre olarak geçirilir.

> [!NOTE]
> Şu anda yalnızca `SSIF_VERBOSE_SEARCH_INFO` destekleniyor ve parametresi olarak belirtilmelidir `dwFlags` `IDebugModule3::GetSymbolInfo` . Diğer tüm değerler bir hata döndürür.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
