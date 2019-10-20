---
title: UML genişletmek için bir profil tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e621297b36d75a0e48baed4ab24d50abd5e61663
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668685"
---
# <a name="define-a-profile-to-extend-uml"></a>UML’yi genişletmek için profil tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standart model öğelerini belirli amaçlarla özelleştirmek için bir *UML profili* tanımlayabilirsiniz. Bir profil, bir veya daha fazla *UML stereotiplerini*tanımlar. Bir stereotip, belirli bir nesne türünü temsil eden bir türü işaretlemek için kullanılabilir. Bir stereotip Ayrıca bir öğenin özellik listesini genişletebilir.

 Çeşitli profiller, Visual Studio 'nun desteklenen sürümleriyle yüklenir. Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Bu profiller ve stereotiplerin nasıl uygulanacağı hakkında daha fazla bilgi için bkz. [modelinize profiller ve Stereotipler Ile özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 UML 'i kendi iş alanı veya mimarinize uyarlamak ve genişletmek için kendi profillerinizi tanımlayabilirsiniz. Örneğin:

- Web sitelerini sık sık tanımlarsanız, sınıf diyagramlarındaki sınıflara uygulanabilen bir «Web sayfası» stereotipi sağlayan kendi profilinizi tanımlayabilirsiniz. Daha sonra bir Web sitesi planlamak için sınıf diyagramlarını kullanabilirsiniz. Her «Web sayfası» sınıfı, sayfa içeriği, stili, vb. için ek özelliklere sahip olur.

- Bankacılık yazılımı geliştiriyorsanız, «Account» stereotipi sağlayan bir profil tanımlayabilirsiniz. Daha sonra farklı hesap türlerini tanımlamak ve aralarındaki ilişkileri göstermek için sınıf diyagramlarını kullanabilirsiniz.

  Kendi profillerinizi ekibinize dağıtabilirsiniz. Her ekip üyesi, profilinizi yükleyebilir. Bu, kendi stereotiplerini kullanan modelleri düzenlemenizi ve oluşturmasını sağlar.

> [!NOTE]
> Bir profilin stereotiplerini düzenlemekte olduğunuz bir modele uygularsanız ve sonra modeli diğer kişilerle paylaşıyorsanız, aynı profili kendi bilgisayarlarına yüklemelidir. Aksi takdirde, kullandığınız stereotiplerin görmeyecektir.

 Profil genellikle daha büyük bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısının bir parçasıdır. Örneğin, bir modelin bazı parçalarını koda çeviren bir komut tanımlayabilirsiniz. Kullanıcıların çevirmek istedikleri paketlere uygulanması gereken bir profil tanımlayabilirsiniz. Yeni komutlarınızı profille birlikte tek bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısında dağıtırsınız.

 Ayrıca, bir profilin yerelleştirilmiş türevlerini de tanımlayabilirsiniz. Uzantınızı yükleyen kullanıcılar kendi kültürüne uygun olan değişkeni görebilir.

## <a name="DefineProfile"></a>Profil tanımlama

#### <a name="to-define-a-uml-profile"></a>Bir UML profili tanımlamak için

1. @No__t_0 dosya adı uzantısına sahip yeni bir XML dosyası oluşturun.

2. [Bir profilin yapısında](#Schema)açıklanan yönergelere göre stereotip tanımları ekleyin.

3. Profili bir Visual Studio uzantısına (`.vsix` dosyasına) ekleyin. Profiliniz için yeni bir uzantı oluşturabilir ya da profili mevcut bir uzantıya ekleyebilirsiniz.

     [Bir Visual Studio uzantısına profil ekleme](#AddProfile)başlıklı sonraki bölüme bakın.

4. Uzantıyı bilgisayarınıza yükler.

    1. @No__t_0 dosya adı uzantısına sahip uzantı dosyasına çift tıklayın.

    2. Visual Studio'yu yeniden başlatın.

5. Profilin yüklü olduğunu doğrulayın.

    1. UML Explorer 'da modeli seçin.

    2. Özellikler penceresi **profiller** özelliğine tıklayın. Profiliniz menüde görünür. Profilin yanındaki onay işaretini ayarlayın.

    3. Profilinizin stereotipleri tanımladığı bir öğe seçin. Özellikler penceresi, **Stereotipler** özelliğine tıklayın. Stereotiplerinizin listede yer alacak. Onay işaretini stereotiplerin birine göre ayarlayın.

    4. Profiliniz bu stereotip için ek özellikler tanımlıyorsa, bunları görmek için stereotip özelliğini genişletin.

6. Uzantı dosyasını, bilgisayarlarına yüklemek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diğer kullanıcılarına gönderin.

## <a name="AddProfile"></a>Visual Studio uzantısına profil ekleme
 Bir profil yüklemek ve diğer kullanıcılara göndermenize izin vermek için, profili bir Visual Studio uzantısına eklemeniz gerekir. Daha fazla bilgi için bkz. [Visual Studio uzantılarını dağıtma](http://go.microsoft.com/fwlink/?LinkId=160780).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Yeni bir Visual Studio uzantısında bir profil tanımlamak için

1. Visual Studio uzantı projesi oluşturun.

   > [!NOTE]
   > Bu yordamı kullanmak için [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] yüklemiş olmanız gerekir.

   1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

   2. **Yeni proje** iletişim kutusunda, **yüklü şablonlar**altında, **görsel C#** ' i, **genişletilebilirlik**' i ve **VSIX projesi**' ne tıklayın. Proje adını ayarlayın ve **Tamam**' a tıklayın.

2. Profilinizi projeye ekleyin.

   - Çözüm Gezgini ' de projeye sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **var olan öğe**' ye tıklayın. İletişim kutusunda profil dosyanızı bulun.

3. Profil dosyasının, çıkış özelliğine **Kopyala** özelliğini ayarlayın.

   1. Çözüm Gezgini, profil dosyasına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

   2. Özellikler penceresi, **Çıkış Dizinine Kopyala** özelliğini **her zaman Kopyala**olarak ayarlayın.

4. Çözüm Gezgini ' de `source.extension.vsixmanifest` açın.

    Dosya uzantı bildirim düzenleyicisinde açılır.

5. **Varlıklar** sayfasında, profili açıklayan bir satır ekleyin:

   - **Yeni**'yi tıklatın. **Yeni varlık Ekle** iletişim kutusundaki alanları aşağıdaki gibi ayarlayın.

   - **Türü** `Microsoft.VisualStudio.UmlProfile` olarak ayarla

        Bu, açılan Seçimlerinizden biri değildir. Bu adı klavyeden girin.

   - **Dosya sisteminde dosya** ' ya tıklayın ve profil dosyanızın adını seçin, örneğin `MyProfile.profile`

6. Projeyi oluşturun.

7. **Profilde hata ayıklamak Için**F5 'e basın.

    Visual Studio 'nun deneysel bir örneği açılır. Bu örnekte, bir modelleme projesi açın. UML Gezgini ' nde, modelin kök öğesini seçin ve Özellikler penceresi profilinizi seçin. Sonra modelin içindeki öğeleri seçin ve kendileri için tanımladığınız stereotipleri ayarlayın.

8. **Dağıtım için VSıX 'i ayıklamak için**

   1. Windows Gezgini 'nde, **. vsix** dosyasını bulmak için, **\ \Bin\debug** veya. **\bin\Release** klasörünü açın. Bu bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısı dosyasıdır. Bu, bilgisayarınıza yüklenebilir ve diğer Visual Studio kullanıcılarına gönderilebilir.

   2. Uzantıyı yüklemek için:

       1. @No__t_0 dosyasına çift tıklayın. Visual Studio Uzantı Yükleyicisi başlatılır.

       2. Çalıştıran tüm Visual Studio örneklerini yeniden başlatın.

   @No__t_0 yüklemediyseniz, küçük uzantılar için aşağıdaki alternatif yordam kullanılabilir.

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Visual Studio SDK kullanmadan bir profil uzantısı tanımlamak için

1. Aşağıdaki üç dosyayı içeren bir Windows dizini oluşturun:

    - *Yourprofile* `.profile`

    - `extension.vsixmanifest`

    - `[Content_Types].xml`, bu adı köşeli ayraç ile burada gösterildiği gibi yazın

2. @No__t_0 aşağıdaki metni içerecek şekilde düzenleyin. Her dosya adı uzantısı için bir giriş içerdiğine dikkat edin.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="profile" ContentType="application/octet-stream" />
      <Default Extension="vsixmanifest" ContentType="text/xml" />
    </Types>
    ```

3. Mevcut bir `extension.vsixmanifest` kopyalayın ve bir XML Düzenleyicisi ile düzenleyin. KIMLIĞI, adı ve Içerik düğümlerini değiştirin.

    - Bu dizinde `extension.vsixmanifest` bir örnek bulabilirsiniz:

         *sürücü* **: \Program Files\Microsoft Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**

    - Içerik düğümü şöyle olmalıdır:

        ```
        <Content>
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"
          >YourProfile.Profile</CustomExtension>
        </Content>
        ```

4. Üç dosyayı daraltılmış bir dosyaya sıkıştırın.

     Windows Gezgini 'nde üç dosyayı seçin, sağ tıklayın, **Gönder**' in üzerine gelin ve ardından **Sıkıştırılmış (daraltılmış) klasör**' e tıklayın.

5. Daraltılmış dosyayı yeniden adlandırıp `.zip` dosya adı uzantısını `.vsix` olarak değiştirin.

6. Profili, Visual Studio 'nun uygun sürümleriyle herhangi bir bilgisayara yüklemek için `.vsix` dosyasına çift tıklayın.

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Bir Visual Studio uzantısı 'ndan bir UML profili yüklemek için

1. Windows Gezgini 'nde `.vsix` dosyasına çift tıklayın veya Visual Studio içinde açın.

2. Görüntülenen iletişim kutusunda, **yüklensin** ' e tıklayın.

3. Uzantıyı kaldırmak veya geçici olarak devre dışı bırakmak için, **Araçlar** menüsünden **Uzantılar ve güncelleştirmeler** ' i açın.

## <a name="Localized"></a>Yerelleştirilmiş profilleri tanımlama
 Farklı kültürler ve diller için farklı profiller tanımlayabilir ve bunların tümünü aynı uzantıya paketleyebilirsiniz. Bir Kullanıcı uzantınızı yüklediğinde, kültürü için tanımladığınız profili görürler.

 Her zaman bir varsayılan profil sağlamanız gerekir. Kullanıcının kültürü için bir profil tanımlamadıysanız, varsayılan profili görürler.

#### <a name="to-define-a-localized-profile"></a>Yerelleştirilmiş bir profil tanımlamak için

1. Önceki bölümlerde[bir profil tanımlama](#DefineProfile) ve [Visual Studio uzantısına profil ekleme](#AddProfile)konularında açıklandığı şekilde bir profil oluşturun. Bu varsayılan profildir ve yerelleştirilmiş bir profil sağlamayan herhangi bir yüklemede kullanılacaktır.

2. Varsayılan profil dosyanız ile aynı dizine yeni bir dizin ekleyin.

    > [!NOTE]
    > Uzantıyı bir Visual Studio uzantısı projesi kullanarak oluşturuyorsanız, projeye yeni bir klasör eklemek için Çözüm Gezgini kullanın.

3. Yeni dizinin adını, yerelleştirilmiş kültürün (Bulgarca için `bg` veya Fransızca için `fr`) ISO kısa kodu olarak değiştirin. @No__t_0 gibi belirli bir kültürün değil, genellikle iki harf olan bağımsız bir kültür kodu kullanmanız gerekir. Kültür kodları hakkında daha fazla bilgi için, kültür kodlarının tamamen bir listesini sağlayan [CultureInfo. Getkültürleri yöntemine](http://go.microsoft.com/fwlink/?LinkId=160782)bakın.

4. Varsayılan profilinizin bir kopyasını yeni dizine ekleyin. Dosya adını değiştirmeyin.

     Örnek bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısı klasörü, bir `.vsix` dosyasına oluşturulmadan veya sıkıştırılmadan önce, aşağıdaki klasörleri ve dosyaları içerir:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > Profillerin yerelleştirilmiş sürümlerine başvuru `extension.vsixmanifest` içine eklememelisiniz. Kopyalanan profil dosyaları üst klasördeki profille aynı ada sahip olmalıdır.

5. @No__t_0 öznitelikleri gibi, kullanıcıya görünür olacak tüm parçaları hedef dile çevirerek profilin yeni kopyasını düzenleyin.

6. İstediğiniz sayıda kültür için ek kültür klasörleri ve yerelleştirilmiş profiller oluşturabilirsiniz.

7. Uzantı projesini oluşturarak ya da önceki bölümlerde açıklandığı gibi tüm dosyaları sıkıştırarak Visual Studio uzantısı oluşturun.

## <a name="Schema"></a>Bir profilin yapısı
 UML profilleri için XSD dosyası aşağıdaki örnekte bulunabilir: [Stereotipler ve PROFILLER xsd olarak ayarlanıyor](http://go.microsoft.com/fwlink/?LinkID=213811). Profil dosyalarını düzenlemenize yardımcı olması için `.xsd` dosyasını içine yükleyebilirsiniz:

 **%ProgramFiles%\Microsoft Visual Studio [sürüm] \Xml\Schemas**

 Bu bölüm bir örnek C# olarak profili kullanır. Tüm profil tanımı şu şekilde görülebilir:

 *sürücü* **: \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\umlprofiles\csharp.exe**

 Bu yolun ilk kısımları yüklemenizde farklılık gösterebilir.

 .NET profili hakkında daha fazla bilgi için bkz. [UML modelleri Için standart stereotipler](../modeling/standard-stereotypes-for-uml-models.md).

### <a name="main-sections-of-the-uml-profile-definition"></a>UML profil tanımının ana bölümleri
 Her profil aşağıdaki içeriği içerir:

```
<?xml version="1.0" encoding="utf-8"?>
<profile dslVersion="1.0.0.0"
       name="CSharpProfile" displayName="C# Profile"
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">
  <stereotypes>...</stereotypes>
  <metaclasses>...</metaclasses>
  <propertyTypes>...</propertyTypes>
</profile>
```

> [!NOTE]
> @No__t_0 adlı öznitelik boşluk veya noktalama işareti içermemelidir. Kullanıcı arabiriminde görünen `displayName` özniteliği geçerli bir XML dizesi olmalıdır.

 Her profil üç ana bölüm içerir. Ters sırada bunlar aşağıdaki gibidir:

- `<propertyTypes>`-stereotipler bölümünde tanımlanan özellikler için kullanılan türlerin listesi.

- `<metaclasses>`-Bu profildeki stereotiplerin uygulandığı, IClass, IInterface, IOperation, IDependency gibi model öğe türlerinin listesi.

- `<stereotypes>`-stereotip tanımları. Her tanım, hedef model öğesine eklenen özelliklerin adlarını ve türlerini içerir.

#### <a name="property-types"></a>Özellik Türleri
 @No__t_0 bölümü, `<stereotypes>` bölümündeki özellikler için kullanılan türlerin bir listesini bildirir. İki tür özellik türü vardır: dış ve sabit listesi.

 Dış tür, standart bir .NET türünün tam nitelikli adını bildirir:

```
<externalType name="System.String" />
```

 Sabit listesi türü, sabit değerler kümesini tanımlar:

```
<enumerationType name="PackageVisibility">
  <enumerationLiterals>
    <enumerationLiteral name="internal" displayName="internal"  />
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />
  </enumerationLiterals>
</enumerationType>
```

#### <a name="metaclasses"></a>Metaclasses
 @No__t_0 bölümü, bu profildeki stereotiplerin tanımlanbileceği model öğesi türlerinin bir listesidir:

```
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />
```

 Meta sınıflar olarak kullanabileceğiniz model öğesi ve ilişki türlerinin tam listesi için bkz. [model öğe türleri](#Elements).

#### <a name="stereotype-definition"></a>Stereotip tanımı
 @No__t_0 bölümü bir veya daha fazla stereotip tanımı içerir:

```
<stereotype name="CSharpClass" displayName="C# Class"> ...
```

 Her stereotip, uygulanabilecek bir veya daha fazla model öğesi ya da ilişki türlerini listeler. Tüm türetilmiş türlerini dahil etmek için temel türün adına izin verebilirsiniz. Örneğin, `Microsoft.VisualStudio.Uml.Classes.IType` belirtirseniz, stereotip `IClass`, `IInterface`, `IEnumeration` ve diğer birçok öğe türü için uygulanabilir.

```
<metaclasses>
  <metaclassMoniker name=
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />
</metaclasses>
```

 @No__t_1 `name` özniteliği, `<metaClasses>` bölümündeki bir öğenin bağlantı öğesidir.

> [!NOTE]
> Bilinen ad adının `/yourProfileName/` ile başlaması gerekir, burada `yourProfileName` profilin `name` özniteliğinde tanımlanmıştır (Bu örnekteki "CSharpProfile"). Bilinen ad, Metaclasses bölümündeki girdilerden birinin adıyla biter.

 Her stereotip, uygulandığı herhangi bir model öğesine eklediği sıfır veya daha fazla özelliği listeleyebilir. @No__t_0, `<propertyTypes>` bölümünde tanımlanan türlerden birine bir bağlantı içerir. Bağlantı, bir `<enumerationType>` başvurmak için bir `<externalType>,` ya da bir `<enumerationTypeMoniker>` başvurmak üzere bir `<externalTypeMoniker>` olmalıdır. Yine, bağlantı profilinizin adıyla başlar.

```
  <properties>
    <property name="IsStatic"
            displayName="Is Static" defaultValue="false">
      <propertyType>
<externalTypeMoniker
               name="/CSharpProfile/System.Boolean" />
      </propertyType>
    </property>
    <property name="PackageVisibility"
              displayName="Package Visibility"
              defaultValue="internal">
      <propertyType>
        <enumerationTypeMoniker
              name="/CSharpProfile/PackageVisibility"/>
      </propertyType>
    </property>
  </properties>
</stereotype>
```

## <a name="Elements"></a>Model öğe türleri
 Stereotipleri tanımlayabilmeniz gereken türler kümesi [UML model öğe türlerinde](../modeling/uml-model-element-types.md)listelenmiştir.

## <a name="troubleshooting"></a>Sorun giderme
 Stereotiplerim UML modellerim görünmüyor.
Profilinizi bir paket veya modelde seçmeniz gerekir. Stereotipler daha sonra paket veya model içindeki öğelerde görüntülenir. Daha fazla bilgi için bkz. [UML model öğelerine stereotipler ekleme](../modeling/add-stereotypes-to-uml-model-elements.md).

 Bir UML modeli açtığımda şu hata görüntülenir: **VS1707: bir serileştirme hatası oluştuğundan aşağıdaki profiller yüklenemedi: MyProfile. Profile**
1. . Profile öğesinin temel XML sözdiziminin doğru olduğundan emin olun.

2. Her bir bilinen ad adının/profileName/nodeName. biçimde olduğundan emin olun ProfileName, kök profili düğümündeki ad özniteliğinin değeridir. Düğüme, bir Metaclass, externalType veya enumerationType ad özniteliğinin değeridir.

3. Sözdiziminin burada açıklandığı gibi olduğundan ve _sürücüde_gösterildiği gibi **: \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles \\** .

4. Hatalı uzantıyı kaldırın. **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın.

   - Uzantı görünmezse bir sonraki öğeye bakın.

5. VSıX dosyasını yeniden oluşturun ve yeniden yüklemek için Windows Gezgini 'nde açın. @No__t_0 yeniden başlatın.

   Uzantı, Uzantı Yöneticisi 'nde görünmez, ancak yeniden yüklemeye çalıştığınızda aşağıdaki ileti görüntülenir: **uzantı zaten tüm ilgili ürünlere yüklenmiş.**
   1. Uzantı dosyasını *LocalAppData*\microsoft\visualstudio \\ [Version] \ Extensions\ alt klasöründen Kaldır

   - *LocalAppData*görmek Için, Windows Gezgini klasör seçeneklerinin Görünüm sekmesinde gizli dosyaları ve klasörleri göster ' i ayarlamanız gerekir.

   - *LocalAppData* , genellikle C:\Users \\*UserName*\appdata\local\ konumunda

6. @No__t_0 yeniden başlatın.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML model öğelerine stereotipler ekleme](../modeling/add-stereotypes-to-uml-model-elements.md) [modelinizi, modellerinizi profiller ve Stereotipler](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [için standart stereotiplerle](../modeling/standard-stereotypes-for-uml-models.md) özelleştirin [örnek: stereotiplere göre renk UML ÖĞELERI](http://go.microsoft.com/fwlink/?LinkID=213841) örnek: [Stereotipler ayarlama, profiller xsd](http://go.microsoft.com/fwlink/?LinkID=213811)
