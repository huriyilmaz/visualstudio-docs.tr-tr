---
title: Hata Ayıklama'daki İfadeler | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VBScript
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3999737a2fad04c9b513722ae11608574a72c410
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302527"
---
# <a name="expressions-in-the-debugger"></a>Hata Ayıklayıcıdaki İfadeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcı, **QuickWatch** iletişim kutusuna, **İzleme** penceresine veya **Hemen** penceresine bir ifade girdiğinizde çalışan ifade değerlendiricileriçerir. İfade değerlendiriciler, **Kesme Noktaları** penceresinde ve hata ayıklayıcıdaki diğer birçok yerde de iş başındadır.  
  
 Aşağıdaki bölümlerde farklı dillerdeki ifadeler hakkında ayrıntılı bilgi verilmiştir.  
  
## <a name="f-expressions-are-not-supported"></a>F# ifadeleri desteklenmiyor  
 F# ifadeleri tanınmaz. F# kodunu hata ayıklıyorsanız, ifadeleri hata ayıklama penceresine veya iletişim kutusuna girmeden önce ifadelerinizi C# sözdizimine çevirmeniz gerekir. İfadeleri F#'dan C#'a çevirdiğinizde, C#'ın `==` eşitliği test etmek için işleci kullandığını, F#'nın ise tekini `=`kullandığını unutmayın.  
  
## <a name="c-expressions"></a>C++ İfadeleri  
 C++'da ifadelerle bağlam işleçlerini kullanma hakkında bilgi için [bkz.](../debugger/context-operator-cpp.md)  
  
### <a name="unsupported-expressions-in-c"></a>C++'da Desteklenmeyen İfadeler  
  
#### <a name="constructors-destructors-and-conversions"></a>Yapıcılar, yıkıcılar ve dönüşümler  
 Bir nesne için açık veya kapalı olarak bir oluşturucu veya yıkıcı çağıramazsınız. Örneğin, aşağıdaki ifade açıkça bir oluşturucu çağırır ve bir hata iletisi ile sonuçlanır:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Dönüştürmenin hedefi bir sınıfsa, dönüşüm işlevini çağıramazsınız. Böyle bir dönüştürme bir nesnenin yapımını içerir. Örneğin, dönüşüm `myFraction` işlevi işleci `CFraction` `FixedPoint`tanımlayan bir , örneği ise, aşağıdaki ifade bir hatayla sonuçlanır:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Yeni veya silme operatörlerini arayamaz sınız. Örneğin, aşağıdaki ifade desteklenmez:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Önişlemci Makroları  
 Hata ayıklamada önişlemci makroları desteklenmez. Örneğin, bir sabit `VALUE` şu şekilde `#define VALUE 3`bildirilirse: , `VALUE` **Watch** penceresinde kullanamazsınız. Bu sınırlamayı önlemek için, mümkün olduğunca enums ve fonksiyonlar ile 's değiştirmelisiniz. `#define`  
  
### <a name="using-namespace-declarations"></a>ad alanı bildirimlerini kullanma  
 Bildirimleri `using namespace` kullanamazsınız.  Geçerli ad alanının dışında bir tür adı veya değişkene erişmek için tam nitelikli adı kullanmanız gerekir.  
  
### <a name="anonymous-namespaces"></a>Anonim ad alanları  
 Anonim ad alanları desteklenmez. Aşağıdaki koda sahipseniz, saat `test` penceresine ekleyemezsiniz:  
  
```cpp  
namespace mars   
{   
    namespace  
    {  
        int test = 0;   
    }   
}   
int main()   
{   
    // Adding a watch on test does not work.   
    mars::test++;   
    return 0;   
}  
  
```  
  
### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Durumu korumak için hata ayıklama içsel işlevleri kullanma  
 Hata ayıklama içsel işlevleri, uygulamanın durumunu değiştirmeden ifadelerde belirli C/C++ işlevlerini çağırmanın bir yolunu verir.  
  
 Hata ayıklama içsel fonksiyonlar:  
  
- Güvenli olduğu garanti edilir: hata ayıklama içsel işlevi yürütmek debugged ediliyor işlemi bozmaz.  
  
- Yan etkilere ve fonksiyon değerlendirmesine izin verilmeyen senaryolarda bile tüm ifadelere izin verilir.  
  
- Normal işlev çağrılarının mümkün olmadığı senaryolarda (örneğin, bir minidump hata ayıklama gibi) çalışın.  
  
  Hata ayıklama içsel işlevler de ifadeleri değerlendirmeyi daha kullanışlı hale getirebilir. Örneğin, `strncmp(str, “asd”)` bir kesme noktası durumunda yazmak çok `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`daha kolaydır. )  
  
|Alan|İç işlevler|  
|----------|-------------------------|  
|**Dize uzunluğu**|strlen, wcslen, strnlen, wcsnlen|  
|**Dize karşılaştırması**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Dize arama**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Bu işlevler, Windows 8'de çalıştırılmak üzere debugged olan işlemi gerektirir. Windows 8 aygıtından oluşturulan döküm dosyalarının hata ayıklanması, Visual Studio bilgisayarının Windows 8 çalıştırılmasını da gerektirir. Ancak, bir Windows 8 aygıtını uzaktan hata ayıklıyorsanız, Visual Studio bilgisayarı Windows 7 çalıştırıyor olabilir.|  
|**Çeşitli**|__log2<br /><br /> Belirtilen bir tamsaın günlük tabanını 2'yi verir, yuvarlanır en yakın alt tamsayıya.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLI - Desteklenmeyen İfadeler  
  
- İşaretçileri veya kullanıcı tanımlı dökümleri içeren dökümler desteklenmez.  
  
- Nesne karşılaştırması ve atama desteklenmez.  
  
- Aşırı yüklenen operatörler ve aşırı yüklü işlevler desteklenmez.  
  
- Kutulama ve unboxing desteklenmez.  
  
- `Sizeof`işleci desteklenmez.  
  
## <a name="c---unsupported-expressions"></a>C# - Desteklenmeyen İfadeler  
  
### <a name="dynamic-objects"></a>Dinamik Nesneler  
 Statik olarak dinamik olarak yazılan hata ayıklama ifadelerinde değişkenler kullanabilirsiniz. Watch penceresinde uygulanan <xref:System.Dynamic.IDynamicMetaObjectProvider> nesneler değerlendirildiğinde Dinamik Görünüm düğümü eklenir. Dinamik Görünüm düğümü nesne üyelerini gösterir, ancak üyelerin değerlerini düzenlemeye izin vermez.  
  
 Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:  
  
- Bileşik işleçleri `+=`, `-=`, `%=`, `/=`, ve`*=`  
  
- Sayısal dökümler ve yazı bağımsız değişken dökümleri de dahil olmak üzere birçok döküm  
  
- Yöntem ikiden fazla bağımsız değişkeni olan çağrıları  
  
- İkiden fazla bağımsız değişkeni olan özellik getters  
  
- Bağımsız değişkenleri olan özellik ayarlayıcıları  
  
- Dizin leyiciye atama  
  
- Boolean `&&` operatörleri ve`||`  
  
### <a name="anonymous-methods"></a>Anonim Yöntemler  
 Yeni anonim yöntemlerin oluşturulması desteklenmez.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - Desteklenmeyen İfadeler  
  
### <a name="dynamic-objects"></a>Dinamik Nesneler  
 Statik olarak dinamik olarak yazılan hata ayıklama ifadelerinde değişkenler kullanabilirsiniz. Watch penceresinde uygulanan <xref:System.Dynamic.IDynamicMetaObjectProvider> nesneler değerlendirildiğinde Dinamik Görünüm düğümü eklenir. Dinamik Görünüm düğümü nesne üyelerini gösterir, ancak üyelerin değerlerini düzenlemeye izin vermez.  
  
 Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:  
  
- Bileşik işleçleri `+=`, `-=`, `%=`, `/=`, ve`*=`  
  
- Sayısal dökümler ve yazı bağımsız değişken dökümleri de dahil olmak üzere birçok döküm  
  
- Yöntem ikiden fazla bağımsız değişkeni olan çağrıları  
  
- İkiden fazla bağımsız değişkeni olan özellik getters  
  
- Bağımsız değişkenleri olan özellik ayarlayıcıları  
  
- Dizin leyiciye atama  
  
- Boolean `&&` operatörleri ve`||`  
  
### <a name="local-constants"></a>Yerel Sabitler  
 Yerel sabitler desteklenmez.  
  
### <a name="import-aliases"></a>Diğer Adları İthalat  
 Alma takma adları desteklenmez.  
  
### <a name="variable-declarations"></a>Değişken Bildirimler  
 Hata ayıklama pencerelerinde açık yeni değişkenler bildiremezsiniz. Ancak, **Hemen** penceresi içinde yeni örtük değişkenler atayabilirsiniz. Bu örtük değişkenler hata ayıklama oturumuna göre kapsamlıdır ve hata ayıklama nın dışında erişilemez. Örneğin, deyim `o = 5` örtülü olarak yeni bir `o` değişken oluşturur ve 5 değerini ona atar. Tür hata ayıklama tarafından çıkarılamıyorsa, bu tür örtük değişkenler **nesne** türündendir.  
  
### <a name="unsupported-keywords"></a>Desteklenmeyen Anahtar Kelimeler  
  
- `AddressOf`  
  
- `End`  
  
- `Error`  
  
- `Exit`  
  
- `Goto`  
  
- `On Error`  
  
- `Resume`  
  
- `Return`  
  
- `Select/Case`  
  
- `Stop`  
  
- `SyncLock`  
  
- `Throw`  
  
- `Try/Catch/Finally`  
  
- `With`  
  
- Ad alanı veya modül düzeyindeanahtar kelimeler, gibi `End Sub` veya `Module`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C++'da Biçimlendirme](../debugger/format-specifiers-in-cpp.md)   
 [Bağlam İşlemesi (C++)](../debugger/context-operator-cpp.md)   
 [C'deki Biçimlendirmeler #](../debugger/format-specifiers-in-csharp.md)   
 [Sözde Değişkenler](../debugger/pseudovariables.md)
