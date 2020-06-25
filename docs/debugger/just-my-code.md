---
title: Yalnızca kendi kodum Kullanıcı kodunda hata ayıkla | Microsoft Docs
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58e233be301630b00031bb90cd95fc78c2697c4e
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348437"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Yalnızca Yalnızca kendi kodum ile Kullanıcı kodunda hata ayıkla

*Yalnızca kendi kodum* , sistem, çerçeve ve diğer Kullanıcı dışı koda yapılan çağrılar üzerinde otomatik olarak adımlar Içeren bir Visual Studio hata ayıklama özelliğidir. **Çağrı yığını** penceresinde, bu çağrıları **[Dış kod]** çerçevelerine daraltır yalnızca kendi kodum.

Yalnızca kendi kodum .NET, C++ ve JavaScript projelerinde farklı şekilde çalışır.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a>Yalnızca kendi kodum etkinleştir veya devre dışı bırak

Çoğu programlama dili için Yalnızca kendi kodum varsayılan olarak etkindir.

- Visual Studio 'da yalnızca kendi kodum etkinleştirmek veya devre dışı bırakmak için, **Araçlar**  >  **Seçenekler** (veya **hata ayıklama**  >  **seçenekleri**) altında, genel **hata ayıklama**>  >  **General**' i seçin veya seçimini **yalnızca kendi kodum**kaldırın.

![Seçenekler iletişim kutusunda Yalnızca kendi kodum etkinleştir](../debugger/media/dbg_justmycode_options.png "Yalnızca kendi kodum etkinleştir")

> [!NOTE]
> **Enable yalnızca kendi kodum** , tüm dillerdeki tüm Visual Studio projeleri için geçerli olan genel bir ayardır.

## <a name="just-my-code-debugging"></a>Yalnızca Kendi Kodumda hata ayıklama

Bir hata ayıklama oturumu sırasında **modüller** penceresi, hata ayıklayıcının, sembol yükleme durumu Ile birlikte kodum (Kullanıcı kodu) olarak davranılması gereken kod modüllerini gösterir. Daha fazla bilgi için bkz. [hata ayıklayıcının uygulamanıza nasıl ilişi hakkında daha fazla bilgi edinin](../debugger/debugger-tips-and-tricks.md#modules_window).

![Modüller penceresindeki Kullanıcı kodu](../debugger/media/dbg_justmycode_module.png "Modüller penceresindeki Kullanıcı kodu")

**Çağrı yığını** veya **Görevler** penceresinde, Kullanıcı olmayan kodu, etiketli bir gri açıklamalı kod çerçevesine daraltır yalnızca kendi kodum `[External Code]` .

![Çağrı yığını penceresindeki dış kod çerçevesi](../debugger/media/dbg_justmycode_externalcode.png "Dış kod çerçevesi")

>[!TIP]
>**Modülleri**, **çağrı yığınını**, **görevleri**veya diğer birçok hata ayıklama pencerelerini açmak için bir hata ayıklama oturumunda olmanız gerekir. Hata ayıklama sırasında, **hata ayıklama**  >  **Windows**altında, açmak istediğiniz pencereleri seçin.

<a name="BKMK_Override_call_stack_filtering"></a>Kodu daraltılmış **[harici kod]** çerçevesinde görüntülemek Için, **çağrı yığını** veya **görev** penceresinde sağ tıklayın ve bağlam menüsünden **dış kodu göster** ' i seçin. Genişletilmiş dış kod satırları **[Dış kod**] çerçevesinin yerini alır.

![Çağrı yığını penceresinde dış kodu göster](../debugger/media/dbg_justmycode_showexternalcode.png "Dış kodu göster")

> [!NOTE]
> **Dış kodu göster** , Kullanıcı tarafından açılan tüm dillerdeki tüm projelere uygulanan geçerli bir Kullanıcı Profil Oluşturucu ayarıdır.

**Çağrı yığını** penceresinde genişletilmiş bir dış kod satırına çift tıklamak, kaynak kodda çağırma kodu satırını yeşil renkte vurgular. Bulunamayan veya yüklenmeyen dll 'Ler veya diğer modüller için bir sembol veya kaynak bulunamadı sayfası açılabilir.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Yalnızca kendi kodum

.NET projelerinde, Kullanıcı ve Kullanıcı olmayan kodu sınıflandırmak için simge (*. pdb*) dosyalarını ve program iyileştirmelerini kullanır yalnızca kendi kodum. .NET hata ayıklayıcı, iyileştirilmiş ikilileri ve yüklenmeyen *. pdb* dosyalarını Kullanıcı kodu olmayan bir şekilde değerlendirir.

Üç derleyici özniteliği de .NET hata ayıklayıcının Kullanıcı kodu olarak dikkate düşündüğünü etkiler:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>hata ayıklayıcıya uyguladığı kodun kullanıcı kodu olmadığını söyler.
- <xref:System.Diagnostics.DebuggerHiddenAttribute>Yalnızca kendi kodum kapalı olsa bile kodu hata ayıklayıcıdan gizler.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>hata ayıklayıcının, koda adım adım değil, uygulandığı kodda ilermasını söyler.

.NET hata ayıklayıcı diğer tüm kodları Kullanıcı kodu olacak şekilde değerlendirir.

.NET hata ayıklama sırasında:

- **Hata Ayıkla**  >  Kullanıcı kodunun sonraki satırına kod üzerinde Kullanıcı dışı kod adımlarında **adımla** (veya **F11**).
- **Hata Ayıkla**  >  Kullanıcı dışı kod üzerinde **Step Out** (veya **Shift** + **F11**), Kullanıcı kodu için bir sonraki satırda çalışır.

Daha fazla Kullanıcı kodu yoksa, hata ayıklama sona erene kadar devam eder, başka bir kesme noktasına veya bir hata oluşturur.

<a name="BKMK_NET_Breakpoint_behavior"></a>Hata ayıklayıcı kullanıcı olmayan kodu kaparsa (örneğin, **hata ayıklama**  >  **kesmeyi** kullanırsanız ve Kullanıcı olmayan kodda durakladıysanız), **kaynak** penceresi görünmez. Daha sonra **Debug**  >  Kullanıcı kodu sonraki satırına gitmek için bir hata ayıklama**adımı** komutunu kullanabilirsiniz.

Kullanıcı olmayan kodda işlenmeyen bir özel durum oluşursa, hata ayıklayıcı özel durumun oluşturulduğu Kullanıcı kodu satırına kesilir.

Özel durum için ilk şans özel durumları etkinleştirilirse, çağıran kullanıcı kodu satırı, kaynak kodunda yeşil renkle vurgulanır. **Çağrı yığını** penceresi **[Dış kod]** etiketli açıklamalı çerçeveyi görüntüler.

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a>C++ Yalnızca kendi kodum

Visual Studio 2017 sürüm 15,8 ' den başlayarak, kod adımlaması için Yalnızca kendi kodum de desteklenir. Bu özellik ayrıca [/JMC (yalnızca kodumun hata ayıklama)](/cpp/build/reference/jmc) derleyici anahtarından kullanılmasını gerektirir. Anahtar, C++ projelerinde varsayılan olarak etkindir. **Çağrı yığını** penceresi ve yalnızca kendi kodum çağrı yığını desteği için/JMC anahtarı gerekli değildir.

<a name="BKMK_CPP_User_and_non_user_code"></a>Kullanıcı kodu olarak sınıflandırılacak şekilde, Kullanıcı kodunu içeren ikilinin PDB hata ayıklayıcı tarafından yüklenmelidir (Bunu denetlemek için **modüller** penceresini kullanın).

Çağrı **yığını** penceresinde olduğu gibi çağrı yığını davranışı Için, C++ içindeki yalnızca kendi kodum yalnızca bu işlevleri *Kullanıcı dışı kod*olarak değerlendirir:

- Sembol dosyasında, atılmış kaynak bilgisine sahip işlevler.
- Sembol dosyalarının, yığın çerçevesine karşılık gelen kaynak dosya olmadığını gösteren işlevler.
- *%VSInstallDirectory%\common7\packages\debugger\visualıcılar* klasöründeki * \* . natjmc* dosyalarında belirtilen işlevler.

Kod atlama davranışı için C++ içindeki Yalnızca kendi kodum yalnızca bu işlevleri *Kullanıcı olmayan kod*olarak değerlendirir:

- Karşılık gelen PDB dosyası hata ayıklayıcıda yüklenmemiş olan işlevleri.
- *%VSInstallDirectory%\common7\packages\debugger\visualıcılar* klasöründeki * \* . natjmc* dosyalarında belirtilen işlevler.

> [!NOTE]
> Yalnızca kendi kodum ' de kod Adımlama desteği için, C++ kodu Visual Studio 15,8 Preview 3 veya sonraki sürümlerde MSVC derleyicileri kullanılarak derlenmesi gerekir ve/JMC derleyici anahtarı etkinleştirilmelidir (varsayılan olarak etkindir). Daha fazla bilgi için bkz. [C++ çağrı yığınını ve kod atlama davranışını özelleştirme](#BKMK_CPP_Customize_call_stack_behavior)ve bu [blog gönderisi](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Eski bir derleyici kullanılarak derlenen kod için *. natstepfilter* dosyaları, yalnızca kendi kodum bağımsız olan kod adımlamayı özelleştirmenin tek yoludur. Bkz. [C++ atlama davranışını özelleştirme](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a>C++ hata ayıklaması sırasında:

- **Hata Ayıkla**  >  Kullanıcı kodunun sonraki satırına kod üzerinde Kullanıcı dışı kod adımlarında **adımla** (veya **F11**).
- **Hata Ayıkla**  >  Kullanıcı dışı kod üzerinde **Step Out** (veya **Shift** + **F11**), Kullanıcı kodu için bir sonraki satırda çalışır.

Daha fazla Kullanıcı kodu yoksa, hata ayıklama sona erene kadar devam eder, başka bir kesme noktasına veya bir hata oluşturur.

Hata ayıklayıcı Kullanıcı dışı kod (örneğin, **hata ayıklama**  >  **kesmeyi** kullanırsanız ve Kullanıcı olmayan kodda durakladıysanız), Adımlama Kullanıcı olmayan kodda devam eder.

Hata ayıklayıcı bir özel durum ile karşılaşırsanız, Kullanıcı veya Kullanıcı olmayan kodda olup olmayana özel durum üzerinde duraklar. **Özel durum ayarları** Iletişim kutusundaki **Kullanıcı tarafından işlenmeyen** seçenekler yok sayılır.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>C++ çağrı yığınını ve kod Adımlama davranışını özelleştirme

C++ projeleri için, **çağrı yığını** penceresinin * \* . natjmc* dosyalarında belirterek Kullanıcı dışı kod olarak davrandığı modülleri, kaynak dosyalarını ve işlevleri belirtebilirsiniz. Bu özelleştirme, en son derleyicisini kullanıyorsanız kod adımlaması için de geçerlidir (bkz. [C++ yalnızca kendi kodum](#BKMK_CPP_User_and_non_user_code)).

- Visual Studio makinesinin tüm kullanıcıları için Kullanıcı olmayan kodu belirtmek için, *. natjmc* dosyasını *%VSInstallDirectory%\common7\packages\debugger\visualıcılar* klasörüne ekleyin.
- Tek bir kullanıcı için Kullanıcı olmayan kodu belirtmek için, * \\ Visual Studio Sürüm \> \ Görselleştiriciler* klasörüne *. natjmc* dosyasını%UserProfile%\My Documents<ekleyin.

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
|`Name`|Gereklidir. Modülün veya modüllerin tam yolu. Windows joker karakterlerini `?` (sıfır veya bir karakter) ve `*` (sıfır veya daha fazla karakter) kullanabilirsiniz. Örneğin,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> hata ayıklayıcıya herhangi bir sürücüdeki *\3Rdparty\utillibs* içindeki tüm modülleri dış kod olarak değerlendirmesine söyler.|
|`Company`|İsteğe bağlı. Yürütülebilir dosyaya katıştırılmış modülü yayımlayan şirketin adı. Bu özniteliği modülleri ortadan kaldırmak için kullanabilirsiniz.|

 **Dosya öğesi öznitelikleri**

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gereklidir. Dış kod olarak kabul edilecek kaynak dosyanın veya dosyaların tam yolu. Windows joker karakterlerini `?` ve `*` yolunu belirtirken kullanabilirsiniz.|

 **İşlev öğesi öznitelikleri**

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gereklidir. Dış kod olarak davranıyilecekleri işlevin tam adı.|
|`Module`|İsteğe bağlı. İşlevi içeren modülün adı veya tam yolu. Aynı ada sahip işlevleri ayırt etmek için bu özniteliği kullanabilirsiniz.|
|`ExceptionImplementation`|Olarak ayarlandığında `true` , çağrı yığını bu işlev yerine özel durumu oluşturan işlevi görüntüler.|

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>C++ Adımlama davranışını Yalnızca kendi kodum ayarlarından bağımsız olarak özelleştirme

C++ projeleri ' nde, * \* . natstepfilter* dosyalarında Kullanıcı olmayan kod olarak listeleyerek adım adım işlemler yapabilirsiniz. * \* . Natstepfilter* dosyalarında listelenen işlevler yalnızca kendi kodum ayarlarına bağımlı değildir.

- Tüm yerel Visual Studio kullanıcıları için Kullanıcı olmayan kodu belirtmek için, *. natstepfilter* dosyasını *%VSInstallDirectory%\common7\packages\debugger\visualıcılar* klasörüne ekleyin.
- Tek bir kullanıcı için Kullanıcı olmayan kodu belirtmek için, * \\ Visual Studio Sürüm \> \ görselleştiriciler klasörü<%UserProfile%\My Documents dizinine* *. natstepfilter* dosyasını ekleyin.

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

|Öğe|Description|
|-------------|-----------------|
|`Function`|Gereklidir. Kullanıcı dışı işlevler olarak bir veya daha fazla işlevi belirtir.|
|`Name`|Gereklidir. Eşleştirilecek tam işlev adını belirten bir ECMA-262 biçimli normal ifade. Örneğin:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> içindeki tüm yöntemlerin `MyNS::MyClass` Kullanıcı dışı kod olarak kabul edileceğini hata ayıklayıcıya söyler. Eşleşme büyük/küçük harfe duyarlıdır.|
|`Module`|İsteğe bağlı. İşlevi içeren modülün tam yolunu belirten bir ECMA-262 biçimli normal ifade. Eşleşme büyük/küçük harfe duyarsızdır.|
|`Action`|Gereklidir. Şu büyük/küçük harfe duyarlı değerlerden biri:<br /><br /> `NoStepInto`-hata ayıklayıcıya işlevin üzerinde ilermasını söyler.<br /> `StepInto`-hata ayıklayıcıya eşleşen işlev için diğerini geçersiz kılarak işlevin içine gitmesini söyler `NoStepInto` .|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a>JavaScript Yalnızca kendi kodum

<a name="BKMK_JS_User_and_non_user_code"></a>JavaScript Yalnızca kendi kodum, kodu aşağıdaki sınıflandırmalardaki kategorilere ayırarak, yığın görüntüsünü Adımlama ve çağır ' a denetler:

|||
|-|-|
|**MyCode**|Sahip olduğunuz ve denetlediğiniz Kullanıcı kodu.|
|**LibraryCode**|Düzenli olarak kullandığınız kitaplıklardaki Kullanıcı olmayan kod ve uygulamanız doğru şekilde çalışır (örneğin, WinJS veya jQuery).|
|**UnrelatedCode**|Uygulamanızda sahip olmadığınız ve uygulamanızın doğru çalışması için dayanmayan Kullanıcı olmayan kod. Örneğin, reklamları görüntüleyen bir reklam SDK 'Sı UnrelatedCode olabilir. UWP projelerinde, uygulamanıza HTTP veya HTTPS URI 'sinden yüklenmiş tüm kodlar de Relatedcode olarak kabul edilir.|

JavaScript hata ayıklayıcısı kodu Kullanıcı veya Kullanıcı olmayan bu sırada sınıflandırır:

1. Varsayılan sınıflandırmalar.
   - Ana bilgisayar tarafından sunulan işleve bir dize geçirerek yürütülen betik `eval` **MyCode**' dır.
   - Oluşturucuya bir dize geçirerek yürütülen betik `Function` **librarycode**' dur.
   - Bir çerçeve başvurusunda, WinJS veya Azure SDK gibi betik, **Librarycode**' tır.
   - ,, Veya işlevlerine bir dize geçirerek yürütülen `setTimeout` betik `setImmediate` `setInterval` **UnrelatedCode**.

2. Dosyadaki *% VSInstallDirectory% \JavaScript\JustMyCode\mycode.default.wwa.js* tüm Visual Studio JavaScript projeleri için belirtilen sınıflandırmalar.

3. Geçerli projenin dosyasındaki *mycode.js* sınıflandırmalar.

Her sınıflandırma adımı önceki adımları geçersiz kılar.

Diğer tüm kodlar **MyCode**olarak sınıflandırılır.

Bir JavaScript projesinin kök klasörüne *mycode.js* adlı bir *. JSON* dosyası ekleyerek varsayılan sınıflandırmaları değiştirebilir ve belirli dosyaları ve URL 'leri Kullanıcı veya Kullanıcı dışı kod olarak sınıflandırabilirsiniz. Bkz. [JavaScript yalnızca kendi kodum özelleştirme](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a>JavaScript hata ayıklaması sırasında:

- Bir işlev kullanıcı olmayan bir kod ise, **hata ayıklama**  >  **adımı** (veya **F11**) **hata ayıklama**  >  **adımıyla** (veya **F10**) aynı şekilde davranır.
- Bir adım kullanıcı olmayan (**librarycode** veya **UnrelatedCode**) kodda başlıyorsa, yalnızca kendi kodum etkin olmadığında geçici olarak adımlayın. Kullanıcı koduna döndüğünüzde Yalnızca kendi kodum Adımlama yeniden etkinleştirilir.
- Bir Kullanıcı kodu adımı geçerli yürütme bağlamından ayrılmaya neden olduğunda, hata ayıklayıcı bir sonraki yürütülen kullanıcı kod satırından sona erer. Örneğin, **Librarycode** kodunda bir geri çağırma yürütülüyorsa, Kullanıcı kodu sonraki satırı yürütülene kadar hata ayıklayıcı devam eder.
- **Step Out** (veya **SHIFT** + **F11**), sonraki Kullanıcı kodu satırında durduruluyor.

Daha fazla Kullanıcı kodu yoksa, hata ayıklama sona erene kadar devam eder, başka bir kesme noktasına veya bir hata oluşturur.

Kodda ayarlanan kesme noktaları her zaman isabet ediyor, ancak kod sınıflandırıldı.

- `debugger` **Librarycode**içinde anahtar sözcük oluşursa, hata ayıklayıcı her zaman kesilir.
- `debugger`Anahtar sözcüğü **UnrelatedCode**içinde oluşursa, hata ayıklayıcı durmaz.

<a name="BKMK_JS_Exception_behavior"></a>**MyCode** veya **librarycode** kodunda işlenmeyen bir özel durum oluşursa, hata ayıklayıcı her zaman kesilir.

**UnrelatedCode**içinde işlenmeyen bir özel durum oluşursa ve **MyCode** veya **librarycode** çağrı yığınında olursa hata ayıklayıcı kesilir.

Özel durum için birinci şans özel durumları etkinleştirilmişse ve özel durum **librarycode** veya **UnrelatedCode**içinde oluşursa:

- Özel durum işlenirse, hata ayıklayıcı kesme yapmaz.
- Özel durum işlenmezse, hata ayıklayıcı kesilir.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>JavaScript Yalnızca kendi kodum özelleştirme

Tek bir JavaScript projesinde kullanıcı ve Kullanıcı olmayan kodu kategorilere ayırmak için, *mycode.js* adlı bir *. JSON* dosyasını projenin kök klasörüne ekleyebilirsiniz.

Bu dosyadaki belirtimler, Varsayılan sınıflandırmaları ve dosyadaki *mycode.default.wwa.js* geçersiz kılar. Dosyadaki *mycode.js* tüm anahtar değer çiftlerini listelemez. **MyCode**, **Kitaplıklar**ve **ilişkisiz** değerler boş diziler olabilir.

Dosyalar *üzerindeMycode.js* bu söz dizimini kullanır:

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
|**Dğer**|Ana bilgisayar tarafından sunulan işleve bir dize geçirerek yürütülen komut dosyası `eval` . Varsayılan olarak, eval betiği **MyCode**olarak sınıflandırılır.|
|**İşlev**|Oluşturucuya bir dize geçirerek yürütülen komut dosyası `Function` . Varsayılan olarak, Işlev betiği **Librarycode**olarak sınıflandırılır.|
|**ScriptBlock**|`setTimeout`, `setImmediate` , Veya işlevlerine bir dize geçirerek yürütülen komut dosyası `setInterval` . Varsayılan olarak, ScriptBlock betiği **UnrelatedCode**olarak sınıflandırılır.|

Değeri şu anahtar sözcüklerden birine değiştirebilirsiniz:

- `MyCode`betiği **MyCode**olarak sınıflandırır.
- `Library`betiği **Librarycode**olarak sınıflandırır.
- `Unrelated`betiği **UnrelatedCode**olarak sınıflandırır.

**MyCode, kitaplıklar ve Ilgisiz**

**MyCode**, **Kitaplıklar**ve **ilişkisiz** anahtar değer çiftleri bir sınıflandırmayla dahil etmek istediğiniz URL 'leri veya dosyaları belirtir:

|||
|-|-|
|**MyCode**|**MyCode**olarak sınıflandırılan bir URL veya dosya dizisi.|
|**Kitaplıklar**|**Librarycode**olarak sınıflandırılan bir URL veya dosya dizisi.|
|**İlgisiz**|**UnrelatedCode**olarak sınıflandırılan bir URL veya dosya dizisi.|

URL veya dosya dizesinde `*` sıfır veya daha fazla karakterle eşleşen bir veya daha fazla karakter olabilir. `*`, normal ifadeyle aynıdır `.*` .
