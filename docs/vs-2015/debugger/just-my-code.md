---
title: Sadece Benim Kodum | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efcabf9c7dc201f95515cd24bf3a14727f7149fe
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302499"
---
# <a name="just-my-code"></a>Yalnızca Kendi Kodum
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework dillerini kullanan geliştiriciler, sistem, çerçeve ve diğer kullanıcı dışı çağrıları hızlandıran ve çağrı yığını pencerelerinde bu çağrıları daraltan Just My Code hata ayıklayıcı özelliğine aşinadır. Just My Code C++ ve JavaScript dillerine genişletildi. Bu konu, .NET Framework, yerel C++ve JavaScript projelerinde Just My Code'u kullanmanın özelliklerini açıklar.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a>Sadece Kodumu etkinleştirme veya devre dışı bırak  
 Just My Code'u etkinleştirmek veya devre dışı kalmak için **Hata Ayıklama** menüsünde **Seçenekler ve Ayarlar'ı** seçin. Hata **Ayıklama** / **Genel** düğümünde, Sadece **Kodumu Etkinleştir'i**seçin veya temizleyin.  
  
 ![Seçenekler iletişim kutusunda Kodumda Etkinleştir](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> **Sadece Kodumu Etkinleştir** ayarı, tüm dillerdeki tüm Visual Studio projelerine uygulanan genel bir ayardır.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a>Arama yığını filtrelemegeçersiz  
 Çağrı Yığını ve Görevler pencereleri gibi çağrı yığını ekranlarında, Yalnızca Kodum kullanıcı kodu olmayan `[External Code]`kodu etiketli açıklamalı bir çerçeveye daraltıyor. Daraltılmış kareleri görüntülemek için, çağrı yığını ekranının bağlam menüsünde **Dış Kodu Göster'i** seçin.  
  
> [!NOTE]
> **Dış Kodu Göster** ayarı geçerli kullanıcının profilcine kaydedilir. Kullanıcı tarafından açılan tüm dillerdeki tüm projelere uygulanır.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Framework Sadece Kodum  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a>Kullanıcı ve kullanıcı dışı kod  
 Kullanıcı kodunu kullanıcı kodundan ayırmak için, Just My Code sembol (.pdb) dosyalarına ve program optimizasyonlarına bakar. Hata ayıklayıcı, ikili en iyi duruma geldiğinde veya .pdb dosyası kullanılamadığında kodu kullanıcı kodu olmayan kod olarak kabul eder.  
  
 Üç öznitelik, hata ayıklayıcının Kodum olarak kabul ettiği şeyi de etkiler:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>hata ayıklayıcıya uygulandığı kodun Kodum olmadığını söyler.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute>Kodum kapalı olsa bile kodu hata ayıklayıcıdan gizler.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>hata ayıklayıcıya, koda adım atmak yerine uygulandığı kodu atmasını söyler.  
  
  Diğer tüm kodlar kullanıcı kodu olarak kabul edilir.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a>Adımatma davranışı  
 Adım **Adım** (Klavye kısayolu: F11) kullanıcı kodu olmayan, hata ayıklayıcı sonraki kullanıcı deyimi için kod üzerinde adımlar. Dışarı **çıktığınızda** (Klavye: Shift + F11), hata ayıklayıcı sonraki kullanıcı kodu satırına çalışır. Kullanıcı koduyla karşılaşılmazsa, uygulama çıkana, kesme noktasına vurulana veya bir özel durum oluşana kadar yürütme devam eder.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a>Kesme noktası davranışı  
 Yalnızca Kodum etkinleştirildiğinde, **Tümlerini Kır** (Klavye: Ctrl + Alt + Kesme) seçeneğini belirleyebilir ve görüntülenecek kullanıcı kodu olmayan bir konumda yürütmeyi durdurabilirsiniz. Bu durumda Kaynak Yok penceresi görüntülenir. Daha sonra bir Adım komutu seçerseniz, hata ayıklayıcı sizi bir sonraki kullanıcı kodu satırına götürür.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a>Özel durum davranışı  
 İşlenmemiş bir özel durum kullanıcı kodunda oluşursa, hata ayıklayıcı kullanıcı kodunda özel durum oluşturulduğu satırda kesilir.  
  
 Özel durum için ilk şans özel durumları etkinse, kullanıcı kodu satırı yeşil renkle vurgulanır. Arama yığını **,[Dış Kod]** etiketli açıklamalı bir çerçeve görüntüler.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a>C++ Sadece Kodum  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a>Kullanıcı ve kullanıcı dışı kod  
 C++ Just My Code ,NET Framework ve JavaScript Just My Code'dan farklıdır, çünkü adımatma davranışı çağrı yığını davranışından bağımsızdır.  
  
 **Arama yığınları**  
  
 Varsayılan olarak, hata ayıklayıcı bu işlevleri çağrı yığını pencerelerinde kullanıcı kodu olmayan olarak kabul eder:  
  
- Semboller dosyasında soyulmuş kaynak bilgileri bulunan işlevler.  
  
- Sembol dosyalarının yığın çerçevesine karşılık gelen kaynak dosya olmadığını gösterdiği işlevler.  
  
- `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` Klasördeki dosyalarda `*.natjmc` belirtilen işlevler.  
  
  **Adım**  
  
  Varsayılan olarak, yalnızca `*.natstepfilter` `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` klasördeki dosyalarda belirtilen işlevler kullanıcı kodu olarak kabul edilir.  
  
  Kendi `.natstepfilter` oluşturabilirsiniz ve `.natjmc` stepping ve arama yığın penceresi davranışı `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`özelleştirmek için .  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a>Adımatma davranışı  
 Kullanıcı kodundan kullanıcı kodu olmayan kullanıcı koduna **Adım Attığınızda** (Klavye kısayolu: F11), hata ayıklayıcı kodun üzerinde bir sonraki kullanıcı kodu satırına adım atar. Dışarı **çıktığınızda** (Klavye: Shift + F11), hata ayıklayıcı sonraki kullanıcı kodu satırına çalışır. Kullanıcı koduyla karşılaşılmazsa, uygulama çıkana, kesme noktasına vurulana veya bir özel durum oluşana kadar yürütme devam eder.  
  
 Hata ayıklayıcı kullanıcı kodunda bozulursa (örneğin, Tüm komutu ara verirse), adımadım kullanıcı olmayan kodda devam ediyor.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a>Özel durum davranışı  
 Hata ayıklayıcı bir özel durum vurduğunda, kullanıcı veya kullanıcı kodu nda olup olmadığına bakılmaksızın özel durum üzerinde durur. **Özel Durumlar** iletişim kutusundaki **Kullanıcı işlenmemiş** seçenekler yoksayılır.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Adımatma davranışını özelleştirme  
 `*.natstepfilter` Dosyaları kullanıcı kodu olmayan olarak listeleyerek aşamalı olarak işlevleri belirtebilirsiniz.  
  
- Visual Studio makinesinin tüm kullanıcıları için kullanıcı kodu olmayan kodu belirtmek için `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` .natstepfilter dosyasını klasöre ekleyin.  
  
- Tek bir kullanıcı için kullanıcı olmayan kodu belirtmek için .natstepfilter dosyasını klasöre `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` ekleyin.  
  
  .natstepfilter dosyaları bu sözdizimi ile xml dosyaları:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|İşlev|Gereklidir. Bir veya daha fazla işlevi kullanıcı olmayan işlevler olarak belirtir.|  
|`Name`|Gereklidir. Bir ECMA-262 biçimlendirilmiş düzenli ifade maç için tam işlev adını belirten. Örnek:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> hata ayıklayıcıya, tüm `MyNS::MyClass` yöntemlerin kullanıcı kodu olarak kabul edilmesi gerektiğini söyler. Eşleşme büyük/küçük harf duyarlı.|  
|`Module`|İsteğe bağlı. İşleviçeren modüle tam yolu belirten bir ECMA-262 biçimlendirilmiş normal ifade. Eşleşme büyük/küçük bir ihtimal duyarsız.|  
|`Action`|Gereklidir. Bu büyük/küçük harf duyarlı değerlerden biri:<br /><br /> -   `NoStepInto`– hata ayıklama cısrısına eşleşen işlevi üzerine basmasını söyler.<br />-   `StepInto`– hata ayıklamacıya eşleşen işlevlere adım atmasını `NoStepInto` söyler ve eşleşen işlevler için diğer işlevleri geçersiz kılır.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Arama yığını davranışını özelleştirme  
 Çağrı yığınlarında kullanıcı kodu olmayan olarak davranılabilmeleri için modülleri, kaynak dosyaları `*.natjmc` ve işlevleri dosyalarda belirterek belirtebilirsiniz.  
  
- Visual Studio makinesinin tüm kullanıcıları için kullanıcı kodu olmayan kodu belirtmek için `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` .natjmc dosyasını klasöre ekleyin.  
  
- Tek bir kullanıcı için kullanıcı olmayan kodu belirtmek için .natjmc dosyasını klasöre `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` ekleyin.  
  
  .natjmc dosyaları bu sözdizimi ile xml dosyaları:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Modül öğesi öznitelikleri**  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gereklidir. Modülün veya modüllerin tam yolu. Windows joker karakterlerini `?` (sıfır veya bir karakter) `*` ve (sıfır veya daha fazla karakter) kullanabilirsiniz. Örneğin,<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> hata ayıklayıcıya, herhangi bir `\3rdParty\UtilLibs` sürücüdeki tüm modülleri harici kod olarak ele almalarını söyler.|  
|`Company`|İsteğe bağlı. Çalıştırılabilir dosyaya katıştırılmış modülü yayımlayan şirketin adı. Modülleri ayrıştırmak için bu özelliği kullanabilirsiniz.|  
  
 **Dosya öğesi öznitelikleri**  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gereklidir. Dış kod olarak ele almak için kaynak dosya veya dosyaların tam yolu. Windows joker karakterlerini `?` ve `*` yolu belirtirken kullanabilirsiniz.|  
  
 **İşlev öğesi öznitelikleri**  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gereklidir. Dış kod olarak ele almak için işlevin tam nitelikli adı.|  
|`Module`|İsteğe bağlı. İşleviçeren modüle ad veya tam yol. Bu özniteliği, aynı ada sahip disambiguate işlevleri için kullanabilirsiniz.|  
|`ExceptionImplementation`|Çağrı yığını `true`bu işlev yerine özel durum atan işlevi görüntüler.|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a>JavaScript Sadece Benim Kodum  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a>Kullanıcı ve kullanıcı dışı kod  
 **Kod sınıflandırmaları**  
  
 JavaScript Just My Code, bu sınıflandırmalardan birinde kodu kategorize ederek adımatma ve arama yığını ekranını denetler:  
  
|||  
|-|-|  
|**MyCode**|Sahip olduğunuz ve kontrol ettiğiniz kullanıcı kodu.|  
|**KütüphaneKodu**|Düzenli olarak kullandığınız kitaplıklardan kullanıcı kodu ve uygulamanız doğru çalışmasına dayanır (örneğin WinJS veya jQuery).|  
|**İlişkisiz Kod**|Uygulamanızda çalışıyor olabilecek kullanıcı kodu olmayan, ancak size ait değildir ve uygulamanız doğru çalışması için doğrudan bu kodun (örneğin, reklam görüntüleyen bir reklam SDK'sı) güvenmez. Windows Mağazası projelerinde, bir HTTP veya HTTPS URI'den uygulamanıza yüklenen tüm kodlar da İlişkisiz Kod olarak kabul edilir.|  
  
 JavaScript hata ayıklayıcı otomatik olarak bu kod türlerini sınıflar:  
  
- Ana bilgisayar tarafından sağlanan `eval` işleve bir dize geçirilerek yürütülen komut dosyası **MyCode**olarak sınıflandırılır.  
  
- `Function` Bir dize oluşturucuya geçirilerek yürütülen komut dosyası **LibraryCode**olarak sınıflandırılır.  
  
- WinJS veya Azure SDK gibi bir çerçeve referansında bulunan komut dosyası **LibraryCode**olarak sınıflandırılır.  
  
- `setTimeout`Bir `setImmediate`dize ,, veya `setInterval` işlevlere geçirilerek yürütülen komut **dosyası, İlişkisiz Kod**olarak sınıflandırılır.  
  
- Tüm `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Visual Studio JavaScript projeleri için diğer kullanıcı ve kullanıcı olmayan kodu belirtir.  
  
  Varsayılan sınıflandırmaları değiştirebilir ve projenin kök klasörüne bir `mycode.json` .json dosyası ekleyerek belirli dosyaları ve url'leri sınıflandırabilirsiniz.  
  
  Diğer tüm kodlar **MyCode**olarak sınıflandırılır.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a>Adımatma davranışı  
  
- Bir işlev kullanıcı **(MyCode**) kodu değilse, **Adım Adım** (Klavye kısayolu: F11) Adım **At (Klavye:** F10) olarak çalışır.  
  
- Kullanıcı olmayan **(LibraryCode** veya **UnrelatedCode)** kodunda bir adım başlarsa, adım adım geçici olarak Yalnızca Kodum etkinleştirilmemiş gibi görünür. Kullanıcı koduna geri adım attığınızda, Yalnızca Kodum adımı yeniden etkinleştirilir.  
  
- Kullanıcı kodundaki bir adım geçerli yürütme bağlamından (olay işleyicisinin son satırında bir adım yapmak gibi) ayrılmasıyla sonuçlandığında, hata ayıklayıcı kullanıcı kodunun bir sonraki yürütülen satırında durur. Örneğin, **LibraryCode** kodunda bir geri arama yürütülürse hata ayıklayıcı sonraki kullanıcı kodu satırı yürütülene kadar devam eder.  
  
- **Adım Dışarı** (Klavye: Shift + F11) kullanıcı kodunun bir sonraki satırında durur. Kullanıcı koduyla karşılaşılmazsa, uygulama çıkana, kesme noktasına vurulana veya bir özel durum oluşana kadar yürütme devam eder.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a>Kesme noktası davranışı  
  
- Herhangi bir kodda ayarlanan kesme noktaları, o kodun sınıflandırılmasından bağımsız olarak her zaman vurulur  
  
- `debugger` Anahtar kelimeile karşılaşılırsa:  
  
  - **LibraryCode** kodu, hata ayıklayıcı her zaman tatili.  

  - **Alakasız Kod** kodu, hata ayıklayıcı durmuyor.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a>Özel durum davranışı  
 Işlenmemiş bir özel durum aşağıdaki durumlarda oluşursa:  
  
- **MyCode** veya **LibraryCode** kodu, hata ayıklayıcı her zaman tatili.  
  
- **IlgisizKod** kodu ve **MyCode** veya **LibraryCode** kodu çağrı yığınında, hata ayıklayıcı tatili.  
  
  Özel Durumlar iletişim kutusundaki özel durumlar için ilk şans özel durumları etkinleştirilirse ve özel durum **LibraryCode** veya **UnrelatedCode** koduna atılırsa:  
  
- Özel durum işlenirse, hata ayıklama kırılmaz.  
  
- Özel durum işlenmemişse, hata ayıklama bozulur.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Sadece Kodumu Özelleştir  
 Tek bir Visual Studio projesi için kullanıcı ve kullanıcı olmayan kodu `mycode.json` kategorilere ayırmak için projenin kök klasörüne bir .json dosyası ekleyin.  
  
 Sınıflandırmalar bu sırayla gerçekleştirilir:  
  
1. Varsayılan sınıflandırmalar  
  
2. Dosyadaki `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` sınıflandırmalar  
  
3. Geçerli projenin `mycode. json` dosyasındaki sınıflandırmalar.  
  
   Her sınıflandırma adımı önceki adımları geçersiz kılar. Bir .json dosyasının tüm anahtar değer çiftlerini listelemesi gerekmez ve **MyCode,** **Kitaplıklar**ve **İlişkisiz** değerler boş diziler olabilir.  
  
   Kod .json dosyalarım şu sözdizimini kullanır:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, Fonksiyon ve ScriptBlock**  
  
 **Eval**, **İşlev**ve **ScriptBlock** anahtar değeri çiftleri dinamik olarak oluşturulan kodun nasıl sınıflandırış olduğunu belirler.  
  
|||  
|-|-|  
|**Dğer**|Bir dize ana bilgisayar tarafından sağlanan `eval` işleve geçirilerek yürütülen komut dosyası. Varsayılan olarak, Eval komut dosyası **MyCode**olarak sınıflandırılır.|  
|**İşlev**|Bir dize `Function` oluşturucuya geçirilerek yürütülen komut dosyası. Varsayılan olarak, İşlev komut dosyası **LibraryCode**olarak sınıflandırılır.|  
|**Komut Dosyası Bloğu**|`setTimeout`Bir dize , , `setImmediate`veya `setInterval` işlevlere geçirerek yürütülen komut dosyası. Varsayılan olarak, ScriptBlock komut dosyası **UnrelatedCode**olarak sınıflandırılır.|  
  
 Değeri aşağıdaki anahtar kelimelerden biriyle değiştirebilirsiniz:  
  
- `MyCode`komut dosyasını **MyCode**olarak sınıfa  
  
- `Library`komut dosyasını **LibraryCode**olarak sınıflar.  
  
- `Unrelated`komut dosyasını **İlişkisiz Kod**olarak sınıfa salar.  
  
  **MyCode, Kütüphaneler ve İlişkisiz**  
  
  **MyCode,** **Kitaplıklar**ve **İlişkisiz** anahtar değer çiftleri, bir sınıflandırmaya eklemek istediğiniz url'leri veya dosyaları belirtir:  
  
|||  
|-|-|  
|**MyCode**|**MyCode**olarak sınıflandırılan bir dizi url veya dosya.|  
|**Kitaplıklar**|**LibraryCode**olarak sınıflandırılan bir dizi url veya dosya.|  
|**Alakasız**|**UnrelatedCode**olarak sınıflandırılan bir dizi url veya dosya.|  
  
 Url veya dosya dizesi, `*` sıfır veya daha fazla karakterle eşleşen bir veya daha fazla karakter içerebilir. `*`normal ifadenin `.*`eşdeğeridir.
