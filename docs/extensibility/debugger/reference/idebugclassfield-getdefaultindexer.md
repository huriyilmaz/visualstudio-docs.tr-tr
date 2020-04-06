---
title: IDebugClassField::GetDefaultIndexer | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57e00107374485043af370967794bdade1c213d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734427"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Varsayılan dizinleyicinin adını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>Parametreler
`pbstrIndexer`[çıkış] Varsayılan dizinleyicinin adını içeren bir dize döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, varsayılan dizinleyici yoksa S_OK döndürür veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir sınıfın varsayılan dizinleyicisi, dizi `Default` erişimleri için özellik olarak işaretlenen özelliktir. Bu [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]özeldir. Burada, bildirilen varsayılan [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] dizinleyicive nasıl kullanıldığına bir örnek verilmiştir.

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
