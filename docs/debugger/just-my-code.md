---
title: Yalnızca kendi kodum Kullanıcı kodunda hata ayıkla | Microsoft Docs
ms.date: 02/13/2019
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c1d474b388dd8f116eb53febb8a472d4c5b8150
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536001"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Yalnızca Yalnızca kendi kodum ile Kullanıcı kodunda hata ayıkla

*Yalnızca kendi kodum* , sistem, çerçeve ve diğer Kullanıcı dışı koda yapılan çağrılar üzerinde otomatik olarak adımlar Içeren bir Visual Studio hata ayıklama özelliğidir. **Çağrı yığını** penceresinde, bu çağrıları **[Dış kod]** çerçevelerine daraltır yalnızca kendi kodum.

Yalnızca kendi kodum .NET, C++ve JavaScript projelerinde farklı şekilde çalışır.

## <a name="BKMK_Enable_or_disable_Just_My_Code"></a>Yalnızca kendi kodum etkinleştir veya devre dışı bırak

Çoğu programlama dili için Yalnızca kendi kodum varsayılan olarak etkindir.

- Visual Studio 'da Yalnızca kendi kodum etkinleştirmek veya devre dışı bırakmak için **araçlar**  > **Seçenekler** (veya **hata ayıklama**  > **seçenekleri**>) altında, **hata ayıklama**  > **genel**' i seçin veya **seçimi kaldırın.**

![Seçenekler iletişim kutusunda Yalnızca kendi kodum etkinleştir](../debugger/media/dbg_justmycode_options.png "Yalnızca kendi kodum etkinleştir")

> [!NOTE]
> **Enable yalnızca kendi kodum** , tüm dillerdeki tüm Visual Studio projeleri için geçerli olan genel bir ayardır.

## <a name="just-my-code-debugging"></a>Yalnızca Kendi Kodumda hata ayıklama

Bir hata ayıklama oturumu sırasında **modüller** penceresi, hata ayıklayıcının, sembol yükleme durumu Ile birlikte kodum (Kullanıcı kodu) olarak davranılması gereken kod modüllerini gösterir. Daha fazla bilgi için bkz. [hata ayıklayıcının uygulamanıza nasıl ilişi hakkında daha fazla bilgi edinin](../debugger/debugger-tips-and-tricks.md#modules_window).

![Modüller penceresindeki Kullanıcı kodu](../debugger/media/dbg_justmycode_module.png "Modüller penceresindeki Kullanıcı kodu")

**Çağrı yığını** veya **Görevler** penceresinde, Kullanıcı olmayan kodu `[External Code]` etiketli bir gri açıklamalı kod çerçevesine daraltır yalnızca kendi kodum.

![Çağrı yığını penceresindeki dış kod çerçevesi](../debugger/media/dbg_justmycode_externalcode.png "Dış kod çerçevesi")

>[!TIP]
>**Modülleri**, **çağrı yığınını**, **görevleri**veya diğer birçok hata ayıklama pencerelerini açmak için bir hata ayıklama oturumunda olmanız gerekir. Hata ayıklama sırasında, **hata ayıklama**  > **Windows**altında, açmak istediğiniz pencereleri seçin.

<a name="BKMK_Override_call_stack_filtering"></a>Kodu daraltılmış **[harici kod]** çerçevesinde görüntülemek Için, **çağrı yığını** veya **görev** penceresinde sağ tıklayın ve bağlam menüsünden **dış kodu göster** ' i seçin. Genişletilmiş dış kod satırları **[Dış kod**] çerçevesinin yerini alır.

![Çağrı yığını penceresinde dış kodu göster](../debugger/media/dbg_justmycode_showexternalcode.png "Dış kodu göster")

> [!NOTE]
> **Dış kodu göster** , Kullanıcı tarafından açılan tüm dillerdeki tüm projelere uygulanan geçerli bir Kullanıcı Profil Oluşturucu ayarıdır.

**Çağrı yığını** penceresinde genişletilmiş bir dış kod satırına çift tıklamak, kaynak kodda çağırma kodu satırını yeşil renkte vurgular. Bulunamayan veya yüklenmeyen dll 'Ler veya diğer modüller için bir sembol veya kaynak bulunamadı sayfası açılabilir.

## <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Yalnızca kendi kodum

.NET projelerinde, Kullanıcı ve Kullanıcı olmayan kodu sınıflandırmak için simge ( *. pdb*) dosyalarını ve program iyileştirmelerini kullanır yalnızca kendi kodum. .NET hata ayıklayıcı, iyileştirilmiş ikilileri ve yüklenmeyen *. pdb* dosyalarını Kullanıcı kodu olmayan bir şekilde değerlendirir.

Üç derleyici özniteliği de .NET hata ayıklayıcının Kullanıcı kodu olarak dikkate düşündüğünü etkiler:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> hata ayıklayıcıya uyguladığı kodun kullanıcı kodu olmadığını söyler.
- <xref:System.Diagnostics.DebuggerHiddenAttribute>, Yalnızca kendi kodum kapalı olsa bile kodu hata ayıklayıcıdan gizler.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>, hata ayıklayıcıya, kod içine adım adım değil, uygulandığı kodda adım adım ilermasını söyler.

.NET hata ayıklayıcı diğer tüm kodları Kullanıcı kodu olacak şekilde değerlendirir.

.NET hata ayıklama sırasında:

- Bir sonraki Kullanıcı kodu satırına kod üzerinde Kullanıcı dışı kod**adımlarında (veya** **F11**) **hata ayıklayın**  > .
- Kullanıcı olmayan kodda**çalıştırılan  > ** **hata ayıklama** (veya **SHIFT** +**F11**), Kullanıcı kodu sonraki satırına çalıştırılır.

Daha fazla Kullanıcı kodu yoksa, hata ayıklama sona erene kadar devam eder, başka bir kesme noktasına veya bir hata oluşturur.

<a name="BKMK_NET_Breakpoint_behavior"></a>Hata ayıklayıcı kullanıcı olmayan kodu kaparsa (örneğin, **hata ayıkla**  > **Tümünü kes** ve Kullanıcı olmayan kodda Duraklat 'ı kullanırsanız), **kaynak** penceresi görünmez. Daha sonra Kullanıcı kodu sonraki satırına gitmek için bir **hata ayıklama**  > **Step** komutunu kullanabilirsiniz.

Kullanıcı olmayan kodda işlenmeyen bir özel durum oluşursa, hata ayıklayıcı özel durumun oluşturulduğu Kullanıcı kodu satırına kesilir.

Özel durum için ilk şans özel durumları etkinleştirilirse, çağıran kullanıcı kodu satırı, kaynak kodunda yeşil renkle vurgulanır. **Çağrı yığını** penceresi **[Dış kod]** etiketli açıklamalı çerçeveyi görüntüler.

## <a name="BKMK_C___Just_My_Code"></a>C++ Yalnızca kendi kodum

Visual Studio 2017 sürüm 15,8 ' den başlayarak, kod adımlaması için Yalnızca kendi kodum de desteklenir. Bu özellik ayrıca [/JMC (yalnızca kodumun hata ayıklama)](/cpp/build/reference/jmc) derleyici anahtarından kullanılmasını gerektirir. Bu anahtar, C++ projelerde varsayılan olarak etkinleştirilir. **Çağrı yığını** penceresi ve yalnızca kendi kodum çağrı yığını desteği için/JMC anahtarı gerekli değildir.

<a name="BKMK_CPP_User_and_non_user_code"></a>Kullanıcı kodu olarak sınıflandırılacak şekilde, Kullanıcı kodunu içeren ikilinin PDB hata ayıklayıcı tarafından yüklenmelidir (Bunu denetlemek için **modüller** penceresini kullanın).

Çağrı **yığını** penceresinde olduğu gibi çağrı yığını davranışı için yalnızca kendi kodum, yalnızca bu işlevleri C++ *Kullanıcı olmayan kod*olarak değerlendirir:

- Sembol dosyasında, atılmış kaynak bilgisine sahip işlevler.
- Sembol dosyalarının, yığın çerçevesine karşılık gelen kaynak dosya olmadığını gösteren işlevler.
- *%VSInstallDirectory%\common7\packages\debugger\visualıcılar* klasöründeki *\*. natjmc* dosyalarında belirtilen işlevler.

' Deki C++ yalnızca kendi kodum, kod atlama davranışı için yalnızca bu işlevleri *Kullanıcı olmayan koda*göre değerlendirir:

- Karşılık gelen PDB dosyası hata ayıklayıcıda yüklenmemiş olan işlevleri.
- *%VSInstallDirectory%\common7\packages\debugger\visualıcılar* klasöründeki *\*. natjmc* dosyalarında belirtilen işlevler.

> [!NOTE]
> Yalnızca kendi kodum kod Adımlama desteği için, C++ Visual Studio 15,8 Preview 3 veya sonrakı sürümlerde MSVC derleyicileri kullanılarak kod derlenmesi ve/JMC derleyici anahtarının etkinleştirilmesi gerekir (varsayılan olarak etkindir). Daha fazla bilgi için bkz [. C++ çağrı yığınını ve kod atlama davranışını özelleştirme](#BKMK_CPP_Customize_call_stack_behavior)ve bu [blog gönderisi](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Eski bir derleyici kullanılarak derlenen kod için *. natstepfilter* dosyaları, yalnızca kendi kodum bağımsız olan kod adımlamayı özelleştirmenin tek yoludur. Bkz [. C++ atlama davranışını özelleştirme](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a>Hata C++ ayıklama sırasında:

- Bir sonraki Kullanıcı kodu satırına kod üzerinde Kullanıcı dışı kod**adımlarında (veya** **F11**) **hata ayıklayın**  > .
- Kullanıcı olmayan kodda**çalıştırılan  > ** **hata ayıklama** (veya **SHIFT** +**F11**), Kullanıcı kodu sonraki satırına çalıştırılır.

Daha fazla Kullanıcı kodu yoksa, hata ayıklama sona erene kadar devam eder, başka bir kesme noktasına veya bir hata oluşturur.

Hata ayıklayıcı kullanıcı olmayan kodda kesintiye uğramışsa (örneğin, **hata ayıkla**  > **Tümünü kes** ve Kullanıcı olmayan kodda Duraklat), Adımlama Kullanıcı olmayan kodda devam eder.

Hata ayıklayıcı bir özel durum ile karşılaşırsanız, Kullanıcı veya Kullanıcı olmayan kodda olup olmayana özel durum üzerinde duraklar. **Özel durum ayarları** Iletişim kutusundaki **Kullanıcı tarafından işlenmeyen** seçenekler yok sayılır.

### <a name="BKMK_CPP_Customize_call_stack_behavior"></a>Çağrı C++ yığınını ve kod Adımlama davranışını özelleştirme

Projeler C++ Için, **çağrı yığını** penceresinin *\*. natjmc* dosyalarında belirterek Kullanıcı dışı kod olarak davrandığı modülleri, kaynak dosyalarını ve işlevleri belirtebilirsiniz. Bu özelleştirme, en son derleyicisini kullanıyorsanız kod adımlaması için de geçerlidir (bkz [ C++ . yalnızca kendi kodum](#BKMK_CPP_User_and_non_user_code)).

- Visual Studio makinesinin tüm kullanıcıları için Kullanıcı olmayan kodu belirtmek için, *. natjmc* dosyasını *%VSInstallDirectory%\common7\packages\debugger\visualıcılar* klasörüne ekleyin.
- Tek bir kullanıcı için Kullanıcı olmayan kodu belirtmek için, *Visual Studio sürüm \> \Visualıcılar* klasörüne *. natjmc* dosyasını <%UserProfile%\My Documents \\ ekleyin.

Bir *. natjmc* dosyası, bu söz dizimi Ile bir XML dosyasıdır:

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
|`Name`|Gerekli. Modülün veya modüllerin tam yolu. Windows joker karakterlerini `?` (sıfır veya bir karakter) ve `*` (sıfır veya daha fazla karakter) kullanabilirsiniz. Örneğin,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> hata ayıklayıcıya herhangi bir sürücüdeki *\3Rdparty\utillibs* içindeki tüm modülleri dış kod olarak değerlendirmesine söyler.|
|`Company`|İsteğe bağlı. Yürütülebilir dosyaya katıştırılmış modülü yayımlayan şirketin adı. Bu özniteliği modülleri ortadan kaldırmak için kullanabilirsiniz.|

 **Dosya öğesi öznitelikleri**

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gerekli. Dış kod olarak kabul edilecek kaynak dosyanın veya dosyaların tam yolu. @No__t_0 Windows joker karakterlerini kullanabilirsiniz ve yolu belirtirken `*`.|

 **İşlev öğesi öznitelikleri**

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gerekli. Dış kod olarak davranıyilecekleri işlevin tam adı.|
|`Module`|İsteğe bağlı. İşlevi içeren modülün adı veya tam yolu. Aynı ada sahip işlevleri ayırt etmek için bu özniteliği kullanabilirsiniz.|
|`ExceptionImplementation`|@No__t_0 olarak ayarlandığında, çağrı yığını bu işlev yerine özel durumu oluşturan işlevi görüntüler.|

### <a name="BKMK_CPP_Customize_stepping_behavior"></a>Yalnızca kendi kodum C++ ayarlarından bağımsız Adımlama davranışını özelleştirme

Projeler C++ ' de *\*. natstepfilter* dosyalarında Kullanıcı olmayan kod olarak listeleyerek adım adım işlemler yapabilirsiniz. *@No__t_1. natstepfilter* dosyalarında listelenen işlevler yalnızca kendi kodum ayarlarına bağımlı değildir.

- Tüm yerel Visual Studio kullanıcıları için Kullanıcı olmayan kodu belirtmek için, *. natstepfilter* dosyasını *%VSInstallDirectory%\common7\packages\debugger\visualıcılar* klasörüne ekleyin.
- Tek bir kullanıcı için Kullanıcı olmayan kodu belirtmek için, *Visual Studio sürüm \> \Visualiciler klasörü <%UserProfile%\My Documents \\* *. natstepfilter* dosyasını ekleyin.

Bir *. natstepfilter* dosyası, bu söz dizimi Ile bir XML dosyasıdır:

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
|`Function`|Gerekli. Kullanıcı dışı işlevler olarak bir veya daha fazla işlevi belirtir.|
|`Name`|Gerekli. Eşleştirilecek tam işlev adını belirten bir ECMA-262 biçimli normal ifade. Örneğin:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> hata ayıklayıcıya `MyNS::MyClass` içindeki tüm yöntemlerin kullanıcı olmayan kod olarak kabul edileceğini söyler. Eşleşme büyük/küçük harfe duyarlıdır.|
|`Module`|İsteğe bağlı. İşlevi içeren modülün tam yolunu belirten bir ECMA-262 biçimli normal ifade. Eşleşme büyük/küçük harfe duyarsızdır.|
|`Action`|Gerekli. Şu büyük/küçük harfe duyarlı değerlerden biri:<br /><br /> `NoStepInto`-hata ayıklayıcıya işlevin üzerinde ilermasını söyler.<br /> `StepInto`-hata ayıklayıcının işlevin içine gitmesini, eşleşen işlev için diğer `NoStepInto` geçersiz kılmasını söyler.|

## <a name="BKMK_JavaScript_Just_My_Code"></a>JavaScript Yalnızca kendi kodum

<a name="BKMK_JS_User_and_non_user_code"></a>JavaScript Yalnızca kendi kodum, kodu aşağıdaki sınıflandırmalardaki kategorilere ayırarak, yığın görüntüsünü Adımlama ve çağır ' a denetler:

|||
|-|-|
|**MyCode**|Sahip olduğunuz ve denetlediğiniz Kullanıcı kodu.|
|**LibraryCode**|Düzenli olarak kullandığınız kitaplıklardaki Kullanıcı olmayan kod ve uygulamanız doğru şekilde çalışır (örneğin, WinJS veya jQuery).|
|**UnrelatedCode**|Uygulamanızda sahip olmadığınız ve uygulamanızın doğru çalışması için dayanmayan Kullanıcı olmayan kod. Örneğin, reklamları görüntüleyen bir reklam SDK 'Sı UnrelatedCode olabilir. UWP projelerinde, uygulamanıza HTTP veya HTTPS URI 'sinden yüklenmiş tüm kodlar de Relatedcode olarak kabul edilir.|

JavaScript hata ayıklayıcısı kodu Kullanıcı veya Kullanıcı olmayan bu sırada sınıflandırır:

1. Varsayılan sınıflandırmalar.
   - Ana bilgisayar tarafından belirtilen `eval` işlevine bir dize geçirerek yürütülen betik **MyCode**' dır.
   - @No__t_0 oluşturucusuna bir dize geçirerek yürütülen betik **Librarycode**' dur.
   - Bir çerçeve başvurusunda, WinJS veya Azure SDK gibi betik, **Librarycode**' tır.
   - @No__t_0, `setImmediate` veya `setInterval` işlevlerine bir dize geçirerek yürütülen betik **UnrelatedCode**.

2. *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.WWA.JSON* dosyasındaki tüm Visual Studio JavaScript projeleri için belirtilen sınıflandırmalar.

3. Geçerli projenin *MyCode. JSON* dosyasındaki sınıflandırmalar.

Her sınıflandırma adımı önceki adımları geçersiz kılar.

Diğer tüm kodlar **MyCode**olarak sınıflandırılır.

JavaScript projesinin kök klasörüne *MyCode. JSON* adlı bir *. JSON* dosyası ekleyerek varsayılan sınıflandırmaları değiştirebilir ve belirli dosyaları ve URL 'leri Kullanıcı veya Kullanıcı dışı kod olarak sınıflandırabilirsiniz. Bkz. [JavaScript yalnızca kendi kodum özelleştirme](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a>JavaScript hata ayıklaması sırasında:

- Bir işlev kullanıcı olmayan bir kod ise, **hata ayıklama**  > **Step Into** (veya **F11**), **hata ayıklama**  > **adımla** (veya **F10**) aynı şekilde davranır.
- Bir adım kullanıcı olmayan (**librarycode** veya **UnrelatedCode**) kodda başlıyorsa, yalnızca kendi kodum etkin olmadığında geçici olarak adımlayın. Kullanıcı koduna döndüğünüzde Yalnızca kendi kodum Adımlama yeniden etkinleştirilir.
- Bir Kullanıcı kodu adımı geçerli yürütme bağlamından ayrılmaya neden olduğunda, hata ayıklayıcı bir sonraki yürütülen kullanıcı kod satırından sona erer. Örneğin, **Librarycode** kodunda bir geri çağırma yürütülüyorsa, Kullanıcı kodu sonraki satırı yürütülene kadar hata ayıklayıcı devam eder.
- **Step Out** (veya **SHIFT** +**F11**), sonraki Kullanıcı kodu satırında durduruluyor.

Daha fazla Kullanıcı kodu yoksa, hata ayıklama sona erene kadar devam eder, başka bir kesme noktasına veya bir hata oluşturur.

Kodda ayarlanan kesme noktaları her zaman isabet ediyor, ancak kod sınıflandırıldı.

- **Librarycode**içinde `debugger` anahtar sözcüğü oluşursa, hata ayıklayıcı her zaman kesilir.
- @No__t_0 anahtar sözcüğü **UnrelatedCode**içinde oluşursa, hata ayıklayıcı durdurulmaz.

<a name="BKMK_JS_Exception_behavior"></a>**MyCode** veya **librarycode** kodunda işlenmeyen bir özel durum oluşursa, hata ayıklayıcı her zaman kesilir.

**UnrelatedCode**içinde işlenmeyen bir özel durum oluşursa ve **MyCode** veya **librarycode** çağrı yığınında olursa hata ayıklayıcı kesilir.

Özel durum için birinci şans özel durumları etkinleştirilmişse ve özel durum **librarycode** veya **UnrelatedCode**içinde oluşursa:

- Özel durum işlenirse, hata ayıklayıcı kesme yapmaz.
- Özel durum işlenmezse, hata ayıklayıcı kesilir.

### <a name="BKMK_JS_Customize_Just_My_Code"></a>JavaScript Yalnızca kendi kodum özelleştirme

Tek bir JavaScript projesi için Kullanıcı ve Kullanıcı olmayan kodu kategorilere ayırmak üzere, projenin kök klasörüne *MyCode. JSON* adlı bir *. JSON* dosyası ekleyebilirsiniz.

Bu dosyadaki belirtimlerde varsayılan sınıflandırmalar ve *MyCode. default. WWA. JSON* dosyası geçersiz kılınır. *MyCode. JSON* dosyasının tüm anahtar değer çiftlerini listeme gereksinimi yoktur. **MyCode**, **Kitaplıklar**ve **ilişkisiz** değerler boş diziler olabilir.

*MyCode. JSON* dosyaları şu sözdizimini kullanır:

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, Function ve ScriptBlock**

**Eval**, **Function**ve **ScriptBlock** anahtar değer çiftleri, dinamik olarak üretilen kodun sınıflandırıldığını belirleme:

|||
|-|-|
|**Eval**|Konak tarafından belirtilen `eval` işlevine bir dize geçirerek yürütülen komut dosyası. Varsayılan olarak, eval betiği **MyCode**olarak sınıflandırılır.|
|**Çalışmayacaktır**|@No__t_0 oluşturucusuna bir dize geçirerek yürütülen komut dosyası. Varsayılan olarak, Işlev betiği **Librarycode**olarak sınıflandırılır.|
|**ScriptBlock**|@No__t_0, `setImmediate` veya `setInterval` işlevlerine bir dize geçirerek yürütülen komut dosyası. Varsayılan olarak, ScriptBlock betiği **UnrelatedCode**olarak sınıflandırılır.|

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

URL veya dosya dizesinde sıfır veya daha fazla karakterle eşleşen bir veya daha fazla `*` karakteri olabilir. `*`, normal ifade `.*` aynıdır.
