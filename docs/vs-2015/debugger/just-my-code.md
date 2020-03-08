---
title: Yalnızca kendi kodum | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410151"
---
# <a name="just-my-code"></a>Yalnızca Kendi Kodum
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework dillerini kullanan geliştiriciler, sistem, çerçeve ve diğer kullanıcı olmayan çağrılar üzerinde yapılan adımların ve çağrı yığını penceresinde bu çağrıları daraltan Yalnızca kendi kodum hata ayıklayıcı özelliği hakkında bilgi sahibi. Yalnızca kendi kodum, C++ ve JavaScript dillerine genişletilmiştir. Bu konuda, .NET Framework, yerel C++ve JavaScript projelerinde yalnızca kendi kodum kullanmanın özellikleri açıklanmaktadır.  
  
## <a name="BKMK_Enable_or_disable_Just_My_Code"></a>Yalnızca kendi kodum etkinleştir veya devre dışı bırak  
 Yalnızca kendi kodum etkinleştirmek veya devre dışı bırakmak için, **hata ayıklama** menüsünde **Seçenekler ve ayarlar** ' ı seçin. **Hata ayıklama** / **genel** düğümünde **yalnızca kendi kodum etkinleştir**' i seçin veya temizleyin.  
  
 ![Seçenekler iletişim kutusunda Yalnızca kendi kodum etkinleştir](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> **Etkinleştir yalnızca kendi kodum** ayarı tüm dillerdeki tüm Visual Studio projelerine uygulanan genel bir ayardır.  
  
### <a name="BKMK_Override_call_stack_filtering"></a>Çağrı yığını filtrelemeyi geçersiz kıl  
 Çağrı yığını ve Görevler penceresi gibi çağrı yığını ekranlarda Kullanıcı olmayan kodu `[External Code]`etiketli bir açıklamalı çerçevede daraltır Yalnızca kendi kodum. Daraltılan çerçeveleri görüntülemek için çağrı yığını görünümünün bağlam menüsünde **dış kodu göster** ' i seçin.  
  
> [!NOTE]
> **Dış kodu göster** ayarı geçerli kullanıcının profil oluşturucuya kaydedilir. Kullanıcı tarafından açılan tüm dillerdeki tüm projelere uygulanır.  
  
## <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Framework Yalnızca kendi kodum  
  
### <a name="BKMK_NET_User_and_non_user_code"></a>Kullanıcı ve Kullanıcı olmayan kod  
 Kullanıcı kodunu Kullanıcı dışı koddan ayırt etmek için, Yalnızca kendi kodum sembol (. pdb) dosyalarına ve program iyileştirmelerine bakar. Hata ayıklayıcı, ikili iyileştirildiğinde veya. pdb dosyası kullanılabilir olmadığında kodu kullanıcı olmayan kod olarak değerlendirir.  
  
 Üç öznitelik de hata ayıklayıcının benim kodum olarak dikkate aldığı şeyi etkiler:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> hata ayıklayıcıya uygulanan kodun, kodum olmadığını söyler.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute>, Yalnızca kendi kodum kapalı olsa bile kodu hata ayıklayıcıdan gizler.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>, hata ayıklayıcının, koda adım adım değil, uygulandığı kodda ilermasını söyler.  
  
  Diğer tüm kodlar Kullanıcı kodu olarak kabul edilir.  
  
### <a name="BKMK_NET_Stepping_behavior"></a>Atlama davranışı  
 ' De **(klavye** kısayolu: F11) Kullanıcı olmayan kod, hata ayıklayıcı bir sonraki kullanıcı bildirimine kod üzerinde adımlar halinde yapılır. **Dışarı adımla** (klavye: Shift + F11), hata ayıklayıcı sonraki Kullanıcı kodu satırına çalışır. Hiçbir Kullanıcı kodu ile karşılaşılırsa, uygulama kaldırılana kadar bir kesme noktasına isabet veya bir özel durum ortaya çıkana kadar yürütme devam eder.  
  
### <a name="BKMK_NET_Breakpoint_behavior"></a>Kesme noktası davranışı  
 Yalnızca kendi kodum etkinleştirildiğinde, **Tümünü kes** ' i (klavye: Ctrl + Alt + Break) seçebilir ve görüntülenecek Kullanıcı kodu olmayan bir konumda yürütmeyi durdurabilirsiniz. Bu durumda kaynak penceresi görüntülenir. Daha sonra bir adım komutu seçerseniz, hata ayıklayıcı sizi bir sonraki Kullanıcı kodu satırına götürür.  
  
### <a name="BKMK_NET_Exception_behavior"></a>Özel durum davranışı  
 Kullanıcı olmayan kodda işlenmeyen bir özel durum oluşursa, hata ayıklayıcı özel durumun oluşturulduğu Kullanıcı kodundaki satıra kesilir.  
  
 Özel durum için ilk şans özel durumları etkinleştirilirse, Kullanıcı kodu satırı yeşil renkle vurgulanır. Çağrı yığını **[Dış kod]** etiketli açıklamalı bir çerçeve görüntüler.  
  
## <a name="BKMK_C___Just_My_Code"></a>C++ Yalnızca kendi kodum  
  
### <a name="BKMK_CPP_User_and_non_user_code"></a>Kullanıcı ve Kullanıcı olmayan kod  
 C++Yalnızca kendi kodum .NET Framework ve JavaScript Yalnızca kendi kodum farklıdır çünkü atlama davranışı çağrı yığını davranışından bağımsızdır.  
  
 **Çağrı yığınları**  
  
 Varsayılan olarak, hata ayıklayıcı bu işlevleri çağrı yığını pencerelerinin Kullanıcı olmayan kodu olarak değerlendirir:  
  
- Sembol dosyasında, atılmış kaynak bilgisine sahip işlevler.  
  
- Sembol dosyalarının, yığın çerçevesine karşılık gelen kaynak dosya olmadığını gösteren işlevler.  
  
- `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` klasöründeki `*.natjmc` dosyalarında belirtilen işlevler.  
  
  **Atma**  
  
  Varsayılan olarak, yalnızca `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` klasöründeki `*.natstepfilter` dosyalarında belirtilen işlevler kullanıcı olmayan kod olarak kabul edilir.  
  
  `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`atlama ve çağrı yığını pencere davranışını özelleştirmek için kendi `.natstepfilter` ve `.natjmc` oluşturabilirsiniz.  
  
### <a name="BKMK_CPP_Stepping_behavior"></a>Atlama davranışı  
 Kullanıcı kodundan **(klavye** kısayolu: F11) Kullanıcı olmayan kod yazdığınızda, hata ayıklayıcı bir sonraki Kullanıcı kodu satırına kodda adım adım yapılır. **Dışarı adımla** (klavye: Shift + F11), hata ayıklayıcı sonraki Kullanıcı kodu satırına çalışır. Hiçbir Kullanıcı kodu ile karşılaşılırsa, uygulama kaldırılana kadar bir kesme noktasına isabet veya bir özel durum ortaya çıkana kadar yürütme devam eder.  
  
 Hata ayıklayıcı kullanıcı olmayan kodda kesintiye uğramışsa (örneğin, tüm komut Kullanıcı olmayan kodda bir break olursa), Adımlama Kullanıcı olmayan kodda devam eder.  
  
### <a name="BKMK_CPP_Exception_behavior"></a>Özel durum davranışı  
 Hata ayıklayıcı bir özel durum algıladığında, Kullanıcı veya Kullanıcı olmayan kodda olmasına bakılmaksızın özel durum üzerinde durdurulur. **Özel durumlar** Iletişim kutusunda **Kullanıcı tarafından işlenmeyen** seçenekler yok sayılır.  
  
### <a name="BKMK_CPP_Customize_stepping_behavior"></a>Atlama davranışını özelleştirme  
 `*.natstepfilter` dosyalarında Kullanıcı olmayan kod olarak listeleyerek adım adım işlemler yapabilirsiniz.  
  
- Visual Studio makinesinin tüm kullanıcıları için Kullanıcı olmayan kodu belirtmek için, `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` klasörüne. natstepfilter dosyasını ekleyin.  
  
- Tek bir kullanıcı için Kullanıcı olmayan kodu belirtmek için, `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` klasörüne. natstepfilter dosyasını ekleyin.  
  
  . natstepfilter dosyaları, bu söz dizimini taşıyan XML dosyalarıdır:  
  
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
|İşlev|Gerekli. Kullanıcı dışı işlevler olarak bir veya daha fazla işlevi belirtir.|  
|`Name`|Gerekli. Eşleştirilecek tam işlev adını belirten bir ECMA-262 biçimli normal ifade. Örneğin:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> hata ayıklayıcıya `MyNS::MyClass` içindeki tüm yöntemlerin kullanıcı olmayan kod olarak kabul edileceğini söyler. Eşleşme büyük/küçük harfe duyarlıdır.|  
|`Module`|İsteğe bağlı. İşlevi içeren modülün tam yolunu belirten bir ECMA-262 biçimli normal ifade. Eşleşme büyük/küçük harfe duyarsızdır.|  
|`Action`|Gerekli. Şu büyük/küçük harfe duyarlı değerlerden biri:<br /><br /> -   `NoStepInto` – hata ayıklayıcıya eşleşen işlevin üzerinde ilermasını söyler.<br />-   `StepInto` – hata ayıklayıcının eşleşen işlevlere gitmesini ve eşleşen işlevler için diğer `NoStepInto` geçersiz kılmasını söyler.|  
  
### <a name="BKMK_CPP_Customize_call_stack_behavior"></a>Çağrı yığını davranışını özelleştirme  
 `*.natjmc` dosyalarında belirterek, çağrı yığınlarında Kullanıcı olmayan kod olarak kabul etmek için modüller, kaynak dosyalar ve işlevler belirtebilirsiniz.  
  
- Visual Studio makinesinin tüm kullanıcıları için Kullanıcı olmayan kodu belirtmek için, `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` klasörüne. natjmc dosyasını ekleyin.  
  
- Tek bir kullanıcı için Kullanıcı olmayan kodu belirtmek için,. natjmc dosyasını `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` klasörüne ekleyin.  
  
  . natjmc dosyaları şu söz dizimini taşıyan XML dosyalarıdır:  
  
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
|`Name`|Gerekli. Modülün veya modüllerin tam yolu. Windows joker karakterlerini `?` (sıfır veya bir karakter) ve `*` (sıfır veya daha fazla karakter) kullanabilirsiniz. Örneğin,<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> hata ayıklayıcıya herhangi bir sürücüdeki `\3rdParty\UtilLibs` tüm modülleri dış kod olarak değerlendirmesine söyler.|  
|`Company`|İsteğe bağlı. Yürütülebilir dosyaya katıştırılmış modülü yayımlayan şirketin adı. Bu özniteliği modülleri ortadan kaldırmak için kullanabilirsiniz.|  
  
 **Dosya öğesi öznitelikleri**  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli. Dış kod olarak kabul edilecek kaynak dosyanın veya dosyaların tam yolu. `?` Windows joker karakterlerini kullanabilirsiniz ve yolu belirtirken `*`.|  
  
 **İşlev öğesi öznitelikleri**  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli. Dış kod olarak davranıyilecekleri işlevin tam adı.|  
|`Module`|İsteğe bağlı. İşlevi içeren modülün adı veya tam yolu. Aynı ada sahip işlevleri ayırt etmek için bu özniteliği kullanabilirsiniz.|  
|`ExceptionImplementation`|`true`olarak ayarlandığında, çağrı yığını bu işlev yerine özel durumu oluşturan işlevi görüntüler.|  
  
## <a name="BKMK_JavaScript_Just_My_Code"></a>JavaScript Yalnızca kendi kodum  
  
### <a name="BKMK_JS_User_and_non_user_code"></a>Kullanıcı ve Kullanıcı olmayan kod  
 **Kod sınıflandırmaları**  
  
 JavaScript Yalnızca kendi kodum, kodu aşağıdaki sınıflandırmalardaki kategorilere ayırarak, yığın görüntüsünü Adımlama ve çağır ' a denetler:  
  
|||  
|-|-|  
|**MyCode**|Sahip olduğunuz ve denetlediğiniz Kullanıcı kodu.|  
|**LibraryCode**|Düzenli olarak kullandığınız kitaplıklardaki Kullanıcı olmayan kod ve uygulamanız doğru şekilde çalışır (örneğin, WinJS veya jQuery).|  
|**UnrelatedCode**|Uygulamanızda çalışan kullanıcı olmayan kod, ancak kendinize ait değildir ve uygulamanız doğru bir şekilde çalışması için doğrudan bu değildir (örneğin, reklamları görüntüleyen bir reklam SDK 'Sı). Windows Mağazası projelerinde, uygulamanıza HTTP veya HTTPS URI 'sinden yüklenmiş tüm kodlar de Relatedcode olarak kabul edilir.|  
  
 JavaScript hata ayıklayıcı bu kod türlerini otomatik olarak sınıflandırır:  
  
- Ana bilgisayar tarafından sunulan `eval` işlevine bir dize geçirerek yürütülen betik **MyCode**olarak sınıflandırılır.  
  
- `Function` oluşturucusuna bir dize geçirerek yürütülen betik, **Librarycode**olarak sınıflandırılır.  
  
- WinJS veya Azure SDK gibi bir çerçeve başvurusunda bulunan betik, **Librarycode**olarak sınıflandırılmaktadır.  
  
- `setTimeout`, `setImmediate`veya `setInterval` işlevlerine bir dize geçirerek yürütülen komut dosyası **UnrelatedCode**olarak sınıflandırılır.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`, tüm Visual Studio JavaScript projeleri için diğer kullanıcıyı ve Kullanıcı olmayan kodu belirtir.  
  
  Bir projenin kök klasörüne `mycode.json` adlı bir. JSON dosyası ekleyerek varsayılan sınıflandırmaları değiştirebilir ve belirli dosya ve URL 'leri sınıflandırabilirsiniz.  
  
  Diğer tüm kodlar **MyCode**olarak sınıflandırılır.  
  
### <a name="BKMK_JS_Stepping_behavior"></a>Atlama davranışı  
  
- Bir işlev kullanıcı (**MyCode**) kodu değilse, **Step Into** (klavye kısayolu: F11) **üzerinde adımla** (klavye: F10) olarak davranır.  
  
- Bir adım kullanıcı olmayan (**librarycode** veya **UnrelatedCode**) kodda başlıyorsa, yalnızca kendi kodum etkinleştirilmemişse geçici olarak adımlayın. Kullanıcı koduna geri döndüğünüzde Yalnızca kendi kodum Adımlama yeniden etkinleştirilir.  
  
- Kullanıcı kodundaki bir adım geçerli yürütme bağlamından ayrılmaya neden olduğunda (örneğin, bir olay işleyicisinin son satırında bir adım yapmak gibi), hata ayıklayıcı bir sonraki çalıştırılan Kullanıcı kodu satırında duraklar. Örneğin, **Librarycode** kodunda bir geri çağırma yürütülüyorsa, Kullanıcı kodu sonraki satırı yürütülene kadar hata ayıklayıcı devam eder.  
  
- **Dışarı adımla** (klavye: SHIFT + F11), sonraki Kullanıcı kodu satırında duraklar. Hiçbir Kullanıcı kodu ile karşılaşılırsa, uygulama kaldırılana kadar bir kesme noktasına isabet veya bir özel durum ortaya çıkana kadar yürütme devam eder.  
  
### <a name="BKMK_JS_Breakpoint_behavior"></a>Kesme noktası davranışı  
  
- Herhangi bir kodda ayarlanmış olan kesme noktaları, bu kodun sınıflandırmasından bağımsız olarak her zaman bir vuruş olacaktır  
  
- İçinde `debugger` anahtar kelimesiyle karşılaşılırsa:  
  
  - **Librarycode** kodu, hata ayıklayıcı her zaman kesilir.  

  - **UnrelatedCode** kodu, hata ayıklayıcı durdurulmaz.  
  
### <a name="BKMK_JS_Exception_behavior"></a>Özel durum davranışı  
 İçinde işlenmeyen bir özel durum oluşursa:  
  
- **MyCode** veya **librarycode** kodu, hata ayıklayıcı her zaman kesilir.  
  
- **UnrelatedCode** kodu ve **MyCode** veya **librarycode** kodu çağrı yığınında, hata ayıklayıcı kesilir.  
  
  Özel durumlar iletişim kutusunda özel durum için ilk şans özel durumları etkinse ve özel durum **librarycode** veya **UnrelatedCode** kodu içinde oluşturulursa:  
  
- Özel durum işlenirse, hata ayıklayıcı kesme yapmaz.  
  
- Özel durum işlenmezse, hata ayıklayıcı kesilir.  
  
### <a name="BKMK_JS_Customize_Just_My_Code"></a>Yalnızca kendi kodum özelleştirme  
 Tek bir Visual Studio projesi için Kullanıcı ve Kullanıcı olmayan kodu kategorilere ayırmak üzere, `mycode.json` adlı bir. json dosyasını projenin kök klasörüne ekleyin.  
  
 Sınıflandırmalar şu sırada gerçekleştirilir:  
  
1. Varsayılan sınıflandırmalar  
  
2. `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` dosyasındaki sınıflandırmalar  
  
3. Geçerli projenin `mycode. json` dosyasındaki sınıflandırmalar.  
  
   Her sınıflandırma adımı önceki adımları geçersiz kılar. Bir. JSON dosyası tüm anahtar değer çiftlerini listelemez, **MyCode**, **Kitaplıklar**ve **ilişkisiz** değerler boş diziler olabilir.  
  
   My Code. JSON dosyaları şu sözdizimini kullanır:  
  
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
  
 **Eval, Function ve ScriptBlock**  
  
 **Eval**, **Function**ve **ScriptBlock** anahtar değer çiftleri, dinamik olarak üretilen kodun sınıflandırıldığını belirleme.  
  
|||  
|-|-|  
|**Eval**|Konak tarafından belirtilen `eval` işlevine bir dize geçirerek yürütülen komut dosyası. Varsayılan olarak, eval betiği **MyCode**olarak sınıflandırılır.|  
|**Çalışmayacaktır**|`Function` oluşturucusuna bir dize geçirerek yürütülen komut dosyası. Varsayılan olarak, Işlev betiği **Librarycode**olarak sınıflandırılır.|  
|**ScriptBlock**|`setTimeout`, `setImmediate`veya `setInterval` işlevlerine bir dize geçirerek yürütülen komut dosyası. Varsayılan olarak, ScriptBlock betiği **UnrelatedCode**olarak sınıflandırılır.|  
  
 Değeri şu anahtar sözcüklerden birine değiştirebilirsiniz:  
  
- `MyCode` betiği **MyCode**olarak sınıflandırır.  
  
- `Library` betiği **Librarycode**olarak sınıflandırır.  
  
- `Unrelated` betiği **UnrelatedCode**olarak sınıflandırır.  
  
  **MyCode, kitaplıklar ve Ilgisiz**  
  
  **MyCode**, **Kitaplıklar**ve **ilişkisiz** anahtar değer çiftleri bir sınıflandırmayla dahil etmek istediğiniz URL 'leri veya dosyaları belirtir:  
  
|||  
|-|-|  
|**MyCode**|**MyCode**olarak sınıflandırılan bir URL veya dosya dizisi.|  
|**Kitaplıklar**|**Librarycode**olarak sınıflandırılan bir URL veya dosya dizisi.|  
|**İlgisiz**|**UnrelatedCode**olarak sınıflandırılan bir URL veya dosya dizisi.|  
  
 URL veya dosya dizesi, sıfır veya daha fazla karakterle eşleşen bir veya daha fazla `*` karakteri içerebilir. `*`, normal ifade `.*`eşdeğerdir.
