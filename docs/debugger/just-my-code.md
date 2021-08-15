---
title: Yalnızca kendi kodum | ile kullanıcı kodunda hata ayıklama Microsoft Docs
description: Yalnızca kendi kodum, kullanıcı olmayan koda yapılan çağrılar üzerinde otomatik olarak adım adım atılan bir hata ayıklama özelliğidir. Bu özelliği etkinleştirmeyi, devre dışı bırakmayı ve kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2cdf4e14f61e051b282336fbeec2a53fffb89c8ff3316de1242b5f2c7ff8921f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121325100"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Yalnızca kullanıcı kodunda hata ayıklama ve Yalnızca kendi kodum

*Yalnızca kendi kodum,* Visual Studio, çerçeveye ve diğer kullanıcı olmayan kodlara yapılan çağrılar üzerinden otomatik olarak adım adım geçen bir hata ayıklama özelliğidir. Çağrı Yığını **penceresinde,** Yalnızca kendi kodum çağrıları **[Dış Kod] çerçevelerine daraltıyor.**

Yalnızca kendi kodum .NET, C++ ve JavaScript projelerinde farklı çalışır.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Etkinleştirme veya devre dışı Yalnızca kendi kodum

Çoğu programlama dili için Yalnızca kendi kodum varsayılan olarak etkindir.

- Visual Studio'de Yalnızca kendi kodum'ı etkinleştirmek veya devre dışı bırakmak için, Araçlar Seçenekleri (veya Hata Ayıklama Seçenekleri) altında > Hata Ayıklama Genel'i seçin  >     >     >   **veya Etkinleştir'in Yalnızca kendi kodum.**

![Seçenekler Yalnızca kendi kodum iletişim kutusunda Ayarları Etkinleştir](../debugger/media/dbg_justmycode_options.png "Yalnızca kendi kodum")

> [!NOTE]
> **Enable Yalnızca kendi kodum,** tüm dillerdeki tüm projelerde Visual Studio genel bir ayardır.

## <a name="just-my-code-debugging"></a>Yalnızca Kendi Kodumda hata ayıklama

Hata ayıklama oturumu sırasında **Modüller penceresi,** hata ayıklayıcının kodum (kullanıcı kodu) olarak davranan kod modüllerini ve sembol yükleme durumunu gösterir. Daha fazla bilgi için [bkz. Hata ayıklayıcının uygulamanıza nasıl ekli olduğu hakkında daha fazla bilgi.](../debugger/debugger-tips-and-tricks.md#modules_window)

![Modüller penceresindeki kullanıcı kodu](../debugger/media/dbg_justmycode_module.png "Modüller penceresindeki kullanıcı kodu")

Çağrı **Yığını veya** Görevler **penceresinde,** Yalnızca kendi kodum olmayan kodu, etiketli gri açıklamalı bir kod çerçevesine daraltıyor. `[External Code]`

![Çağrı Yığını penceresindeki Dış Kod çerçevesi](../debugger/media/dbg_justmycode_externalcode.png "Dış Kod çerçevesi")

>[!TIP]
>Modüller, **Çağrı**  **Yığını,** Görevler veya diğer hata ayıklama pencerelerini açmak için bir hata ayıklama oturumundasınız. Hata ayıklama sırasında Hata  >  **ayıkla Windows** altında açmak istediğiniz pencereleri seçin.

<a name="BKMK_Override_call_stack_filtering"></a>Daraltılmış **[Dış Kod]** çerçevesinde kodu görüntülemek için Çağrı Yığını veya  Görev penceresine  sağ tıklayın ve bağlam menüsünden Dış Kodu Göster'i seçin.  Genişletilmiş dış kod satırları [Dış Kod ] **çerçevesini** değiştirir.

![Çağrı Yığını penceresinde Dış Kodu Göster](../debugger/media/dbg_justmycode_showexternalcode.png "Dış Kodu Göster")

> [!NOTE]
> **Dış Kodu Göster,** kullanıcı tarafından açılan tüm dillerdeki tüm projelere uygulanan geçerli bir kullanıcı profili oluşturma ayarıdır.

Çağrı Yığını penceresinde genişletilmiş bir  dış kod satırına çift tıklarsanız, kaynak kodda çağırma kodu satırı yeşil olarak vurgulanır. Bulunamadı veya yüklenmemiş DIĞER modüller için bir sembol veya kaynak bulunamadı sayfası açabilirsiniz.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Yalnızca kendi kodum

.NET projelerinde, Yalnızca kendi kodum ve kullanıcı olmayan kodu sınıflandırmak için sembol (*.pdb*) dosyalarını ve program iyileştirmelerini kullanır. .NET hata ayıklayıcısı, iyileştirilmiş ikili dosyaları ve yüklenmemiş *.pdb* dosyalarını kullanıcı olmayan kod olarak kabul ediyor.

Üç derleyici özniteliği, .NET hata ayıklayıcısının kullanıcı kodu olarak kabul edilenleri de etkiler:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> hata ayıklayıcısına uygulandığı kodun kullanıcı kodu olmadığını söyler.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> , hata ayıklayıcısı kapalı olsa bile Yalnızca kendi kodum gizler.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> hata ayıklayıcıya, koda adım adım değil uygulandığı kodda adım adım yol atmayı söyler.

.NET hata ayıklayıcısı diğer tüm kodu kullanıcı kodu olarak kabul ediyor.

.NET hata ayıklaması sırasında:

- **Hata ayıklama**  >  **Kodun** sonraki kullanıcı kodu satırına kadar olan kullanıcı dışı kod adımlarda Içine Adımla (veya **F11).**
- **Hata ayıklama**  >  **Kullanıcı olmayan** **kodda Step** Out (veya + **Shift F11)** kullanıcı kodunun sonraki satırına çalışır.

Başka kullanıcı kodu yoksa hata ayıklama sona erinceye, başka bir kesme noktasıyla karşılaşana veya hataya neden olana kadar devam eder.

<a name="BKMK_NET_Breakpoint_behavior"></a>Hata ayıklayıcısı kullanıcı olmayan kodda hata ayıklarsa (örneğin, Hata Ayıklama Tüm Kodlarda Hata Ayıkla ve kullanıcı dışı kodda duraklat'ı kullanırsınız), Kaynak Yok penceresi  >   görüntülenir.  Ardından bir Hata Ayıklama **Adımı**  >  **komutunu kullanarak** bir sonraki kullanıcı kodu satırına gidebilirsiniz.

Kullanıcı olmayan kodda işilmeyen bir özel durum oluşursa, hata ayıklayıcı özel durumun oluştuğu kullanıcı kod satırına sonlanır.

Özel durum için ilk şans özel durumları etkinleştirilirse, çağıran kullanıcı kodu satırı kaynak kodda yeşil renkle vurgulanır. Çağrı **Yığını penceresi,[Dış** Kod] etiketli **açıklamalı çerçeveyi görüntüler.**

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> C++ Yalnızca kendi kodum

2017 Visual Studio 15.8'den başlayarak, Yalnızca kendi kodum adımlama için de destek de vardır. Bu özellik ayrıca [/JMC (Yalnızca kodumda hata ayıklama) derleyici anahtarının](/cpp/build/reference/jmc) kullanımını gerektirir. Anahtar, C++ projelerinde varsayılan olarak etkindir. **Yalnızca kendi kodum'daki** Çağrı Yığını penceresi ve çağrı yığını desteği için /JMC anahtarı gerekli değildir.

<a name="BKMK_CPP_User_and_non_user_code"></a>Kullanıcı kodu olarak sınıflandırılacak, kullanıcı kodunu içeren ikili için PDB hata ayıklayıcı  tarafından yükleniyor (bunu kontrol etmek için Modüller penceresini kullanın).

Çağrı Yığını penceresinde olduğu gibi  çağrı yığını davranışı için, C++ Yalnızca kendi kodum yalnızca bu işlevleri kullanıcı olmayan kod *olarak kabul eder:*

- Semboller dosyasındaki kaynak bilgileri çıkarılmış işlevler.
- Sembol dosyalarının yığın çerçevesine karşılık gelen bir kaynak dosya olmadığını işaret eden işlevler.
- *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* *\* klasöründeki .natjmc* dosyalarında belirtilen işlevler.

Kod adımlama davranışı Yalnızca kendi kodum C++ içinde bu işlevleri yalnızca kullanıcı olmayan kod *olarak kabul eder:*

- Hata ayıklayıcıda karşılık gelen PDB dosyasının yüklenmemiş olduğu işlevleri.
- *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* *\* klasöründeki .natjmc* dosyalarında belirtilen işlevler.

> [!NOTE]
> Yalnızca kendi kodum'de kod adımlama desteği için C++ kodunun Visual Studio 15.8 Preview 3 veya sonraki bir sürümüne sahip MSVC derleyicileri kullanılarak derlenmiş olması ve /JMC derleyici anahtarının etkinleştirilmesi gerekir (varsayılan olarak etkindir). Ek ayrıntılar için [bkz. C++ çağrı yığınını ve kod adımlama davranışını özelleştirme](#BKMK_CPP_Customize_call_stack_behavior)) ve bu blog [gönderisi.](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/) Daha eski bir derleyici kullanılarak derlenmiş kodlar *için,natstepfilter* dosyaları kod adımlama özelleştirmenin tek yoludur ve bu dosyalardan Yalnızca kendi kodum. Bkz. [C++ adımlama davranışını özelleştirme.](#BKMK_CPP_Customize_stepping_behavior)

<a name="BKMK_CPP_Stepping_behavior"></a> C++ hata ayıklaması sırasında:

- **Hata ayıklama**  >  **Kodun** sonraki kullanıcı kodu satırına kadar olan kullanıcı dışı kod adımlarda Içine Adımla (veya **F11).**
- **Hata ayıklama**  >  **Kullanıcı olmayan** **kodda Step** Out (veya + **Shift F11)** kullanıcı kodunun sonraki satırına çalışır.

Başka kullanıcı kodu yoksa hata ayıklama sona erinceye, başka bir kesme noktasıyla karşılaşana veya hataya neden olana kadar devam eder.

Hata ayıklayıcı kullanıcı olmayan kodda hata ayıklarsa (örneğin, Hata Ayıklama Tüm Kodda Hata Ayıkla ve kullanıcı olmayan kodda duraklat'ı kullanırsanız), adımlama kullanıcı olmayan   >   kodda devam eder.

Hata ayıklayıcısı bir özel durumla karşılaşıyorsa, ister kullanıcı kodunda ister kullanıcı olmayan kodda olsun özel durum üzerinde durur. **Özel Durum Bilgileri iletişim** kutusundaki **kullanıcı tarafından Ayarlar** seçenekleri yoksayılır.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> C++ çağrı yığınını ve kod adımlama davranışını özelleştirme

C++ projeleri için, *\* .natjmc* dosyalarında belirterek  Çağrı Yığını penceresinin kullanıcı olmayan kod olarak kabul eder modüllerini, kaynak dosyalarını ve işlevlerini belirtebilirsiniz. Bu özelleştirme, en son derleyiciyi kullanıyorsanız kod adımlama için de geçerlidir (bkz. [C++ Yalnızca kendi kodum).](#BKMK_CPP_User_and_non_user_code)

- Visual Studio makinesinin tüm kullanıcıları için kullanıcı olmayan kodu belirtmek için *.natjmc* dosyasını *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers klasörüne* ekleyin.
- Tek bir kullanıcının kullanıcı olmayan kodunu belirtmek için *.natjmc* dosyasını *%USERPROFILE%\Belgelerim \\<Visual Studio sürümü \> \Visualizers klasörüne* ekleyin.

*.natjmc dosyası,* şu söz dizimleriyle bir XML dosyasıdır:

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
|`Name`|Gereklidir. Modülün veya modüllerin tam yolu. Joker karakter karakterlerini Windows (sıfır veya bir karakter) ve (sıfır veya daha fazla `?` karakter) `*` kullanabilirsiniz. Örneğin,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> , hata ayıklayıcısına herhangi bir sürücüde *\3rdParty\UtilLibs'daki* tüm modülleri dış kod olarak kabul eder.|
|`Company`|İsteğe bağlı. Yürütülebilir dosyaya eklenmiş olan modülü yayımlayan şirketin adı. Bu özniteliği kullanarak modüllerin daha kolay bir şekilde karartabilirsiniz.|

 **Dosya öğesi öznitelikleri**

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gereklidir. Dış kod olarak kabul etmek için kaynak dosyanın veya dosyaların tam yolu. Varsayılan joker Windows ve yolu `?` `*` belirtirken kullanabilirsiniz.|

 **İşlev öğesi öznitelikleri**

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gereklidir. Dış kod olarak kabul etmek için işlevin tam adı.|
|`Module`|İsteğe bağlı. İşlevi içeren modülün adı veya tam yolu. Bu özniteliği, aynı adla işlevlerin belirsizliklerini yok etmek için kullanabilirsiniz.|
|`ExceptionImplementation`|olarak `true` ayarlanırsa, çağrı yığını bu işlev yerine özel durumu çağıran işlevi görüntüler.|

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> Farklı ayarlardan bağımsız olarak C++ Yalnızca kendi kodum özelleştirme

C++ projelerinde, *\* .natstepfilter* dosyalarında kullanıcı olmayan kod olarak listeleyene kadar adım atacak işlevleri belirtebilirsiniz. *\* .natstepfilter dosyalarında listelenen* işlevler, uygulama ayarlarına Yalnızca kendi kodum değildir.

- Tüm yerel uygulama kullanıcıları için kullanıcı olmayan Visual Studio belirtmek için *.natstepfilter* dosyasını *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers klasörüne* ekleyin.
- Tek bir kullanıcının kullanıcı olmayan kodunu belirtmek için *.natstepfilter* dosyasını *%USERPROFILE%\Belgelerim \\<Visual Studio sürümü \> \Visualizers klasörüne* ekleyin.

*.natstepfilter dosyası* şu söz dizimini olan bir XML dosyasıdır:

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
|`Function`|Gereklidir. Bir veya daha fazla işlevi kullanıcı olmayan işlevler olarak belirtir.|
|`Name`|Gereklidir. Eşleşmek için tam işlev adını belirten ECMA-262 biçimli bir normal ifade. Örnek:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> , hata ayıklayıcısına'daki tüm `MyNS::MyClass` yöntemlerin kullanıcı dışı kod olarak kabul edilir olduğunu söyler. Eşleşme büyük/büyük/büyük harfe duyarlıdır.|
|`Module`|İsteğe bağlı. İşlevi içeren modülün tam yolunu belirten ECMA-262 biçimli bir normal ifade. Eşleşme büyük/büyük/büyük harfe duyarlı değildir.|
|`Action`|Gereklidir. Büyük/büyük/büyük harfe duyarlı şu değerlerden biri:<br /><br /> `NoStepInto`  - hata ayıklayıcısına işlevin üzerinden adım attırmalarını söyler.<br /> `StepInto`  - hata ayıklayıcısına işleve adım atarak, eşilen işlev için `NoStepInto` diğerlerini geçersiz kılmasını söyler.|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript Yalnızca kendi kodum

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript Yalnızca kendi kodum sınıflandırmalardan biri içinde kategorilere ayırmaya göre adımlama ve çağrı yığını görüntüleme denetimlerini içerir:

|Sınıflandırma|Açıklama|
|-|-|
|**MyCode**|Sahip olduğunuz ve denetiminizi yapılan kullanıcı kodu.|
|**LibraryCode**|Düzenli olarak kullanabileceğiniz kitaplıklardan kullanıcı olmayan kod ve uygulamanın düzgün çalışması için (winJS veya jQuery gibi) bağlı olması.|
|**UnrelatedCode**|Uygulamanıza sahip olmadığınız ve düzgün çalışması için uygulamanıza bağlı olmayan kullanıcı olmayan kod. Örneğin, reklam görüntüleyen bir reklam SDK'sı UnrelatedCode olabilir. UWP projelerinde, http veya HTTPS URI'lerinden uygulamanıza yüklenen tüm kodlar Da UnrelatedCode olarak kabul edilir.|

JavaScript hata ayıklayıcısı kodu şu sırayla kullanıcı veya kullanıcı olmayan olarak sınıflar:

1. Varsayılan sınıflandırmalar.
   - Konak tarafından sağlanan işleve bir dize geçerek yürütülen betik `eval` **MyCode'dur.**
   - Oluşturucuya bir dize geçerek yürütülen `Function` betik **LibraryCode'dur.**
   - WinJS veya Azure SDK gibi bir çerçeve başvurusunda betik **LibraryCode'dır.**
   - , veya işlevlerine bir dize geçerek yürütülen `setTimeout` `setImmediate` `setInterval` betik **UnrelatedCode 'dır.**

2. *Dosyada %VSInstallDirectory%Visual Studio* JavaScript projeleri için belirtilen \JavaScript\JustMyCode\mycode.default.wwa.jssınıflandırmalar.

3. Geçerli projenin *mycode.jsdosyasındaki* sınıflandırmalar.

Her sınıflandırma adımı önceki adımları geçersiz kılar.

Diğer tüm kod **MyCode olarak sınıflandırılır.**

Varsayılan sınıflandırmaları değiştirebilir ve javaScript projesinin kök klasörüne *mycode.js* adlı *bir .json* dosyası ekleyerek belirli dosyaları ve URL'leri kullanıcı veya kullanıcı olmayan kod olarak sınıflandırabilirsiniz. Bkz. [JavaScript'i Yalnızca kendi kodum.](#BKMK_JS_Customize_Just_My_Code)

<a name="BKMK_JS_Stepping_behavior"></a> JavaScript hata ayıklaması sırasında:

- Bir işlev kullanıcı olmayan bir kodsa, **Hata** Ayıklama Adımını At  >   (veya **F11)** Hata Ayıklama Adımı   >   (veya **F10)** ile aynı şekilde davranır.
- Adım kullanıcı olmayan (**LibraryCode** veya **UnrelatedCode**) kodunda başlıyorsa, adımlama geçici olarak Yalnızca kendi kodum etkinleştirilmemiş gibi davranır. Kullanıcı koduna geri dönüp adımlama Yalnızca kendi kodum yeniden etkinleştirilir.
- Bir kullanıcı kodu adımı geçerli yürütme bağlamından ayrılmakla sonuçlanırsa, hata ayıklayıcı bir sonraki yürütülen kullanıcı kodu satırına durur. Örneğin, bir geri çağırma **LibraryCode** kodunda yürütülürse, hata ayıklayıcı bir sonraki kullanıcı kodu satırı yürütülene kadar devam eder.
- **Step Out** **(veya Shift** + **F11)** kullanıcı kodunun sonraki satırı üzerinde durur.

Başka kullanıcı kodu yoksa hata ayıklama sona erinceye, başka bir kesme noktasıyla karşılaşana veya hataya neden olana kadar devam eder.

Kodda ayarlanmış kesme noktalarına her zaman isabet olur, ancak kod sınıflandırılır.

- anahtar sözcüğü `debugger` LibraryCode içinde **oluşursa** hata ayıklayıcı her zaman bozar.
- Anahtar sözcüğü `debugger` **UnrelatedCode içinde oluşursa** hata ayıklayıcı durmaz.

<a name="BKMK_JS_Exception_behavior"></a> İşlenemeyen bir özel durum **MyCode** veya **LibraryCode kodunda** oluşursa, hata ayıklayıcı her zaman bozar.

**UnrelatedCode** içinde işlenmemiş bir özel durum oluşursa ve Çağrı yığınında **MyCode** veya **LibraryCode** varsa hata ayıklayıcı sonlanır.

Özel durum için ilk şans özel durumları etkinleştirildiyse ve özel durum **LibraryCode** veya **UnrelatedCode içinde oluşursa:**

- Özel durum işlemesi, hata ayıklayıcı kesmez.
- Özel durum işlanmazsa hata ayıklayıcı bozar.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> JavaScript Yalnızca kendi kodum

Tek bir JavaScript projesi için kullanıcı kodunu ve kullanıcı olmayan kodu kategorilere ayırmak için, projenin kök klasörüne *mycode.js* adlı *bir .json* dosyası ekleyin.

Bu dosyada yer alan belirtimler, varsayılan sınıflandırmaları ve *mycode.default.wwa.jsgeçersiz* kılar. Dosya *mycode.jstüm* anahtar değer çiftlerini listeleye ihtiyacı yoktur. **MyCode,** **Kitaplıklar** ve **Ilgisiz değerler** boş diziler olabilir.

*Mycode.jsdosyalarda* bu söz dizimi kullanılır:

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

**Değerlendirme, İşlev ve ScriptBlock**

Değerlendirme, **İşlev** ve **ScriptBlock** anahtar değer çiftleri, dinamik olarak oluşturulan kodun nasıl sınıflandırılır olduğunu belirler: 

|Ad|Açıklama|
|-|-|
|**Dğer**|Konak tarafından sağlanan işleve bir dize geçerek yürütülen `eval` betik. Varsayılan olarak, Eval betiği **MyCode olarak sınıflandırılır.**|
|**İşlev**|Oluşturucuya bir dize geçerek yürütülen `Function` betik. Varsayılan olarak, İşlev betiği LibraryCode olarak **sınıflandırılır.**|
|**ScriptBlock**|, veya işlevlerine bir dize geçerek yürütülen `setTimeout` `setImmediate` `setInterval` betik. ScriptBlock betiği varsayılan olarak **UnrelatedCode olarak sınıflandırılır.**|

Değeri şu anahtar sözcüklerden biri olarak değiştirebilirsiniz:

- `MyCode`betiği **MyCode olarak sınıflar.**
- `Library`betiği LibraryCode olarak **sınıflar.**
- `Unrelated`betiği **UnrelatedCode olarak sınıflandır.**

**MyCode, Kitaplıklar ve Ilgisiz**

**MyCode,** **Kitaplıklar** ve **Ilgisiz** anahtar değer çiftleri, bir sınıflandırmaya eklemek istediğiniz URL'leri veya dosyaları belirtir:

|Ad|Açıklama|
|-|-|
|**MyCode**|MyCode olarak sınıflandırılan URL'ler veya **dosyalar dizisi.**|
|**Kitaplıklar**|LibraryCode olarak sınıflandırılan URL'ler veya dosyalar **dizisi.**|
|**Alakasız**|UnrelatedCode olarak sınıflandırılan URL'ler **veya dosyalar dizisi.**|

URL veya dosya dizesi, sıfır veya daha fazla karakterle `*` eşan bir veya daha fazla karaktere sahip olabilir. `*` , normal ifadeyle `.*` aynıdır.
