---
title: T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma
description: Tasarım zamanı T4 metin şablonlarının, Visual Studio projenizde program kodu ve diğer dosyalar oluşturmanıza nasıl olanak sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8b7bc48a5c409dbecbb313fd277a31ad1cec287
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389143"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma

Tasarım zamanı T4 Metin şablonları, Visual Studio projenizde program kodu ve diğer dosyaları oluşturmanıza olanak tanır. Genellikle, şablonları bir *modelden* verilere göre oluşturdukları kodu değiştirecek şekilde yazarsınız. Model, uygulamanızın gereksinimleriyle ilgili anahtar bilgileri içeren bir dosya veya veritabanıdır.

Örneğin, bir tablo veya diyagram olarak iş akışını tanımlayan bir modelinize sahip olabilirsiniz. Modelden, iş akışını yürüten yazılımı oluşturabilirsiniz. Kullanıcılarınızın gereksinimleri değiştiğinde, kullanıcılarla yeni iş akışını tartışmak kolaydır. Kodu iş akışından yeniden oluşturma işlemi, kodu el ile güncelleştirmeden daha güvenilirdir.

> [!NOTE]
> *Model* , bir uygulamanın belirli bir yönlerini açıklayan bir veri kaynağıdır. Herhangi bir dosya veya veritabanı türü gibi herhangi bir biçimde olabilir. UML model veya Domain-Specific dil modeli gibi belirli bir biçimde olması gerekmez. Tipik modeller tablo veya XML dosyaları biçiminde bulunur.

Büyük olasılıkla kod üretimi hakkında zaten bilgi sahibisiniz. Visual Studio çözümünüzdeki bir **. resx** dosyasında kaynak tanımladığınızda, bir dizi sınıf ve yöntem otomatik olarak oluşturulur. Kaynak dosyası, sınıfları ve yöntemleri düzenlemeniz gerekdiğinizden, kaynakları düzenlemeyi çok daha kolay ve güvenilir hale getirir. Metin şablonlarıyla, kendi tasarımınızın bir kaynağından aynı şekilde kod oluşturabilirsiniz.

Metin şablonu, oluşturmak istediğiniz metnin bir karışımını ve metnin değişken parçalarını oluşturan program kodunu içerir. Program kodu, oluşturulan metnin parçalarını yinelemenize veya koşullu olarak atlamanızı sağlar. Oluşturulan metin, uygulamanızın bir kısmını oluşturacak program kodu olabilir.

## <a name="create-a-design-time-t4-text-template"></a>Design-Time T4 metin şablonu oluşturma

1. Yeni bir Visual Studio projesi oluşturun veya var olan bir projeyi açın.

2. Projenize bir metin şablonu dosyası ekleyin ve **. tt** uzantısına sahip bir ad verin.

    Bunu yapmak için, **Çözüm Gezgini**, projenizin kısayol menüsünde   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda Orta bölmeden **metin şablonu** ' nu seçin.

    Dosyanın **özel araç** özelliğinin **TextTemplatingFileGenerator** olduğunu unutmayın.

3. Dosyayı açın. Zaten aşağıdaki yönergeleri içerir:

   ```
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   ```

    Şablonu bir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeye eklediyseniz, dil özniteliği " `VB` " olur.

4. Dosyanın sonuna bir metin ekleyin. Örneğin:

   ```
   Hello, world!
   ```

5. Dosyayı kaydedin.

    Şablonu çalıştırmak istediğinizi onaylamanızı isteyen bir **güvenlik uyarısı** ileti kutusu görebilirsiniz. **Tamam**'a tıklayın.

6. **Çözüm Gezgini**, şablon dosyası düğümünü genişletin ve uzantısı **.txt** olan bir dosya bulacaksınız. Dosya şablondan oluşturulan metni içerir.

   > [!NOTE]
   > Projeniz bir Visual Basic projesi ise, çıkış dosyasını görmek için **tüm dosyaları göster** ' e tıklamanız gerekir.

### <a name="regenerate-the-code"></a>Kodu yeniden üret

Bir şablon, aşağıdaki durumlardan herhangi biri içinde, yan bir dosya oluşturarak yürütülür:

- Şablonu düzenleyin ve odağı farklı bir Visual Studio penceresine değiştirin.

- Şablonu kaydedin.

- **Build** menüsündeki **Tüm Şablonları Dönüştür** ' e tıklayın. Bu işlem, Visual Studio çözümündeki tüm şablonları dönüştürür.

- **Çözüm Gezgini**, herhangi bir dosyanın kısayol menüsünde **özel araç Çalıştır**' ı seçin. Şablonların seçili bir alt kümesini dönüştürmek için bu yöntemi kullanın.

Ayrıca, okudukları veri dosyaları değiştiğinde şablonların yürütülmesi için bir Visual Studio projesi de ayarlayabilirsiniz. Daha fazla bilgi için bkz. [kodu otomatik olarak](#Regenerating)yeniden oluşturma.

## <a name="generate-variable-text"></a>Değişken metni oluştur

Metin şablonları, oluşturulan dosyanın içeriğini değiştirmek için program kodunu kullanmanıza olanak sağlar.

1. Dosyanın içeriğini değiştirin `.tt` :

   ```csharp
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   <#int top = 10;

   for (int i = 0; i<=top; i++)
   { #>
      The square of <#= i #> is <#= i*i #>
   <# } #>
   ```

   ```vb
   <#@ template hostspecific="false" language="VB" #>
   <#@ output extension=".txt" #>
   <#Dim top As Integer = 10

   For i As Integer = 0 To top
   #>
       The square of <#= i #> is <#= i*i #>
   <#
   Next
   #>
   ```

2. . Tt dosyasını kaydedin ve oluşturulan .txt dosyasını yeniden inceleyin. 0 ile 10 arasında sayıların karelerinin sayısını listeler.

   Deyimlerinin içinde ve tek ifadelerin içine alındığına dikkat edin `<#...#>` `<#=...#>` . Daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

   İçinde üretilen kodu yazarsanız [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , `template` yönergesinin içermesi gerekir `language="VB"` . `"C#"` varsayılan değerdir.

## <a name="debugging-a-design-time-t4-text-template"></a>Design-Time T4 metin şablonunda hata ayıklama

Metin şablonunda hata ayıklamak için:

- `debug="true"` `template` Yönergeye ekleyin. Örneğin:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Şablondaki kesme noktalarını, sıradan kodunuzla aynı şekilde ayarlayın.

- Çözüm Gezgini metin şablonu dosyasının kısayol menüsünden **T4 şablonu hata ayıkla** ' yı seçin.

   Şablon, kesme noktalarında çalışır ve duraklar. Değişkenleri inceleyebilir ve her zamanki şekilde kodda adım adım gezinebilirsiniz.

> [!TIP]
> `debug="true"` oluşturulan koda daha fazla satır numaralandırma yönergesi ekleyerek oluşturulan kod eşlemesini metin şablonuna daha doğru hale getirir. Ayrıldıysanız, kesme noktaları yanlış durumda çalışmayı durdurabilir.
>
> Ancak, hata ayıklama yapmadığınızda bile şablon yönergesinin yan tümcesini bırakabilirsiniz. Bu, yalnızca performansta çok küçük bir bırakma oluşmasına neden olur.

## <a name="generating-code-or-resources-for-your-solution"></a>Çözümünüz için kod veya kaynak üretme

Bir modele bağlı olarak değişen program dosyaları oluşturabilirsiniz. Model, veritabanı, yapılandırma dosyası, UML modeli, DSL modeli veya diğer kaynak gibi bir giriştir. Genellikle aynı modelden birkaç program dosyası oluşturursunuz. Bunu başarmak için, oluşturulan her program dosyası için bir şablon dosyası oluşturun ve tüm şablonların aynı modeli okumasını sağlayabilirsiniz.

### <a name="to-generate-program-code-or-resources"></a>Program kodu veya kaynakları oluşturmak için

1. Çıktı yönergesini,. cs,. vb,. resx veya .xml gibi uygun türde bir dosya oluşturacak şekilde değiştirin.

2. İhtiyaç duyduğunuz çözüm kodunu oluşturacak kodu ekleyin. Örneğin, bir sınıfta üç tamsayı alan bildirimi oluşturmak istiyorsanız:

    ```csharp

    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3. Dosyayı kaydedin ve şimdi aşağıdaki kodu içeren oluşturulan dosyayı inceleyin:

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Kod oluşturma ve oluşturulan metin

Program kodu oluştururken, şablonunuzda yürütülen kod üreten kodu ve çözümünüzün bir parçası haline gelen oluşturulan kodu karıştırmaktan kaçınmak önemlidir. İki dilin aynı olması gerekmez.

Önceki örnekte iki sürüm vardır. Tek sürümde, üretilen kod C# ' de bulunur. Diğer sürümde, üretilen kod Visual Basic. Ancak her ikisi tarafından oluşturulan metin aynıdır ve bu bir C# sınıfıdır.

Aynı şekilde, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] herhangi bir dilde kod oluşturmak için bir şablon kullanabilirsiniz. Oluşturulan metnin belirli bir dilde olması gerekmez ve program kodu olması gerekmez.

### <a name="structuring-text-templates"></a>Metin şablonlarını yapılandırma

İyi bir yöntem olarak, şablon kodunu iki kısma ayıracağız:

- Değişkenlerde değerleri ayarlayan ancak metin blokları içermeyen bir yapılandırma veya veri toplama bölümü. Önceki örnekte, bu bölüm öğesinin başlatımı olur `properties` .

   Bu bazen "model" bölümü olarak adlandırılır, çünkü bir mağaza modeli oluşturur ve genellikle bir model dosyası okur.

- Değişkenlerin değerlerini kullanan metin oluşturma bölümü ( `foreach(...){...}` örnekteki).

   Bu gerekli bir ayrım değildir, ancak metin içeren parçanın karmaşıklığını azaltarak şablonu okumayı daha kolay hale getiren bir stildir.

## <a name="reading-files-or-other-sources"></a>Dosyaları veya diğer kaynakları okuma

Bir model dosyasına veya veritabanına erişmek için, şablon kodunuz System.XML gibi derlemeler kullanabilir. Bu derlemelere erişim kazanmak için aşağıdaki gibi yönergeler eklemeniz gerekir:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

`assembly`Yönergesi, belirtilen derlemeyi, Visual Studio projesinin başvurular bölümüyle aynı şekilde şablon kodunuz için kullanılabilir hale getirir. Otomatik olarak başvurulan System.dll bir başvuru eklemeniz gerekmez. yönergesi, türleri tam adlarını kullanmadan normal bir program dosyasındaki yönergeyle aynı `import` `using` şekilde kullanmana olanak sağlar.

Örneğin, bir System.IO içeri **aktardıktan** sonra şunları yazabilir:

```csharp

<# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>
```

### <a name="opening-a-file-with-a-relative-pathname"></a>Göreli yol adı ile dosya açma

Metin şablonuna göre bir konumdan dosya yüklemek için `this.Host.ResolvePath()` kullanabilirsiniz. Bunu kullanmak için. Ana bilgisayar, içinde `hostspecific="true"` ayarlay `template` gerekir:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
```

Daha sonra yazabilir, örneğin:

```csharp
<# string filename = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...
```

```vb
<# Dim filename = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>
```

Geçerli şablon dosyasının `this.Host.TemplateFile` adını tanımlayan 'i de kullanabilirsiniz.

türü `this.Host` (VB, `Me.Host` içinde ) 'dır. `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`

### <a name="getting-data-from-visual-studio"></a>Veri kaynağından Visual Studio

Hizmetlerde sağlanan hizmetleri Visual Studio için `hostSpecific` özniteliğini ayarlayın ve derlemeyi `EnvDTE` yükleme. uzantı `Microsoft.VisualStudio.TextTemplating` yöntemini içeren `GetCOMService()` 'i içeri aktarın.  Daha sonra DTE'ye ve diğer hizmetlere erişmek için IServiceProvider.GetCOMService() kullanabilirsiniz. Örneğin:

```src
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

> [!TIP]
> Metin şablonu kendi uygulama etki alanında çalışır ve hizmetlere sıralama ile erişilir. Bu durumda GetCOMService() işlevi GetService() işlevinden daha güvenilirdir.

## <a name="regenerating-the-code-automatically"></a><a name="Regenerating"></a> Kodu otomatik olarak yeniden oluşturma

Genellikle, bir çözümde Visual Studio dosya tek bir giriş modeliyle oluşturulur. Her dosya kendi şablonundan oluşturulur, ancak şablonların hepsi aynı modele başvurur.

Kaynak model değişirse çözümde tüm şablonları yeniden çalıştırmanız gerekir. Bunu el ile yapmak için Derleme **menüsünde Tüm Şablonları** Dönüştür'e tıklayın. 

Visual Studio Modelleme SDK'sı'sini yüklemiş olursanız, derlemeyi her gerçekleştirin ve tüm şablonları otomatik olarak dönüştürebilirsiniz. Bunu yapmak için proje dosyanızı (.csproj veya .vbproj) bir metin düzenleyicisinde düzenleyin ve dosyanın sonuna, diğer deyimlerden sonra aşağıdaki `<import>` satırları ekleyin:

> [!NOTE]
> Metin Şablonu Dönüştürme SDK'sı ve Visual Studio Modelleme SDK'sı, uygulamanın belirli özelliklerini Visual Studio. Diğer ayrıntılar için bu [blog gönderisi'ne bakın.](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

Daha fazla bilgi için [bkz. Derleme İşlemsinde Kod Oluşturma.](../modeling/code-generation-in-a-build-process.md)

## <a name="error-reporting"></a>Hata raporlama

Hata iletilerini hata penceresine Visual Studio için şu yöntemleri kullanabilirsiniz:

```
Error("An error message");
Warning("A warning message");
```

## <a name="converting-an-existing-file-to-a-template"></a><a name="Converting"></a> Var olan bir dosyayı şablona dönüştürme

Şablonların yararlı bir özelliği, eklenen program koduyla birlikte, bu şablonların kendi oluşturan dosyalara çok benzli olarak bakmalarıdır. Bu, şablon oluşturmak için kullanışlı bir yöntem önerir. İlk olarak prototip olarak dosya gibi sıradan bir dosya oluşturun ve ardından sonuçta elde edilen dosyayı farklı olan [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oluşturma kodunu kademeli olarak tanıtin.

### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Var olan bir dosyayı tasarım zamanı şablonuna dönüştürmek için

1. Yeni Visual Studio, oluşturmak istediğiniz türde bir dosya (örneğin, , veya `.cs` `.vb` dosyası) `.resx` ekleyin.

2. Yeni dosyayı test etmek ve çalışır olduğundan emin olun.

3. Dosya Çözüm Gezgini uzantısını **.tt olarak değiştirebilirsiniz.**

4. **.tt** dosyasının aşağıdaki özelliklerini doğrulayın:

   |Özellik |Ayar |
   |-|-|
   | **Özel Araç =** | **Texttemplatingfilegenerator** |
   | **Derleme Eylemi =** | **Hiçbiri** |

5. Dosyanın başına aşağıdaki satırları ekler:

   ```
   <#@ template debug="false" hostspecific="false" language="C#" #>
   <#@ output extension=".cs" #>
   ```

    şablonu oluşturma kodunu içinde yazmak için [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] özniteliğini yerine `language` `"VB"` olarak `"C#"` ayarlayın.

    özniteliğini, oluşturmak istediğiniz dosya türü için dosya adı uzantısı olarak `extension` ayarlayın; `.cs` örneğin, `.resx` , veya `.xml` .

6. Dosyayı kaydedin.

    Belirtilen uzantıya sahip bir yan kuruluş dosyası oluşturulur. Özellikleri dosya türü için doğrudur. Örneğin, **bir** .cs dosyasının Derleme Eylemi özelliği Compile **olur.**

    Oluşturulan dosyanın özgün dosyayla aynı içeriği içerdiğini doğrulayın.

7. Dosyanın değişiklik yapmak istediğiniz bir bölümünü tanımlama. Örneğin, yalnızca belirli koşullar altında görünen bir bölüm ya da tekrarlanan veya belirli değerlerin farklılık göster olduğu bir bölüm. Oluşturma kodu ekleme. Dosyayı kaydedin ve yan kuruluş dosyasının doğru şekilde üretilmiş olduğunu doğrulayın. Bu adımı yinele.

## <a name="guidelines-for-code-generation"></a>Kod Oluşturma Yönergeleri

Lütfen [bkz. T4 Metin Şablonları Yazma Yönergeleri.](../modeling/guidelines-for-writing-t4-text-templates.md)

## <a name="next-steps"></a>Sonraki adımlar

|Sonraki adım|Konu|
|-|-|
|Yardımcı işlevleri, dahil edilen dosyaları ve dış verileri kullanan kodla daha gelişmiş bir metin şablonu yazma ve hata ayıklama.|[T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)|
|Çalışma zamanında şablonlardan belgeler oluşturun.|[T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Metin oluşturmayı çalışma Visual Studio.|[TextTransform Yardımcı Programı ile Dosya Oluşturma](../modeling/generating-files-with-the-texttransform-utility.md)|
|Verilerinizi etki alanına özgü bir dil şeklinde dönüştürebilirsiniz.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|
|Kendi veri kaynaklarınızı dönüştürmek için yönerge işlemcileri yazın.|[T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [T4 Metin Şablonları Yazma Yönergeleri](../modeling/guidelines-for-writing-t4-text-templates.md)
