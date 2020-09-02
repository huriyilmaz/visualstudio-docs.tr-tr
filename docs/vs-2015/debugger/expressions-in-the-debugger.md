---
title: Hata Ayıklayıcıdaki İfadeler | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315037"
---
# <a name="expressions-in-the-debugger"></a>Hata Ayıklayıcıdaki İfadeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcı, **QuickWatch** iletişim kutusunda, **Gözcü** penceresinde veya **anında** pencereye bir ifade girdiğinizde çalışan ifade değerlendiricileri içerir. Değerlendiricileri ifadesi Ayrıca **kesme noktaları** penceresinde ve hata ayıklayıcıda birçok diğer yerde de çalışır.  
  
 Aşağıdaki bölümler, farklı dillerdeki ifadelerle ilgili ayrıntıları sağlar.  
  
## <a name="f-expressions-are-not-supported"></a>F # ifadeleri desteklenmez  
 F # ifadeleri tanınmıyor. F # kodunda hata ayıklaması yapıyorsanız, ifadeleri bir hata ayıklayıcı penceresine veya iletişim kutusuna girmeden önce ifadelerinizi C# sözdizimine çevirmeniz gerekir. F # ' dan C# ' A ifade çevirirken, C# ' nin `==` eşitlik için test etmek üzere Işlecini kullandığını unutmayın, f # Single öğesini kullanır `=` .  
  
## <a name="c-expressions"></a>C++ Ifadeleri  
 C++ içindeki ifadelerle bağlam işleçlerini kullanma hakkında daha fazla bilgi için bkz. [Bağlam işleci (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>C++ ' da desteklenmeyen Ifadeler  
  
#### <a name="constructors-destructors-and-conversions"></a>Oluşturucular, Yıkıcılar ve dönüştürmeler  
 Açıkça veya örtük olarak bir nesne için bir Oluşturucu ya da yıkıcı çağrılamaz. Örneğin, aşağıdaki ifade açıkça bir oluşturucuyu çağırır ve bir hata iletisiyle sonuçlanır:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Dönüştürmenin hedefi bir sınıf ise, bir dönüştürme işlevi çağrılamaz. Böyle bir dönüştürme bir nesnenin oluşturulmasını içerir. Örneğin, `myFraction` `CFraction` dönüştürme işlevi işlecini tanımlayan bir örneğidir, `FixedPoint` aşağıdaki ifade bir hatayla sonuçlanır:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 New veya delete işleçlerini çağrılamaz. Örneğin, aşağıdaki ifade desteklenmez:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Önişlemci makroları  
 Önişlemci makroları hata ayıklayıcıda desteklenmez. Örneğin, bir sabit değer `VALUE` olarak bildirilirse `#define VALUE 3` , `VALUE` **Gözcü** penceresinde kullanamazsınız. Bu sınırlamayı önlemek için, `#define` mümkün olan her durumda Enum ve işlevlerle değiştirmelisiniz.  
  
### <a name="using-namespace-declarations"></a>ad alanı bildirimlerini kullanma  
 `using namespace`Bildirimleri kullanamazsınız.  Geçerli ad alanı dışındaki bir tür adına veya değişkenine erişmek için tam adı kullanmanız gerekir.  
  
### <a name="anonymous-namespaces"></a>Anonim ad alanları  
 Anonim ad alanları desteklenmez. Aşağıdaki koda sahipseniz, `test` Gözcü penceresine ekleyemezsiniz:  
  
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
  
### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Durumu korumak için hata ayıklayıcı iç işlevlerini kullanma  
 Hata ayıklayıcı iç işlevleri, uygulamanın durumunu değiştirmeden ifadelerde belirli C/C++ işlevlerini çağırmak için bir yol sağlar.  
  
 Hata ayıklayıcı iç işlevleri:  
  
- Güvenli olduğu garanti edilir: bir hata ayıklayıcı iç işlevinin yürütülmesi, hataları ayıklanan işlemi bozmaz.  
  
- Yan etkileri ve işlev değerlendirmesinin izin verilmediği senaryolarda bile tüm ifadelerde izin verilir.  
  
- Bir mini döküm dosyasında hata ayıklama gibi normal işlev çağrılarının mümkün olmadığı senaryolarda çalışın.  
  
  Hata ayıklayıcı iç işlevleri ayrıca değerlendirme ifadelerin daha kullanışlı olmasını sağlayabilir. Örneğin, `strncmp(str, “asd”)` bir kesme noktası koşulunda daha kolay yazılması çok daha kolaydır `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’` . )  
  
|Alan|İç işlevler|  
|----------|-------------------------|  
|**Dize uzunluğu**|strlen, wcslen, strnlen, wcsnlen|  
|**Dize karşılaştırması**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsıcmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnıcmp, wcsnıcmp|  
|**Dize arama**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError (), TlsGetValue ()|  
|**Windows 8**|WindowsGetStringLen (), Windowsgetstrıngrawbuffer ()<br /><br /> Bu işlevler, hata ayıklamakta olan işlemin Windows 8 üzerinde çalışıyor olmasını gerektirir. Windows 8 cihazından oluşturulan döküm dosyalarının hata ayıklaması, Visual Studio bilgisayarının Windows 8 çalıştırıyor olmasını da gerektirir. Ancak, Windows 8 cihazının uzaktan hata ayıklaması yapıyorsanız, Visual Studio bilgisayarı Windows 7 çalıştırıyor olabilir.|  
|**Çeşitli**|__log2<br /><br /> Belirtilen bir tamsayının, en yakın küçük tamsayıya yuvarlanmış olan günlük 2 değerini döndürür.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLı-desteklenmeyen Ifadeler  
  
- İşaretçileri veya Kullanıcı tanımlı yayınları içeren yayınlar desteklenmez.  
  
- Nesne karşılaştırma ve atama desteklenmiyor.  
  
- Aşırı yüklenmiş işleçler ve aşırı yüklenmiş işlevler desteklenmez.  
  
- Kutulama ve kutudan çıkarma desteklenmez.  
  
- `Sizeof` işleç desteklenmiyor.  
  
## <a name="c---unsupported-expressions"></a>C#-desteklenmeyen Ifadeler  
  
### <a name="dynamic-objects"></a>Dinamik nesneler  
 Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. Uygulayan nesneler <xref:System.Dynamic.IDynamicMetaObjectProvider> İzleme penceresi değerlendirildiğinde, dinamik bir görünüm düğümü eklenir. Dinamik görünüm düğümü nesne üyelerini gösterir ancak üyelerin değerlerini düzenlememe izin vermez.  
  
 Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:  
  
- Bileşik işleçler `+=` , `-=` ,, `%=` `/=` ve `*=`  
  
- Sayısal yayınlar ve tür bağımsız değişken yayınları dahil olmak üzere çok sayıda yayını  
  
- İkiden fazla bağımsız değişkenle Yöntem çağrıları  
  
- İkiden fazla bağımsız değişkene sahip Özellik alıcıları  
  
- Bağımsız değişkenlerle özellik ayarlayıcıları  
  
- Dizin oluşturucuya atama  
  
- Boole işleçleri `&&` ve `||`  
  
### <a name="anonymous-methods"></a>Anonim Yöntemler  
 Yeni anonim yöntemlerin oluşturulması desteklenmez.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic-desteklenmeyen Ifadeler  
  
### <a name="dynamic-objects"></a>Dinamik nesneler  
 Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. Uygulayan nesneler <xref:System.Dynamic.IDynamicMetaObjectProvider> İzleme penceresi değerlendirildiğinde, dinamik bir görünüm düğümü eklenir. Dinamik görünüm düğümü nesne üyelerini gösterir ancak üyelerin değerlerini düzenlememe izin vermez.  
  
 Dinamik nesnelerin aşağıdaki özellikleri desteklenmez:  
  
- Bileşik işleçler `+=` , `-=` ,, `%=` `/=` ve `*=`  
  
- Sayısal yayınlar ve tür bağımsız değişken yayınları dahil olmak üzere çok sayıda yayını  
  
- İkiden fazla bağımsız değişkenle Yöntem çağrıları  
  
- İkiden fazla bağımsız değişkene sahip Özellik alıcıları  
  
- Bağımsız değişkenlerle özellik ayarlayıcıları  
  
- Dizin oluşturucuya atama  
  
- Boole işleçleri `&&` ve `||`  
  
### <a name="local-constants"></a>Yerel sabitler  
 Yerel sabitler desteklenmez.  
  
### <a name="import-aliases"></a>Diğer adları içeri aktar  
 İçeri aktarma diğer adları desteklenmez.  
  
### <a name="variable-declarations"></a>Değişken bildirimleri  
 Hata ayıklayıcı Windows 'da açık yeni değişkenler bildiremezsiniz. Bununla birlikte, **hemen** penceresi içinde yeni örtük değişkenler atayabilirsiniz. Bu örtük değişkenler hata ayıklama oturumunun kapsamına alınır ve hata ayıklayıcının dışında erişilebilir değildir. Örneğin, ifade `o = 5` örtük olarak yeni bir değişken oluşturur `o` ve 5 değerini bu değere atar. Türü hata ayıklayıcı tarafından çıkarsanmadığı takdirde bu tür örtük değişkenler **Object** türündedir.  
  
### <a name="unsupported-keywords"></a>Desteklenmeyen anahtar sözcükler  
  
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
  
- Ad alanı veya modül düzeyi anahtar sözcükleri, örneğin `End Sub` veya `Module` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C++ içindeki biçim belirticileri](../debugger/format-specifiers-in-cpp.md)   
 [Bağlam Işleci (C++)](../debugger/context-operator-cpp.md)   
 [C 'de biçim belirticileri #](../debugger/format-specifiers-in-csharp.md)   
 [Sözde Değişkenler](../debugger/pseudovariables.md)
