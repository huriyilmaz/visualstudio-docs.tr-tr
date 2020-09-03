---
title: Özel Yönerge İşlemcisi Dağıtma
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4762ad21f117bebe22ecfce1c846f15d154b1bf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536025"
---
# <a name="deploying-a-custom-directive-processor"></a>Özel Yönerge İşlemcisi Dağıtma

Herhangi bir bilgisayarda Visual Studio 'da özel bir yönerge işlemcisi kullanmak için, bu konuda açıklanan yöntemlerden birini kullanarak kaydetmeniz gerekir.

Diğer yöntemler şunlardır:

- [Visual Studio uzantıları](../extensibility/shipping-visual-studio-extensions.md). Bu, yönerge işlemcisini hem kendi bilgisayar hem de diğer bilgisayarlara yüklemek/kaldırmak için bir yol sağlar. Genellikle, diğer özellikleri aynı VSIX'te paketleyebilirsiniz.

- [VSPackage](../extensibility/internals/vspackages.md). Yönerge işlemcisinin yanı sıra diğer özellikleri de içeren bir VSPackage tanımlıyorsanız, yönerge işlemcisi kaydetmeye uygun bir yöntem yoktur.

- Bir kayıt defteri anahtarı ayarlayın. Bu yöntemde, yönerge işlemcisi için bir kayıt defteri girdisini ekleyin.

Bu yöntemlerden birini yalnızca, Visual Studio veya MSBuild 'de metin şablonunuzu dönüştürmek istiyorsanız kullanmanız gerekir. Kendi uygulamanızda özel bir ana bilgisayar kullanıyorsanız, her yönerge için yönerge işlemcisi bulmak özel ana bilgisayarınızın sorumluluğundadır.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>VSIX'te Yönerge İşlemcisini Dağıtma

Bir [Visual Studio uzantısına (VSIX)](../extensibility/starting-to-develop-visual-studio-extensions.md)özel bir yönerge işlemcisi ekleyebilirsiniz.

 Aşağıdaki iki öğenin .vsix dosyasında bulunduğundan emin olmanız gerekir:

- Özel yönerge işlemcisi sınıfını içeren derleme (.dll).

- Yönerge işlemcisini kaydeden .pkgdef dosyası. Dosyanın kök adı derleme ile aynı olmalıdır. Örneğin, dosyalarınız CDP.dll ve CDP.pkgdef olarak adlandırılabilir.

Bir .vsix dosyasının içeriğini denetlemek veya değiştirmek için, dosya adı uzantısını .zip olarak değiştirin ve açın. İçerikleri düzenledikten sonra, dosya adını .vsix olarak eski haline döndürün.

Bir .vsix dosyası oluşturmanın birkaç yolu vardır. Aşağıdaki yordam bir yöntemi açıklamaktadır.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Bir VSIX projesinde özel bir yönerge işlemcisi geliştirmek için

1. Yeni bir **VSIX proje** projesi oluşturun.

2. **Source. Extension. valtmanifest**içinde, içerik türünü ve desteklenen sürümleri ayarlayın.

    1. VSıX bildirim düzenleyicisinde, **varlıklar** sekmesinde **Yeni** ' yi seçin ve yeni öğenin özelliklerini ayarlayın:

         **Içerik türü**  =  **VSPackage**

         **Kaynak proje** = \<*the current project*>

    2. **Seçili sürümler** ' e tıklayın ve yönerge işlemcisinin kullanılabilir olmasını istediğiniz yükleme türlerini işaretleyin.

3. .pkgdef dosyası ekleyin ve özelliklerini VSIX'e dahil edecek şekilde ayarlayın.

    1. Bir metin dosyası oluşturun ve \<*assemblyName*> . pkgdef olarak adlandırın.

         \<*assemblyName*> genellikle projenin adı ile aynıdır.

    2. Çözüm Gezgini'nde seçin ve özelliklerini aşağıdaki gibi ayarlayın:

         **Derleme eylemi**  =  **İçerik**

         **Çıkış Dizinine Kopyala**  =  **Her zaman Kopyala**

         **VSIX**  =  'e Ekle **Doğru**

    3. VSIX'in adını ayarlayın ve kimliğin benzersiz olmasını sağlayın.

4. Aşağıdaki metni .pkgdef dosyasına ekleyin.

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     Aşağıdaki adları kendi adlarınızla değiştirin: `CustomDirectiveProcessorName` , `NamespaceName` , `ClassName` , `AssemblyName` .

5. Aşağıdaki başvuruları projeye ekleyin:

    - **Microsoft. VisualStudio. Textşablon oluşturma. \* . 0**

    - **Microsoft. VisualStudio. Textşablon. \* Interfaces. 0**

    - **Microsoft. VisualStudio. Textşablon. VSHost. \* . 0**

6. Projeye özel yönerge işlemcisi sınıfınızı ekleyin.

     Bu, veya uygulaması gereken bir genel sınıftır <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

#### <a name="to-install-the-custom-directive-processor"></a>Özel Yönerge İşlemcisini yüklemek için

1. Windows Gezgini 'nde, derleme dizinini (genellikle bin\Debug veya bin\Release) açın.

2. Yönerge işlemcisini başka bir bilgisayara yüklemek isterseniz .vsix dosyasını başka bir bilgisayara kopyalayın.

3. .vsix dosyasına çift tıklatın. Visual Studio Uzantı Yükleyicisi görüntülenir.

4. Visual Studio’yu yeniden başlatın. Artık, özel yönerge işlemcisine başvuran yönergeleri içeren metin şablonlarını çalıştırmak mümkün olacaktır. Her yönerge bu şekildedir:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Özel yönerge işlemcisini kaldırmak veya kalıcı olarak devre dışı bırakmak için

1. Visual Studio **araçları** menüsünde **Uzantı Yöneticisi**' ne tıklayın.

2. Yönerge işlemcisini içeren VSıX ' i seçin ve ardından **Kaldır** veya **devre dışı bırak**' a tıklayın.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>VSIX'te bir Yönerge İşlemcisine Sorun Giderme İşlemi Yapma
 Yönerge işlemcisi çalışmazsa şu öneriler yardımcı olabilir:

- Özel yönergede belirttiğiniz Işlemci adı, `CustomDirectiveProcessorName` . pkgdef dosyasında belirttiğiniz ile eşleşmelidir.

- `IsDirectiveSupported`Yönteminizin adı geçirildiğinde, uygulamanız döndürmelidir `true` `CustomDirective` .

- Uzantıyı uzantı Yöneticisi 'nde göremiyorsanız, ancak sistem bunu yüklemenize izin vermeyecektir, bu uzantıyı **%LocalAppData%\microsoft\visualstudio \\ \* 0 \ Extensions \\ **konumundan silin.

- .Vsix dosyasını açın ve içeriğini inceleyin. Açmak için, dosya adı uzantısını .zip olarak değiştirin. .dll, .pkgdef ve extension.vsixmanifest dosyalarını içerdiğini doğrulayın. .vsixmanifest uzantı dosyası SupportedProducts düğümü için uygun listeyi içermelidir ve buna ek olarak İçerik düğümü altında bir VsPackage düğümü içermelidir:

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>VSPackage'ta Yönerge İşlemcisini Dağıtma
 Yönerge işlemciniz GAC'ye yüklenecek VSPackage'ın parçasıysa sistemin sizin için .pkgdef dosyası oluşturmasını sağlayın.

 Paket sınıfınıza şu öznitelikleri yerleştirin:

```csharp
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
> Bu öznitelik, yönerge işlemcisi sınıfına değil, paket sınıfına yerleştirilir.

 .pkgdef dosyası projeyi oluşturduğunuzda oluşturulur. VSPackage'i yüklediğinizde, .pkgdef dosyası yönerge işlemcisini kaydeder.

 .pkgdef dosyasının, genellikle bin\Debug veya bin\Release olan yapı klasöründe göründüğünü doğrulayın. Görünmezse,. csproj dosyasını bir metin düzenleyicisinde açın ve şu düğümü kaldırın: `<GeneratePkgDefFile>false</GeneratePkgDefFile>` .

 Daha fazla bilgi için bkz. [VSPackages](../extensibility/internals/vspackages.md).

## <a name="setting-a-registry-key"></a>Bir Kayıt Defteri Anahtarını Ayarlama
 Bu, özel bir yönerge işlemcisi yükleme yöntemi en az tercih edilir. Yönerge işlemcisini etkinleştirmek veya devre dışı bırakmak için uygun bir yol sağlamaz; yönerge işlemcisinin başka kullanıcılara dağıtılması yöntemini de sağlamaz.

> [!CAUTION]
> Kayıt defterini yanlış düzenlemek sisteminize ciddi zararlar verebilir. Kayıt defterinde değişiklikler yapmadan önce, bilgisayarınızdaki tüm değerli verileri yedeklediğinizden emin olun.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Bir kayıt defteri anahtarı ayarlayarak bir yönerge işlemcisi kaydetmek için

1. `regedit` öğesini çalıştırın.

2. Regedit içinde şuraya gidin:

    **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ \* . 0 \ Texttemplating\directiveiþlemcileri**

    Visual Studio 'nun deneysel sürümüne yönerge işlemcisini yüklemek isterseniz "11,0" sonrasına "exp" ekleyin.

3. Yönerge işlemcisi sınıfıyla aynı ada sahip bir kayıt defteri anahtarı ekleyin.

   - Kayıt defteri ağacında, **Directiveişlemcilerle** düğümüne sağ tıklayın, **Yeni**' nin üzerine gelin ve ardından **anahtar**' a tıklayın.

4. Yeni düğümünde, Sınıf ve CodeBase veya Derleme için dize değerlerini aşağıdaki tablolara göre ekleyin.

   1. Oluşturduğunuz düğüme sağ tıklayın, **Yeni**' nin üzerine gelin ve **dize değeri**' ne tıklayın.

   2. Değerin adını düzenleyin.

   3. Adı çift tıklatın ve verileri düzenleyin.

   Özel yönerge işlemcisi GAC'de değilse, kayıt defteri alt anahtarları aşağıdaki tabloda gibi görünmelidir:

|Ad|Tür|Veriler|
|-|-|-|
|(Varsayılan)|REG_SZ|(değer ayarlı değil)|
|Sınıf|REG_SZ|**\<Namespace Name>.\<Class Name>**|
|CodeBase|REG_SZ|**\<Your Path>\\ Derleme adınızı<\>**|

 Derleme GAC'deyse, kayıt defteri alt anahtarları aşağıdaki tabloda gibi görünmelidir:

|Ad|Tür|Veriler|
|-|-|-|
|(Varsayılan)|REG_SZ|(değer ayarlı değil)|
|Sınıf|REG_SZ|\<**Your Fully Qualified Class Name**>|
|Bütünleştirilmiş Kod|REG_SZ|\<**Your Assembly Name in the GAC**>|

## <a name="see-also"></a>Ayrıca bkz.

- [Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md)
