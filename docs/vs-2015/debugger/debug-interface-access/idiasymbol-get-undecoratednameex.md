---
title: 'IDiaSymbol:: get_undecoratedNameEx | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9c50f5d352d8a52b0eb8b125992b2c325e48234
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811869"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

C++ ile düzenlenmiş (bağlantı) adı için, açıklanmamalıdır bir adın bir kısmını veya tamamını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `undecoratedOptions`  
 'ndaki Döndürülecek olan bayrakları denetleyen bayrakların birleşimini belirtir. Belirli değerler ve ne yapacaklarınız için açıklamalar bölümüne bakın.  
  
 `pRetVal`  
 dışı C++ ile düzenlenmiş bir ad için, açıklanmunadı döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.  
  
## <a name="remarks"></a>Açıklamalar  
 `undecorateOptions`Aşağıdaki bayrakların bir birleşimi olabilir.  
  
> [!NOTE]
> Bayrak adları DIA SDK tanımlı değildir, bu nedenle kodunuza bildirimleri eklemeniz ya da ham değerleri kullanmanız gerekir.  
  
|Bayrak|Değer|Açıklama|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Tam dekorasyonu sunar.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Microsoft genişletilmiş anahtar sözcüklerinden önde gelen alt çizgileri kaldırır.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Microsoft genişletilmiş anahtar sözcükleri genişletmeyi devre dışı bırakır.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Birincil bildirim için dönüş türü genişletmeyi devre dışı bırakır.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Bildirim modelinin genişlemesine devre dışı bırakır.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Bildirim dili belirticisi genişletmeyi devre dışı bırakır.|  
|UNDNAME_RESERVED1|0x0020|Ayrılamadı.|  
|UNDNAME_RESERVED2|0x0040|Ayrılamadı.|  
|UNDNAME_NO_THISTYPE|0x0060|Türdeki tüm değiştiricileri devre dışı bırakır `this` .|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Üyeler için erişim belirticileri genişletmeyi devre dışı bırakır.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|İşlevler ve işlevlere işaretçiler için "throw-imzalar" genişletmeyi devre dışı bırakır.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Veya üyeleri genişletmeyi devre dışı bırakır `static` `virtual` .|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|UDT için Microsoft modelinin genişlemesini devre dışı bırakır.|  
|UNDNAME_32_BIT_DECODE|0x0800|32 bitlik adları dekorunlaştırır.|  
|UNDNAME_NAME_ONLY|0x1000|Yalnızca birincil bildirimin adını alır; yalnızca [Scope::] adını döndürür.  Şablon params 'i genişletir.|  
|UNDNAME_TYPE_ONLY|0x2000|Giriş yalnızca bir tür kodlaması; Soyut bildirimci oluşturur.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Gerçek şablon parametreleri kullanılabilir.|  
|UNDNAME_NO_ECSU|0x8000|Enum/class/struct/Union 'yi bastırır.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Geçerli tanımlayıcı karakterlerinin denetimini bastırır.|  
|UNDNAME_NO_PTR64|0x20000|Çıkışa Ptr64 içermez.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
