---
title: Hata ayıklayıcıda biçim belirticileri (C++) | Microsoft Docs
description: Bir değerin Watch, oto veya Locals penceresinde görüntüleneceği biçimi değiştirmek için bir Biçim belirleyicisi kullanın. Bu makalede kullanım ayrıntıları sağlanmaktadır.
ms.custom: SEO-VS-2020
ms.date: 3/11/2019
ms.topic: conceptual
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
ms.openlocfilehash: 84f62c6c98e677de242482b055502c54451367af
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803914"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısında C++ için biçim belirticileri

Biçim belirticilerini kullanarak, bir değerin **Watch**, **oto** ve **Yereller** pencerelerinde görüntüleneceği biçimi değiştirebilirsiniz.

Biçim belirticilerini **hemen** penceresinde, **komut** penceresinde, [izlenenoktalarda](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints), hatta kaynak penceresinde de kullanabilirsiniz. Bu pencerelerin bir ifadesinde durakladıysanız, sonuç bir [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)içinde görüntülenir. Veri Ipucu ekranı, biçim belirticisini yansıtır.

> [!NOTE]
> Visual Studio yerel hata ayıklayıcı yeni bir hata ayıklama altyapısına değiştiği zaman, bazı yeni biçim belirticileri eklenmiştir ve eskileri kaldırılmıştır. Daha eski hata ayıklayıcı, C++/CLIILE birlikte çalışma (karma yerel ve yönetilen) hata ayıklaması yaparken hala kullanılır.

## <a name="set-format-specifiers"></a>Biçim belirticilerini ayarla

Aşağıdaki örnek kodu kullanacağız:

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

`my_var1`hata ayıklama sırasında değişkeni **izleme** penceresine ekleyin, **hata ayıkla**  >  **Windows**  >  **izle**  >  **izleyin 1**. Sonra, değişkene sağ tıklayıp **onaltılık görüntü**' i seçin. Şimdi **İzle** penceresinde 0x0065 değeri gösterilir. Bu değeri bir tamsayı yerine bir karakter olarak ifade etmek için, önce sağ tıklayıp **onaltılık ekran** seçimini kaldırın. Ardından, değişken adından sonra **ad** sütununa **c** karakter Biçim belirleyicisi ekleyin. **Değer** sütununda şimdi **101 ' e '** gösterilmektedir.

![101 ' e ' değeri ve bir int türü ile my_var1. c ' i gösteren, seçili bir satırla Visual Studio izleme penceresi ekran görüntüsü.](../debugger/media/watchformatcplus1.png)

::: moniker range=">= vs-2019" 
**İzleme** penceresindeki değere bir virgül (,) ekleyerek kullanılabilir biçim belirticileri listesinden görüntüleyebilir ve seçim yapabilirsiniz. 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Biçim belirticileri

Aşağıdaki tablolarda, Visual Studio kullanabileceğiniz biçim belirticileri açıklanır. Kalın olmayan tanımlayıcılar yalnızca yeni hata ayıklayıcı için desteklenir ve C++/CLIILE birlikte çalışma hata ayıklaması için desteklenmez.

::: moniker range=">= vs-2019" 

|Belirleyici|Biçimlendir|Özgün Izleme değeri|Değer görüntülendi|
|---------------|------------|--------------------------|---------------------|
|d|ondalık tamsayı|0x00000066|102|
|o|işaretsiz sekizlik tamsayı|0x00000066|000000000146|
|x<br /><br /> **h**|onaltılı tamsayı|102|0xcccccccc|
|X<br /><br /> **Olsun**|onaltılı tamsayı|102|0xCCCCCCCC|
|XB<br /><br /> **HB**|onaltılık tamsayı (baştaki 0x olmadan)|102|cccccccc|
|XB<br /><br /> **HB**|onaltılık tamsayı (baştaki 0x olmadan)|102|CCCCCCCC|
|b|işaretsiz ikili tamsayı|25|0b00000000000000000000000000011001|
|bb|işaretsiz ikili tamsayı (önde 0b olmadan)|25|00000000000000000000000000011001|
|e|bilimsel gösterim|25000000|2.500000 e + 07|
|g|bilimsel veya kayan noktanın kısalı|25000000|2.5 e + 07|
|c|tek karakter|0x0065|101 ' e '|
|s|const char * dizesi (tırnak işaretleriyle birlikte)|\<location> "Merhaba Dünya"|"Merhaba Dünya"|
|**ise**|const char * dizesi (tırnak işareti yok)|\<location> "Merhaba Dünya"|Merhaba Dünya|
|S8|UTF-8 dizesi|\<location> "Bu bir UTF-8 kahve kupa â ̃ •"|"Bu bir UTF-8 kahve kupa ☕"|
|**s8b**|UTF-8 dizesi (tırnak işareti yok)|\<location> "Merhaba Dünya"|Merhaba Dünya|
|hecesi|Unicode (UTF-16 kodlama) dizesi (tırnak işaretleriyle birlikte)|\<location> L "Merhaba Dünya"|L "Merhaba Dünya"<br /><br /> u "Merhaba Dünya"|
|alt|Unicode (UTF-16 kodlaması) dizesi (tırnak işareti yok)|\<location> L "Merhaba Dünya"|Merhaba Dünya|
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
|Nr|"Ham Görünüm" öğesini gizleme|
|nvo|Yalnızca sayısal değerler için "Ham Görünüm" öğesini göster|
|!|ham biçim, veri türü görünüm özelleştirmelerini yoksayma|\<customized representation>|4|
|Işlemek|win32 tanıtıcısı hakkında bilgileri görüntüler|0x000000000000009c| İş parçacığı kimliği gibi tanıtıcılar hakkında yararlı bilgileri görüntüler. |

::: moniker-end

::: moniker range="vs-2017" 

|Belirleyici|Biçimlendir|Özgün İzleme Değeri|Görüntülenen Değer|
|---------------|------------|--------------------------|---------------------|
|d|ondalık tamsayı|0x00000066|102|
|o|unsigned octal integer|0x00000066|000000000146|
|x<br /><br /> **h**|onaltılık tamsayı|102|0xcccccccc|
|X<br /><br /> **H**|onaltılık tamsayı|102|0xCCCCCCCC|
|c|tek karakter|0x0065, c|101 'e'|
|s|const char* dizesi (tırnak işaretleriyle)|\<location> "hello world"|"hello world"|
|**Sb**|const char* dizesi (tırnak işareti yok)|\<location> "hello world"|Merhaba Dünya|
|s8|UTF-8 dizesi|\<location> "Bu bir UTF-8 kahve fincanı ̃•"|"Bu bir UTF-8 kahve fincanı ☕"|
|**s8b**|UTF-8 dizesi (tırnak işareti yok)|\<location> "hello world"|Merhaba Dünya|
|su|Unicode (UTF-16 kodlama) dizesi (tırnak işaretleriyle)|\<location> L"hello world"|L"hello world"<br /><br /> u "Merhaba Dünya"|
|alt|Unicode (UTF-16 kodlaması) dizesi (tırnak işareti yok)|\<location> L "Merhaba Dünya"|Merhaba Dünya|
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
|!|ham biçim, herhangi bir veri türü görünüm özelleştirmelerini yok sayılıyor|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> **HV** Biçim belirleyicisi olduğunda, hata ayıklayıcı arabelleğin uzunluğunu saptamaya çalışır ve bu sayıda öğeyi görüntüler. Hata ayıklayıcının bir dizinin tam arabellek boyutunu bulması her zaman mümkün olmadığından, mümkün olduğunda bir boyut belirleyicisi kullanmanız gerekir `(pBuffer,[bufferSize])` . Arabellek boyutu hazır olmadığında **HV** Biçim belirleyicisi yararlıdır.

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Diziler için boyut belirticileri dizi olarak işaretçiler

Bir dizi olarak görüntülemek istediğiniz bir nesne işaretçiniz varsa, dizi öğelerinin sayısını belirtmek için bir tamsayı veya bir ifade kullanabilirsiniz.

|Belirleyici|Biçimlendir|Özgün Izleme değeri|Değer görüntülendi|
|---------------|------------|---------------------------|---------------------|
|n|Decimal veya **on altılı** tamsayı|pBuffer, [32]<br /><br /> pBuffer,**[0x20]**|`pBuffer`32 öğe dizisi olarak görüntüler.|
|**exp**|Tamsayı sonucunu veren geçerli bir C++ ifadesi.|pBuffer, [bufferSize]|PBuffer öğelerini dizi olarak görüntüler `bufferSize` .|
|**Genişlet (n)**|Tamsayı olarak değerlendirilen geçerli bir C++ ifadesi|pBuffer, Genişlet (2)|Öğesinin üçüncü öğesini görüntüler  `pBuffer`|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> C++/CLı ile birlikte çalışma hata ayıklaması için biçim belirticileri

**Kalın** olmayan tanımlayıcılar yalnızca yerel ve C++/CLI kodunda hata ayıklamak için desteklenir. Bu, [yönetilen uyumluluk modu](../debugger/general-debugging-options-dialog-box.md)kullanılarak belirtilen eski hata ayıklayıcıyı gerektirir.

|Belirleyici|Biçimlendir|Özgün Izleme değeri|Değer görüntülendi|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|işaretli ondalık tamsayı|0xF000F065|-268373915|
|**larınız**|işaretsiz ondalık tamsayı|0x0065|101|
|o|işaretsiz sekizlik tamsayı|0xF065|0170145|
|x<br /><br />X|Onaltılı tamsayı|61541|0x0000F065|
|**girişindeki**<br /><br />**h**|için uzun veya kısa ön ek: d, i, u, o, x, X|00406042|0x0c22|
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
|**Mq**|2 dörtlü|0x0012ffac|0x0012ffac 7ffdf000000000000 5f441a790012fdd4|
|**mu**|2-byte karakterleri (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> C++/CLI ile birlikte çalışma hata ayıklamada diziler olarak işaretçiler için boyut belirleyicisi

Dizi olarak görüntülemek istediğiniz bir nesnenin işaretçisi varsa, dizi öğelerinin sayısını belirtmek için bir tamsayı kullanabilirsiniz.

|Belirleyici|Biçimlendir|Expression|Görüntülenen Değer|
|---------------|------------|----------------|---------------------|
|n|Ondalık tamsayı|pBuffer[32]|`pBuffer`32 öğeli bir dizi olarak görüntülenir.|
