---
title: Hata ayıklayıcıda biçim belirticileri (C++) | Microsoft Docs
description: Bir değerin Watch, oto veya Locals penceresinde görüntüleneceği biçimi değiştirmek için bir Biçim belirleyicisi kullanın. Bu makalede kullanım ayrıntıları sağlanmaktadır.
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
ms.workload:
- cplusplus
ms.openlocfilehash: 868c02091814fe49ea0224190c7d205e8b67c42b
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042983"
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

`my_var1`Hata ayıklama sırasında değişkeni **izleme** penceresine ekleyin, Windows Watch 'da **hata ayıklama**  >    >    >  **1**' i izleyin. Sonra, değişkene sağ tıklayıp **onaltılık görüntü**' i seçin. Şimdi **İzle** penceresinde 0x0065 değeri gösterilir. Bu değeri bir tamsayı yerine bir karakter olarak ifade etmek için, önce sağ tıklayıp **onaltılık ekran** seçimini kaldırın. Ardından, değişken adından sonra **ad** sütununa **c** karakter Biçim belirleyicisi ekleyin. **Değer** sütununda şimdi **101 ' e '** gösterilmektedir.

![Visual Studio izleme penceresi ekran görüntüsü, bir değeri 101 ' e ' ve bir int türü olan my_var1. c ' i gösteren seçili bir satırla görüntüler.](../debugger/media/watchformatcplus1.png)

::: moniker range=">= vs-2019" 
**İzleme** penceresindeki değere bir virgül (,) ekleyerek kullanılabilir biçim belirticileri listesinden görüntüleyebilir ve seçim yapabilirsiniz. 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Biçim belirticileri

Aşağıdaki tablolarda, Visual Studio 'da kullanabileceğiniz biçim belirticileri açıklanır. Kalın olmayan tanımlayıcılar yalnızca yeni hata ayıklayıcı için desteklenir ve C++/CLIILE birlikte çalışma hata ayıklaması için desteklenmez.

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
|sa|HRESULT veya Win32 hata kodu. Hata ayıklayıcısı bunları otomatik olarak çözttükleri için bu belirleyici artık HRESULTs için gerekli değildir.|S_OK|S_OK|
|Wc|Pencere sınıfı bayrağı|0x0010|WC_DEFAULTCHAR|
|Wm|Windows ileti numaraları|16|WM_CLOSE|
|Nr|"Ham Görünüm" öğesini gizleme|
|nvo|Yalnızca sayısal değerler için "Ham Görünüm" öğesini göster|
|!|ham biçim, herhangi bir veri türü görünüm özelleştirmelerini yoksayma|\<customized representation>|4|
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
|su|Unicode (UTF-16 kodlama) dizesi (tırnak işaretleriyle)|\<location> L"hello world"|L"hello world"<br /><br /> u"hello world"|
|Alt|Unicode (UTF-16 kodlama) dizesi (tırnak işareti yok)|\<location> L"hello world"|Merhaba Dünya|
|bstr|BSTR ikili dizesi (tırnak işaretleriyle)|\<location> L"hello world"|L"hello world"|
|Env|Ortam bloğu (çift null sonlandırılan dize)|\<location>L"=::=:: \\ \\ "|L"=::=:: \\ \\ \\ 0=C:=C: \\ \\ windows \\ \\ system32 \\ 0ALLUSERSPROFILE=...|
|**s32**|UTF-32 dizesi (tırnak işaretleriyle)|\<location> U"hello world"|U"hello world"|
|**s32b**|UTF-32 dizesi (tırnak işareti yok)|\<location> U"hello world"|Merhaba Dünya|
|**en**|enum|Cumartesi(6)|Cumartesi|
|**Hv**|İşaretçi türü - denetlenen işaretçi değerinin bir dizinin yığın ayırma sonucu olduğunu gösterir, örneğin, `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**Na**|Bir nesnenin işaretçisinin bellek adresini bastırıyor.|\<location>, {member=value...}|{member=value...}|
|**Nd**|Türetilmiş sınıfları yoksayarak yalnızca temel sınıf bilgilerini görüntüler|`(Shape*) square` temel sınıf ve türetilmiş sınıf bilgilerini içerir|Yalnızca temel sınıf bilgilerini görüntüler|
|sa|HRESULT veya Win32 hata kodu. Hata ayıklayıcısı bunları otomatik olarak çözttükleri için bu belirleyici artık HRESULTs için gerekli değildir.|S_OK|S_OK|
|Wc|Pencere sınıfı bayrağı|0x0010|WC_DEFAULTCHAR|
|Wm|Windows ileti numaraları|16|WM_CLOSE|
|!|ham biçim, herhangi bir veri türü görünüm özelleştirmelerini yoksayma|\<customized representation>|4|

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

Kalın yazı **tipinde belirleyiciler** yalnızca yerel ve C++/CLI kodunda hata ayıklama için de destek sağlar. Bu, Yönetilen Uyumluluk Modu kullanılarak belirtilen eski [hata ayıklayıcısını gerektirir.](../debugger/general-debugging-options-dialog-box.md)

|Belirleyici|Biçimlendir|Özgün İzleme Değeri|Görüntülenen Değer|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|imzalı ondalık tamsayı|0xF000F065|-268373915|
|**U**|unsigned decimal integer|0x0065|101|
|o|unsigned octal integer|0xF065|0170145|
|x<br /><br />X|Onaltılık tamsayı|61541|0x0000f065|
|**L**<br /><br />**h**|için uzun veya kısa ön ek: d, i, u, o, x, X|00406042|0x0c22|
|**vadeli**|işaretli kayan nokta|(3./2.), f|1,500000|
|**a**|imzalanmış bilimsel gösterim|(3.0/2.0)|1.500000 e + 000|
|**Acil**|işaretli kayan nokta veya imzalanmış bilimsel gösterim,<br/> Hangisi daha kısadır|(3.0/2.0)|1,5|
|c|tek karakter|\<location>|101 ' e '|
|s|const char * (tırnak işaretleriyle birlikte)|\<location>|"Merhaba Dünya"|
|hecesi|const wchar_t *<br /><br /> const char16_t \* (tırnak işaretleriyle birlikte)|\<location>|L "Merhaba Dünya"|
|alt|const wchar_t *<br /><br /> const char16_t\*|\<location>|Merhaba Dünya|
|S8|const char * (tırnak işaretleriyle birlikte)|\<location>|"Merhaba Dünya"|
|sa|HRESULT veya Win32 hata kodu.<br/>Hata ayıklayıcı otomatik olarak onun kodunu çözen için bu tanımlayıcı artık HRESULTs için gerekli değildir.|S_OK|S_OK|
|WC|Pencere sınıfı bayrağı|0x00000040|WC_DEFAULTCHAR|
|WM|Windows ileti numaraları|0x0010|WM_CLOSE|
|!|ham biçim, veri türü görünüm özelleştirmelerini yok sayılıyor|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> C++/CLı ile birlikte çalışma hata ayıklaması içindeki bellek konumlarına yönelik biçim belirticileri

Aşağıdaki tabloda bellek konumları için kullanılan biçimlendirme sembolleri açıklanmaktadır. Bir konum için değerlendirilen herhangi bir değer veya ifadeyle bir bellek Konum Belirleyicisi kullanabilirsiniz.

**Kalın** olmayan tanımlayıcılar yalnızca yerel ve C++/CLI kodunda hata ayıklamak için desteklenir. Bu, [yönetilen uyumluluk modu](../debugger/general-debugging-options-dialog-box.md)kullanılarak belirtilen eski hata ayıklayıcıyı gerektirir.

|Sembol|Biçimlendir|Özgün Izleme değeri|Değer görüntülendi|
|------------|------------|--------------------------|---------------------|
|**hareketli**|64 ASCII karakter|0x0012ffac|0x0012ffac. 4... 0... 0W&....... 1W&.0.: W.. 1.... ".. 1.JO&.1,2... 1... 0y.... 1|
|**m**|16 bayt, onaltılı ve ardından 16 ASCII karakter|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0... ". 0W&..|
|**'lık**|16 bayt, onaltılı ve ardından 16 ASCII karakter|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0... ". 0W&..|
|**MW**|8 sözcük|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**MD**|4 doublesözcük|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**yazılımını**|2 çeyrek sözcük|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**mu**|2 baytlık karakterler (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> C++/CLı ile birlikte çalışma hata ayıklaması içinde diziler olarak işaretçiler için boyut Belirleyicisi

Bir dizi olarak görüntülemek istediğiniz bir nesne işaretçiniz varsa, dizi öğelerinin sayısını belirtmek için bir tamsayı kullanabilirsiniz.

|Belirleyici|Biçimlendir|Expression|Değer görüntülendi|
|---------------|------------|----------------|---------------------|
|n|Ondalık tamsayı|pBuffer [32]|`pBuffer`32 öğeli dizi olarak görüntülenir.|
