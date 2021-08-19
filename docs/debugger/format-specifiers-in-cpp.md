---
title: Hata ayıklayıcı (C++) dosyasındaki biçim | Microsoft Docs
description: İzleme, Otomatikler veya Yereller penceresinde bir değerin görüntülendiğinde biçimi değiştirmek için biçim belirleyicisi kullanın. Bu makalede kullanım ayrıntıları velanmıştır.
ms.custom: SEO-VS-2020
ms.date: 3/11/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: f00e81ea202b59dde227e8cf31fbc0ca2975a595
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052102"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısında C++ için biçim belirleyicileri

Biçim belirleyicilerini kullanarak **İzleme,** Otomatikler ve Yereller pencerelerinde **bir** değerin görüntülenme biçimini değiştirebilirsiniz. 

Biçim belirleyicilerini Anında penceresinde,  Komut penceresinde, izleme [](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)noktalarında ve hatta kaynak pencerelerde de kullanabilirsiniz.  Bu pencerelerde bir ifadede duraklatılırsanız sonuç bir DataTip içinde [görünür.](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) DataTip görüntüsü biçim belirleyiciyi gösterir.

> [!NOTE]
> Yerel Visual Studio yeni bir hata ayıklama altyapısına değiştiriken, bazı yeni biçim belirleyicileri eklenmiştir ve bazı eskileri kaldırılmıştır. C++/CLI ile birlikte çalışma (yerel ve yönetilen karma) hata ayıklaması sırasında eski hata ayıklayıcı hala kullanılır.

## <a name="set-format-specifiers"></a>Biçim belirleyicilerini ayarlama

Aşağıdaki örnek kodu kullan kullanıruz:

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Hata `my_var1` ayıklarken değişkeni İzleme **penceresine** ekleyin, İzleme   >    >    >  **1'Windows ayıkla.** Ardından değişkenine sağ tıklayın ve **Onaltılık Görüntü'leri seçin.** Şimdi **İzleme penceresinde** 0x0065. Bu değeri tamsayı yerine karakter olarak ifade etmek için ilk olarak sağ tıklayın ve Onaltılık Görüntü **seçeneğinin işaretini kaldırın.** Ardından değişken adının ardından Ad sütununa **, c** **karakter** biçimi belirleyicisi ekleyin. Value **sütununda** artık **101 'e' değeri görüntülenir.**

![101 Visual Studio izleme penceresi 'e' my_var1 int türü ile my_var1.c'yi gösteren seçili bir satırın yer alan seçili satırın ekran görüntüsü.](../debugger/media/watchformatcplus1.png)

::: moniker range=">= vs-2019" 
İzleme penceresindeki değere virgül (,) ek olarak kullanılabilir biçim belirleyicileri listesinden seçim **ve** ekleyebilirsiniz. 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Biçim belirleyicileri

Aşağıdaki tablolarda, veri kaynaklarında kullanabileceğiniz biçim Visual Studio. Kalın yazı tipinde olan belirleyiciler yalnızca yeni hata ayıklayıcısı için desteklene, C++/CLI ile birlikte çalışma hata ayıklaması için desteklanmaz.

::: moniker range=">= vs-2019" 

|Belirleyici|Biçimlendir|Özgün İzleme Değeri|Görüntülenen Değer|
|---------------|------------|--------------------------|---------------------|
|d|ondalık tamsayı|0x00000066|102|
|o|unsigned octal integer|0x00000066|000000000146|
|x<br /><br /> **h**|onaltılık tamsayı|102|0xcccccccc|
|X<br /><br /> **H**|onaltılık tamsayı|102|0xCCCCCCCC|
|Xb<br /><br /> **Hb**|onaltılık tamsayı (başında 0x olmadan)|102|cccccccc|
|Xb<br /><br /> **Hb**|onaltılık tamsayı (başında 0x olmadan)|102|CCCCCCCC|
|b|unsigned binary integer|25|0b0000000000000000000000000000011001|
|bb|unsigned binary integer(baştaki 0b olmadan)|25|00000000000000000000000000011001|
|e|bilimsel gösterim|25000000|2.500000e+07|
|g|bilimsel veya kayan noktanın daha kısası|25000000|2,5e+07|
|c|tek karakter|0x0065|101 'e'|
|s|const char* dizesi (tırnak işaretleriyle)|\<location> "hello world"|"hello world"|
|**Sb**|const char* dizesi (tırnak işareti yok)|\<location> "hello world"|Merhaba Dünya|
|s8|UTF-8 dizesi|\<location> "Bu bir UTF-8 kahve fincanı ̃•"|"Bu bir UTF-8 kahve ☕"|
|**s8b**|UTF-8 dizesi (tırnak işareti yok)|\<location> "hello world"|Merhaba Dünya|
|su|Unicode (UTF-16 kodlama) dizesi (tırnak işaretleriyle)|\<location> L"hello world"|L"hello world"<br /><br /> u"hello world"|
|Alt|Unicode (UTF-16 kodlama) dizesi (tırnak işareti yok)|\<location> L"hello world"|Merhaba Dünya|
|bstr|BSTR ikili dizesi (tırnak işaretleriyle birlikte)|\<location> L "Merhaba Dünya"|L "Merhaba Dünya"|
|env|Ortam bloğu (çift boş sonlandırılmış dize)|\<location>L "=:: =:: \\ \\ "|L "=:: =:: \\ \\ \\ 0 = C: = C: \\ \\ Windows \\ \\ system32 \\ 0allusersprofıle =...|
|**s32**|UTF-32 dizesi (tırnak işaretleriyle birlikte)|\<location> U "Merhaba Dünya"|U "Merhaba Dünya"|
|**s32b**|UTF-32 dizesi (tırnak işareti yok)|\<location> U "Merhaba Dünya"|Merhaba Dünya|
|**en**|enum|Cumartesi (6)|Cumartesi|
|**HV**|İşaretçi türü-incelenen işaretçi değerinin, bir dizinin yığın ayırma sonucunun (örneğin,) sonucu olduğunu gösterir `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**yana**|Bir nesnenin bir işaretçisinin bellek adresini bastırır.|\<location>, {member = değer...}|{member = değer...}|
|**on**|Türetilmiş sınıfları yoksayarak yalnızca temel sınıf bilgisini görüntüler|`(Shape*) square` temel sınıf ve türetilmiş sınıf bilgilerini içerir|Yalnızca temel sınıf bilgisini görüntüler|
|sa|HRESULT veya Win32 hata kodu. Hata ayıklayıcı otomatik olarak onun kodunu çözen için bu tanımlayıcı artık HRESULTs için gerekli değildir.|S_OK|S_OK|
|WC|Pencere sınıfı bayrağı|0x0010|WC_DEFAULTCHAR|
|WM|Windows ileti numaraları|16|WM_CLOSE|
|n|"Ham görünüm" öğesini gösterme|
|nvo|Yalnızca sayısal değerler için "ham görünüm" öğesini göster|
|!|ham biçim, herhangi bir veri türü görünüm özelleştirmelerini yok sayılıyor|\<customized representation>|4|
|tutamaçlardan|Win32 tutamacı hakkındaki bilgileri görüntüler|0x000000000000009c| İş parçacığı KIMLIĞI vb. gibi tanıtıcı hakkında yararlı bilgiler görüntüler. |

::: moniker-end

::: moniker range="vs-2017" 

|Belirleyici|Biçimlendir|Özgün Izleme değeri|Değer görüntülendi|
|---------------|------------|--------------------------|---------------------|
|d|ondalık tamsayı|0x00000066|102|
|o|işaretsiz sekizlik tamsayı|0x00000066|000000000146|
|x<br /><br /> **h**|onaltılı tamsayı|102|0xcccccccc|
|X<br /><br /> **Olsun**|onaltılı tamsayı|102|0xCCCCCCCC|
|c|tek karakter|0x0065, c|101 ' e '|
|s|const char * dizesi (tırnak işaretleriyle birlikte)|\<location> "Merhaba Dünya"|"Merhaba Dünya"|
|**ise**|const char * dizesi (tırnak işareti yok)|\<location> "Merhaba Dünya"|Merhaba Dünya|
|S8|UTF-8 dizesi|\<location> "Bu bir UTF-8 kahve kupa â ̃ •"|"Bu bir UTF-8 kahve kupa ☕"|
|**s8b**|UTF-8 dizesi (tırnak işareti yok)|\<location> "Merhaba Dünya"|Merhaba Dünya|
|hecesi|Unicode (UTF-16 kodlama) dizesi (tırnak işaretleriyle birlikte)|\<location> L "Merhaba Dünya"|L "Merhaba Dünya"<br /><br /> u"hello world"|
|Alt|Unicode (UTF-16 kodlama) dizesi (tırnak işareti yok)|\<location> L"hello world"|Merhaba Dünya|
|bstr|BSTR ikili dizesi (tırnak işaretleriyle)|\<location> L"hello world"|L"hello world"|
|Env|Ortam bloğu (çift null sonlandırılan dize)|\<location>L"=::=:: \\ \\ "|L"=::=:: \\ \\ \\ 0=C:=C: \\ \\ windows \\ \\ system32 \\ 0ALLUSERSPROFILE=...|
|**s32**|UTF-32 dizesi (tırnak işaretleriyle)|\<location> U"hello world"|U"hello world"|
|**s32b**|UTF-32 dizesi (tırnak işareti yok)|\<location> U"hello world"|Merhaba Dünya|
|**en**|enum|Cumartesi(6)|Cumartesi|
|**Hv**|İşaretçi türü - denetlenen işaretçi değerinin bir dizinin yığın ayırma sonucu olduğunu gösterir, örneğin, `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**Na**|Bir nesnenin işaretçisinin bellek adresini bastırıyor.|\<location>, {member=value...}|{member=value...}|
|**Nd**|Türetilmiş sınıfları yoksayarak yalnızca temel sınıf bilgilerini görüntüler|`(Shape*) square` temel sınıf ve türetilmiş sınıf bilgilerini içerir|Yalnızca temel sınıf bilgilerini görüntüler|
|sa|HRESULT veya Win32 hata kodu. Hata ayıklayıcısı bunları otomatik olarak çözen hrESULTs için artık bu belirleyici gerekli değildir.|S_OK|S_OK|
|Wc|Pencere sınıfı bayrağı|0x0010|WC_DEFAULTCHAR|
|Wm|Windows numaralarını seçin|16|WM_CLOSE|
|!|ham biçim, veri türü görünüm özelleştirmelerini yoksayma|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> **hv biçim belirleyicisi** mevcut olduğunda, hata ayıklayıcı arabelleğin uzunluğunu belirlemeye ve bu öğe sayısını görüntülemeye çalışır. Hata ayıklayıcının bir dizinin tam arabellek boyutunu bulması her zaman mümkün olduğundan, mümkün olduğunda bir boyut `(pBuffer,[bufferSize])` belirleyicisi kullanılmalıdır. **hv** biçim belirleyicisi, arabellek boyutu hazır değilken kullanışlıdır.

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> İşaretçiler için dizi olarak boyut belirleyicileri

Dizi olarak görüntülemek istediğiniz bir nesnenin işaretçisi varsa, dizi öğelerinin sayısını belirtmek için bir tamsayı veya ifade kullanabilirsiniz.

|Belirleyici|Biçimlendir|Özgün İzleme Değeri|Görüntülenen Değer|
|---------------|------------|---------------------------|---------------------|
|n|Ondalık **veya onaltılık tamsayı**|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|`pBuffer`32 öğeli bir dizi olarak görüntülenir.|
|**[exp]**|Tamsayı olarak değerlendirilen geçerli bir C++ ifadesi.|pBuffer,[bufferSize]|pBuffer'ı bir öğe dizisi olarak `bufferSize` görüntüler.|
|**expand(n)**|Tamsayı olarak değerlendirilen geçerli bir C++ ifadesi|pBuffer, expand(2)|öğesinin üçüncü öğesini görüntüler  `pBuffer`|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> C++/CLI ile birlikte çalışma hata ayıklaması için biçim belirleyicileri

Kalın yazı **tipinde belirleyiciler** yalnızca yerel ve C++/CLI kodunda hata ayıklama için destek sağlar. Bu, Yönetilen Uyumluluk Modu kullanılarak belirtilen eski [hata ayıklayıcısını gerektirir.](../debugger/general-debugging-options-dialog-box.md)

|Belirleyici|Biçimlendir|Özgün İzleme Değeri|Görüntülenen Değer|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|imzalı ondalık tamsayı|0xF000F065|-268373915|
|**U**|unsigned decimal integer|0x0065|101|
|o|unsigned octal integer|0xF065|0170145|
|x<br /><br />X|Onaltılık tamsayı|61541|0x0000f065|
|**L**<br /><br />**h**|için uzun veya kısa ön ek: d, i, u, o, x, X|00406042|0x0c22|
|**F**|imzalı kayan nokta|(3./2.), f|1.500000|
|**E**|imzalı bilimsel nota|(3.0/2.0)|1.500000e+000|
|**G**|imzalı kayan nokta veya imzalı bilimsel nota,<br/> hangisi daha kısa ise|(3.0/2.0)|1,5|
|c|tek karakter|\<location>|101 'e'|
|s|const char* (tırnak işaretleriyle)|\<location>|"hello world"|
|su|const wchar_t*<br /><br /> const char16_t \* (tırnak işaretleriyle)|\<location>|L"hello world"|
|Alt|const wchar_t*<br /><br /> const char16_t\*|\<location>|Merhaba Dünya|
|s8|const char* (tırnak işaretleriyle)|\<location>|"hello world"|
|sa|HRESULT veya Win32 hata kodu.<br/>Hata ayıklayıcısı bunları otomatik olarak çözen hrESULTs için artık bu belirleyici gerekli değildir.|S_OK|S_OK|
|Wc|Pencere sınıfı bayrağı|0x00000040,|WC_DEFAULTCHAR|
|Wm|Windows numaralarını seçin|0x0010|WM_CLOSE|
|!|ham biçim, veri türü görünümü özelleştirmelerini yoksayma|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> C++/CLI ile birlikte çalışma hata ayıklamada bellek konumları için biçim belirleyicileri

Aşağıdaki tabloda bellek konumları için kullanılan biçimlendirme sembolleri açık almaktadır. Bir konum olarak değerlendirilen herhangi bir değer veya ifade ile bir bellek konumu belirleyicisi kullanabilirsiniz.

Kalın yazı **tipinde olan** belirleyiciler yalnızca yerel ve C++/CLI kodunda hata ayıklama için de destek sağlar. Bu, Yönetilen Uyumluluk Modu kullanılarak belirtilen eski [hata ayıklayıcısını gerektirir.](../debugger/general-debugging-options-dialog-box.md)

|Sembol|Biçimlendir|Özgün İzleme Değeri|Görüntülenen Değer|
|------------|------------|--------------------------|---------------------|
|**ma (ma)**|64 ASCII karakteri|0x0012ffac|0x0012ffac .4...0..." 0W&...... 1W&.0.:W.. 1....".. 1.JO&.1.2..". 1...0y...... 1|
|**m**|Onaltılık olarak 16 bayt, ardından 16 ASCII karakter|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4...0...". 0W&..|
|**Mb**|Onaltılık olarak 16 bayt, ardından 16 ASCII karakter|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4...0...". 0W&..|
|**Mw**|8 sözcük|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**md**|4 çift kelime|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**Mq**|2 dörtlü|0x0012ffac|0x0012ffac 7ffdf0000000000000 5f441a790012fdd4|
|**mu**|2-byte karakterleri (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> C++/CLI ile birlikte çalışma hata ayıklamada diziler olarak işaretçiler için boyut belirleyicisi

Dizi olarak görüntülemek istediğiniz bir nesnenin işaretçisi varsa, dizi öğelerinin sayısını belirtmek için bir tamsayı kullanabilirsiniz.

|Belirleyici|Biçimlendir|Expression|Görüntülenen Değer|
|---------------|------------|----------------|---------------------|
|n|Ondalık tamsayı|pBuffer[32]|`pBuffer`32 öğeli bir dizi olarak görüntülenir.|
