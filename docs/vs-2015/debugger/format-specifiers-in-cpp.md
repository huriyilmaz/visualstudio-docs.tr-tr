---
title: C++ ' da biçim belirticileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f620cbf5d522b99965268f35c00ff8e874f1542
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64834170"
---
# <a name="format-specifiers-in-c"></a>C++ içindeki Biçim Belirticileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Biçim belirticilerini kullanarak **izleme** penceresinde bir değerin görüntülendiği biçimi değiştirebilirsiniz.  
  
 Biçim belirticilerini **hemen** penceresinde, **komut** penceresinde ve hatta kaynak penceresinde de kullanabilirsiniz. Bu pencerelerin bir ifadesinde durakladıysanız, sonuç bir DataTip içinde görüntülenir. Veri Ipucu ekranı, biçim belirticisini yansıtır.  
  
> [!NOTE]
> Visual Studio yerel hata ayıklayıcı yeni bir hata ayıklama altyapısına değiştirildi. Bu değişikliğin bir parçası olarak, bazı yeni biçim belirticileri eklenmiştir ve eskileri kaldırılmıştır. Daha eski hata ayıklayıcı, C++/CLIILE birlikte çalışma (karma yerel ve yönetilen) hata ayıklaması yaparken hala kullanılır. Bu konudaki aşağıdaki bölümlerde, her hata ayıklama altyapısının biçim belirticileri gösterilmektedir.  
> 
> - [Biçim belirticileri](#BKMK_Visual_Studio_2012_format_specifiers) , yeni hata ayıklama altyapısındaki biçim belirticilerini açıklar.  
>   - [C++/CLI ile birlikte çalışma hata ayıklaması Için biçim belirticileri](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) , eski hata ayıklama altyapısından biçim belirticilerini tanımlar.  
  
## <a name="using-format-specifiers"></a>Biçim belirticilerini kullanma  
 Aşağıdaki koda sahipseniz:  
  
```cpp  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Değişkeni, `my_var1` **izleme** penceresine ekleyin (hata ayıklama, hata ayıklama **/Windows/izleme/izleme 1**) ve ekranı onaltılı olarak ayarlama ( **Gözcü** penceresinde, değişkene sağ tıklayıp **onaltılık görüntü**' i seçin). Artık izleme penceresi, 0x0065 değerini içerdiğini gösterir. Bu değeri bir tamsayı yerine bir karakter olarak ifade eden bir tamsayı olarak görmek için, ad sütununda, değişken adından sonra, **c**karakter Biçim belirleyicisi ekleyin. **Değer** sütunu artık **101 ' e '** ile görünür.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Biçim belirticileri  
 Aşağıdaki tablolarda, Visual Studio 'da kullanabileceğiniz biçim belirticileri gösterilmektedir. Kalın olmayan tanımlayıcılar, C++/CLIILE birlikte çalışma hata ayıklaması için desteklenmez.  
  
|Belirleyici|Biçimlendir|Özgün Izleme değeri|Değer görüntülendi|  
|---------------|------------|--------------------------|---------------------|  
|d|ondalık tamsayı|0x00000066|102|  
|o|işaretsiz sekizlik tamsayı|0x00000066|000000000146|  
|x<br /><br /> **olsun**|onaltılı tamsayı|102|0xcccccccc|  
|X<br /><br /> **H**|onaltılı tamsayı|102|0xCCCCCCCC|  
|c|tek karakter|0x0065, c|101 ' e '|  
|s|const char * dizesi|\<location> "Merhaba Dünya"|"Merhaba Dünya"|  
|**ise**|const char * dizesi|\<location> "Merhaba Dünya"|Merhaba Dünya|  
|S8|const char * dizesi|\<location> "Merhaba Dünya"|"Merhaba Dünya"|  
|**s8b**|const char * dizesi|\<location> "Merhaba Dünya"|"Merhaba Dünya"|  
|hecesi|const wchar_t * const<br /><br /> char16_t \* dize|\<location> L "Merhaba Dünya"|L "Merhaba Dünya"<br /><br /> u "Merhaba Dünya"|  
|alt|const wchar_t * const<br /><br /> char16_t \* dize|\<location> L "Merhaba Dünya"|Merhaba Dünya|  
|bstr|BSTR dizesi|\<location> L "Merhaba Dünya"|L "Merhaba Dünya"|  
|**s32**|UTF-32 dizesi|\<location> U "Merhaba Dünya"|U "Merhaba Dünya"|  
|**s32b**|UTF-32 dizesi (tırnak işareti yok)|\<location> U "Merhaba Dünya"|Merhaba Dünya|  
|**Em**|enum|Cumartesi (6)|Cumartesi|  
|**HV**|İşaretçi türü-incelenen işaretçi değerinin, bir dizinin yığın ayırma sonucunun (örneğin,) sonucu olduğunu gösterir `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, …}|  
|**yana**|Bir nesnenin bir işaretçisinin bellek adresini bastırır.|\<location>, {member = değer...}|{member = değer...}|  
|**on**|Türetilmiş sınıfları yoksayarak yalnızca temel sınıf bilgisini görüntüler|`(Shape*) square` temel sınıf ve türetilmiş sınıf bilgilerini içerir|Yalnızca temel sınıf bilgisini görüntüler|  
|sa|HRESULT veya Win32 hata kodu. (Hata ayıklayıcı artık HRESULTs 'leri otomatik olarak çözer, bu nedenle bu tanımlayıcı bu durumlarda gerekli değildir.|S_OK|S_OK|  
|WC|Pencere sınıfı bayrağı|0x0010|WC_DEFAULTCHAR|  
|WM|Windows ileti numaraları|16|WM_CLOSE|  
|!|ham biçim, herhangi bir veri türü görünüm özelleştirmelerini yok sayılıyor|\<customized representation>|4|  
  
> [!NOTE]
> **HV** Biçim belirleyicisi varsa, hata ayıklayıcı arabelleğin uzunluğunu saptamaya çalışır ve uygun sayıda öğe görüntüler. Hata ayıklayıcının bir dizinin tam arabellek boyutunu bulması her zaman mümkün olmadığından, mümkün olduğunda bir boyut belirleyicisi kullanmanız gerekir `(pBuffer,[bufferSize])` . **HV** Biçim Belirleyicisi, arabellek boyutunun hazır olmadığı senaryolar için tasarlanmıştır  
  
### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Diziler için boyut belirticileri dizi olarak işaretçiler  
 Bir dizi olarak görüntülemek istediğiniz bir nesne işaretçiniz varsa, dizi öğelerinin sayısını belirtmek için bir tamsayı veya bir ifade kullanabilirsiniz:  
  
|Belirleyici|Biçimlendir|Özgün Izleme Değertr|Değer görüntülendi|  
|---------------|------------|---------------------------|---------------------|  
|n|Decimal veya **on altılı** tamsayı|pBuffer, [32]<br /><br /> pBuffer,**[0x20]**|`pBuffer`32 öğe dizisi olarak görüntüler.|  
|**exp**|Tamsayı sonucunu veren geçerli bir C++ ifadesi.|pBuffer, [bufferSize]|PBuffer öğelerini dizi olarak görüntüler `bufferSize` .|  
|**Genişlet (n)**|Tamsayı olarak değerlendirilen geçerli bir C++ ifadesi|pBuffer, Genişlet (2)|Öğesinin üçüncü öğesini görüntüler  `pBuffer`|  
  
## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> C++/CLı ile birlikte çalışma hata ayıklaması için biçim belirticileri  
 **Kalın** olmayan tanımlayıcılar yalnızca yerel ve C++/CLI kodunda hata ayıklamak için desteklenir.  
  
|Belirleyici|Biçimlendir|Özgün Izleme değeri|Değer görüntülendi|  
|---------------|------------|--------------------------|---------------------|  
|**d, ı**|işaretli ondalık tamsayı|0xF000F065|-268373915|  
|**larınız**|işaretsiz ondalık tamsayı|0x0065|101|  
|o|işaretsiz sekizlik tamsayı|0xF065|0170145|  
|x, X|Onaltılı tamsayı|61541|0x0000F065|  
|**l, h**|için uzun veya kısa ön ek: d, i, u, o, x, X|00406042|0x0c22|  
|**vadeli**|işaretli kayan nokta|(3./2.), f|1,500000|  
|**a**|imzalanmış bilimsel gösterim|(3.0/2.0)|1.500000 e + 000|  
|**Acil**|imzalanmış kayan nokta veya imzalanmış bilimsel gösterim, hangisi daha kısadır|(3.0/2.0)|1,5|  
|c|tek karakter|\<location>|101 ' e '|  
|s|const char *|\<location>|"Merhaba Dünya"|  
|hecesi|const wchar_t *<br /><br /> const char16_t\*|\<location>|L "Merhaba Dünya"|  
|alt|const wchar_t *<br /><br /> const char16_t\*|\<location>|Merhaba Dünya|  
|S8|const char *|\<location>|"Merhaba Dünya"|  
|sa|HRESULT veya Win32 hata kodu. (Hata ayıklayıcı artık HRESULTs 'leri otomatik olarak çözer, bu nedenle bu tanımlayıcı bu durumlarda gerekli değildir.|S_OK|S_OK|  
|WC|Pencere sınıfı bayrağı.|0x00000040|WC_DEFAULTCHAR|  
|WM|Windows ileti numaraları|0x0010|WM_CLOSE|  
|!|ham biçim, herhangi bir veri türü görünüm özelleştirmelerini yok sayılıyor|\<customized representation>|4|  
  
### <a name="format-specifiers-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> C++/CLı ile birlikte çalışma hata ayıklaması içindeki biçim belirticileri bellek konumları  
 Aşağıdaki tabloda bellek konumları için kullanılan biçimlendirme sembolleri yer almaktadır. Bir konum için değerlendirilen herhangi bir değer veya ifadeyle bir bellek Konum Belirleyicisi kullanabilirsiniz.  
  
|Sembol|Biçimlendir|Özgün Izleme değeri|Değer görüntülendi|  
|------------|------------|--------------------------|---------------------|  
|**hareketli**|64 ASCII karakter|0x0012ffac|0x0012ffac. 4... 0... 0W&....... 1W&.0.: W.. 1.... ".. 1.JO&.1,2... 1... 0y.... 1|  
|**m**|16 bayt, onaltılı ve ardından 16 ASCII karakter|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0... ". 0W&..|  
|**'lık**|16 bayt, onaltılı ve ardından 16 ASCII karakter|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0... ". 0W&..|  
|**MW**|8 sözcük|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**MD**|4 doublesözcük|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**yazılımını**|2 çeyrek sözcük|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|2 baytlık karakterler (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-cclit"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> C++/Client ile birlikte çalışma hata ayıklaması içinde diziler olarak işaretçiler için boyut Belirleyicisi  
 Bir dizi olarak görüntülemek istediğiniz bir nesne işaretçiniz varsa, dizi öğelerinin sayısını belirtmek için bir tamsayı kullanabilirsiniz:  
  
|Belirleyici|Biçimlendir|Expression|Değer görüntülendi|  
|---------------|------------|----------------|---------------------|  
|n|Ondalık tamsayı|pBuffer [32]|`pBuffer`32 öğe dizisi olarak görüntüler.|
