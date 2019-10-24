---
title: 'IDiaSymbol:: get_undecoratedNameEx | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48efbc249d076853e12bc54d2e8a8d438570e740
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738988"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
C++ Düzenlenmiş (bağlantı) adı için, açıklanunan bir adın bir kısmını veya tamamını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>Parametreler
 `undecoratedOptions`

'ndaki Döndürülecek olan bayrakları denetleyen bayrakların birleşimini belirtir. Belirli değerler ve ne yapacaklarınız için açıklamalar bölümüne bakın.

 `pRetVal`

dışı Düzenlenmiş bir C++ ad için, açıklanmunadı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 @No__t_0 aşağıdaki bayrakların bir birleşimi olabilir.

> [!NOTE]
> Bayrak adları DIA SDK tanımlı değildir, bu nedenle kodunuza bildirimleri eklemeniz ya da ham değerleri kullanmanız gerekir.

|bayrağıyla|Değer|Açıklama|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|Tam dekorasyonu sunar.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Microsoft genişletilmiş anahtar sözcüklerinden önde gelen alt çizgileri kaldırır.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Microsoft genişletilmiş anahtar sözcükleri genişletmeyi devre dışı bırakır.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Birincil bildirim için dönüş türü genişletmeyi devre dışı bırakır.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Bildirim modelinin genişlemesine devre dışı bırakır.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Bildirim dili belirticisi genişletmeyi devre dışı bırakır.|
|UNDNAME_RESERVED1|0x0020|Ayrılamadı.|
|UNDNAME_RESERVED2|0x0040|Ayrılamadı.|
|UNDNAME_NO_THISTYPE|0x0060|@No__t_0 türündeki tüm değiştiricileri devre dışı bırakır.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Üyeler için erişim belirticileri genişletmeyi devre dışı bırakır.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|İşlevler ve işlevlere işaretçiler için "throw-imzalar" genişletmeyi devre dışı bırakır.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|@No__t_0 veya `virtual` üyelerini genişletmeyi devre dışı bırakır.|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|UDT için Microsoft modelinin genişlemesini devre dışı bırakır.|
|UNDNAME_32_BIT_DECODE|0x0800|32 bitlik adları dekorunlaştırır.|
|UNDNAME_NAME_ONLY|0x1000|Yalnızca birincil bildirimin adını alır; yalnızca [Scope::] adını döndürür.  Şablon params 'i genişletir.|
|UNDNAME_TYPE_ONLY|0x2000|Giriş yalnızca bir tür kodlaması; Soyut bildirimci oluşturur.|
|UNDNAME_HAVE_PARAMETERS|0x4000|Gerçek şablon parametreleri kullanılabilir.|
|UNDNAME_NO_ECSU|0x8000|Enum/class/struct/Union 'yi bastırır.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Geçerli tanımlayıcı karakterlerinin denetimini bastırır.|
|UNDNAME_NO_PTR64|0x20000|Çıkışa Ptr64 içermez.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)