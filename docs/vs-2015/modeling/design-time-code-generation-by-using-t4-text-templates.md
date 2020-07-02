---
title: T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
ms.assetid: 2774b83d-1adb-4c66-a607-746e019b80c0
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efdbf1b96e1dc49f5b9c48cebe6cededc9ea7c6e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534153"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tasarım zamanı T4 Metin şablonları, projenizde program kodu ve diğer dosyaları oluşturmanıza olanak tanır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Genellikle, şablonları bir *modelden*verilere göre oluşturdukları kodu değiştirecek şekilde yazarsınız. Model, uygulamanızın gereksinimleriyle ilgili anahtar bilgileri içeren bir dosya veya veritabanıdır.

 Örneğin, bir tablo veya diyagram olarak iş akışını tanımlayan bir modelinize sahip olabilirsiniz. Modelden, iş akışını yürüten yazılımı oluşturabilirsiniz. Kullanıcılarınızın gereksinimleri değiştiğinde, kullanıcılarla yeni iş akışını tartışmak kolaydır. Kodu iş akışından yeniden oluşturma işlemi, kodu el ile güncelleştirmeden daha güvenilirdir.

> [!NOTE]
> *Model* , bir uygulamanın belirli bir yönlerini açıklayan bir veri kaynağıdır. Herhangi bir dosya veya veritabanı türü gibi herhangi bir biçimde olabilir. UML model veya etki alanına özgü dil modeli gibi belirli bir biçimde olmak zorunda değildir. Tipik modeller tablo veya XML dosyaları biçiminde bulunur.

 Büyük olasılıkla kod üretimi hakkında zaten bilgi sahibisiniz. Çözümünüzde bir **. resx** dosyasında kaynak tanımladığınızda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir dizi sınıf ve yöntem otomatik olarak oluşturulur. Kaynak dosyası, sınıfları ve yöntemleri düzenlemeniz gerekdiğinizden, kaynakları düzenlemeyi çok daha kolay ve güvenilir hale getirir. Metin şablonlarıyla, kendi tasarımınızın bir kaynağından aynı şekilde kod oluşturabilirsiniz.

 Metin şablonu, oluşturmak istediğiniz metnin bir karışımını ve metnin değişken parçalarını oluşturan program kodunu içerir. Program kodu ve oluşturulan metnin parçalarını yinelemenize veya koşullu olarak atlamanızı sağlar. Oluşturulan metin, uygulamanızın bir kısmını oluşturacak program kodu olabilir.

## <a name="creating-a-design-time-t4-text-template"></a>Tasarım zamanı T4 metin şablonu oluşturma

#### <a name="to-create-a-design-time-t4-template-in-visual-studio"></a>Visual Studio 'da tasarım zamanı T4 şablonu oluşturmak için

1. Bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje oluşturun veya var olan bir projeyi açın.

     Örneğin, **Dosya** menüsünde, **Yeni**, **Proje**' yi seçin.

2. Projenize bir metin şablonu dosyası ekleyin ve **. tt**uzantısına sahip bir ad verin.

     Bunu yapmak için **Çözüm Gezgini**, projenizin kısayol menüsünde, **Ekle**, **Yeni öğe**' yi seçin. **Yeni öğe Ekle** iletişim kutusunda Orta bölmeden **metin şablonu** ' nu seçin.

     Dosyanın **özel araç** özelliğinin **TextTemplatingFileGenerator**olduğunu unutmayın.

3. Dosyayı açın. Zaten aşağıdaki yönergeleri içerir:

    ```
    <#@ template hostspecific="false" language="C#" #>
    <#@ output extension=".txt" #>
    ```

     Şablonu bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeye eklediyseniz, dil özniteliği " `VB` " olur.

4. Dosyanın sonuna bir metin ekleyin. Örneğin:

    ```
    Hello, world!
    ```

5. Dosyayı kaydedin.

     Şablonu çalıştırmak istediğinizi onaylamanızı isteyen bir **güvenlik uyarısı** ileti kutusu görebilirsiniz. **Tamam**'a tıklayın.

6. **Çözüm Gezgini**' de, şablon dosyası düğümünü genişletin ve **. txt**uzantılı bir dosya görürsünüz. Dosya şablondan oluşturulan metni içerir.

    > [!NOTE]
    > Projeniz bir Visual Basic projesi ise, çıkış dosyasını görmek için **tüm dosyaları göster** ' e tıklamanız gerekir.

### <a name="regenerating-the-code"></a>Kodu yeniden oluşturma
 Bir şablon, aşağıdaki durumlardan herhangi biri içinde, yan bir dosya oluşturarak yürütülür:

- Şablonu düzenleyin ve odağı farklı bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pencereye değiştirin.

- Şablonu kaydedin.

- **Build** menüsündeki **Tüm Şablonları Dönüştür** ' e tıklayın. Bu, Çözümdeki tüm şablonları dönüştürür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

- **Çözüm Gezgini**, herhangi bir dosyanın kısayol menüsünde **özel araç Çalıştır**' ı seçin. Şablonların seçili bir alt kümesini dönüştürmek için bu yöntemi kullanın.

  Ayrıca bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeyi, okudukları veri dosyaları değiştiğinde şablonların yürütülmesi için de ayarlayabilirsiniz. Daha fazla bilgi için bkz. [kodu otomatik olarak](#Regenerating)yeniden oluşturma.

## <a name="generating-variable-text"></a>Değişken metin üretiliyor
 Metin şablonları, oluşturulan dosyanın içeriğini değiştirmek için program kodunu kullanmanıza olanak sağlar.

#### <a name="to-generate-text-by-using-program-code"></a>Program kodunu kullanarak metin oluşturmak için

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

2. . Tt dosyasını kaydedin ve oluşturulan. txt dosyasını yeniden inceleyin. 0 ile 10 arasında sayıların karelerinin sayısını listeler.

   Deyimlerinin içinde ve tek ifadelerin içine alındığına dikkat edin `<#...#>` `<#=...#>` . Daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

   İçinde üretilen kodu yazarsanız [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , `template` yönergesinin içermesi gerekir `language="VB"` . `"C#"` varsayılan değerdir.

## <a name="debugging-a-design-time-t4-text-template"></a>Tasarım zamanı T4 metin şablonunda hata ayıklama
 Metin şablonunda hata ayıklamak için:

- `debug="true"` `template` Yönergeye ekleyin. Örneğin:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Şablondaki kesme noktalarını, sıradan kodunuzla aynı şekilde ayarlayın.

- Çözüm Gezgini metin şablonu dosyasının kısayol menüsünden **T4 şablonu hata ayıkla** ' yı seçin.

  Şablon, kesme noktalarında çalışır ve durdurulur. Değişkenleri inceleyebilir ve her zamanki şekilde kodda adım adım gezinebilirsiniz.

> [!TIP]
> `debug="true"`oluşturulan koda daha fazla satır numaralandırma yönergesi ekleyerek oluşturulan kod eşlemesini metin şablonuna daha doğru hale getirir. Ayrıldıysanız, kesme noktaları yanlış durumda çalışmayı durdurabilir.
>
> Ancak, hata ayıklama yapmadığınızda bile şablon yönergesinin yan tümcesini bırakabilirsiniz. Bu, yalnızca performansta çok küçük bir bırakma oluşmasına neden olur.

## <a name="generating-code-or-resources-for-your-solution"></a>Çözümünüz için kod veya kaynak üretme
 Bir modele bağlı olarak değişen program dosyaları oluşturabilirsiniz. Model, veritabanı, yapılandırma dosyası, UML modeli, DSL modeli veya diğer kaynak gibi bir giriştir. Genellikle aynı modelden birkaç program dosyası oluşturursunuz. Bunu başarmak için, oluşturulan her program dosyası için bir şablon dosyası oluşturun ve tüm şablonların aynı modeli okumasını sağlayabilirsiniz.

#### <a name="to-generate-program-code-or-resources"></a>Program kodu veya kaynakları oluşturmak için

1. Çıktı yönergesini,. cs,. vb,. resx veya. xml gibi uygun türde bir dosya oluşturacak şekilde değiştirin.

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

    ```
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Kod oluşturma ve oluşturulan metin
 Program kodu oluştururken, şablonunuzda yürütülen kod üreten kodu ve çözümünüzün bir parçası haline gelen oluşturulan kodu karıştırmaktan kaçınmak önemlidir. İki dilin aynı olması gerekmez.

 Önceki örnekte iki sürüm vardır. Tek sürümde, üretilen kod C# ' de bulunur. Diğer sürümde, üretilen kod Visual Basic. Ancak her ikisi tarafından oluşturulan metin aynıdır ve bu bir C# sınıfıdır.

 Aynı şekilde, [!INCLUDE[csprcs](../includes/csprcs-md.md)] herhangi bir dilde kod oluşturmak için bir şablon kullanabilirsiniz. Oluşturulan metnin belirli bir dilde olması gerekmez ve program kodu olması gerekmez.

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

 `assembly`Yönergesi, belirtilen derlemeyi bir projenin başvurular bölümüyle aynı şekilde şablon kodunuz için kullanılabilir hale getirir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Otomatik olarak başvurulan System.dll bir başvuru eklemeniz gerekmez. `import`Yönergesi, `using` normal bir program dosyasındaki yönergeyle aynı şekilde tam nitelikli adlarını kullanmadan türleri kullanmanıza olanak sağlar.

 Örneğin, **System.IO**içeri aktardıktan sonra şunu yazabilirsiniz:

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

### <a name="opening-a-file-with-a-relative-pathname"></a>Göreli yol adıyla dosya açma
 Bir dosyayı metin şablonuna göre bir konumdan yüklemek için kullanabilirsiniz `this.Host.ResolvePath()` . Bunu kullanmak için. Konak, ' de ayarlamanız gerekir `hostspecific="true"` `template` :

```
<#@ template debug="false" hostspecific="true" language="C#" #>

```

 Daha sonra yazabilirsiniz, örneğin:

```csharp
<# string fileName = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...

```

```vb
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>

```

 Ayrıca `this.Host.TemplateFile` , geçerli şablon dosyasının adını tanımlayan öğesini de kullanabilirsiniz.

 Türü `this.Host` (vb, `Me.Host` ) `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost` .

### <a name="getting-data-from-vsprvs"></a>Verileri alma[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]
 İçinde sunulan hizmetleri kullanmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , özniteliğini ayarlayın `hostSpecific` ve `EnvDTE` derlemeyi yükleyin. Daha sonra, DTE ve diğer hizmetlere erişmek için ıvıceprovider. GetCOMService () kullanabilirsiniz. Örneğin:

```scr
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>

```

> [!TIP]
> Bir metin şablonu kendi uygulama etki alanında çalışır ve hizmetlere sıralama tarafından erişilir. Bu durumda, GetCOMService (), GetService () öğesinden daha güvenilirdir.

## <a name="regenerating-the-code-automatically"></a><a name="Regenerating"></a>Kodu otomatik olarak yeniden oluşturma
 Genellikle, bir çözümde birkaç dosya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir giriş modeliyle oluşturulur. Her dosya kendi şablonundan oluşturulur, ancak şablonlar hepsi aynı modele başvurur.

 Kaynak modeli değişirse, Çözümdeki tüm şablonları yeniden çalıştırmalısınız. Bunu el ile yapmak için, **Yapı** menüsünde **Tüm Şablonları Dönüştür** ' ü seçin.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Görselleştirme ve modelleme SDK 'sını yüklediyseniz, her derleme gerçekleştirirken tüm şablonların otomatik olarak dönüştürülmesini sağlayabilirsiniz. Bunu yapmak için, proje dosyanızı (. csproj veya. vbproj) bir metin düzenleyicisinde düzenleyin ve diğer deyimlerden sonra dosyanın sonuna yakın olan aşağıdaki satırları ekleyin `<import>` :

```
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v11.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

 Daha fazla bilgi için bkz. [derleme sürecinde kod oluşturma](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Hata bildirimi
 Hata penceresinde hata ve uyarı iletilerini yerleştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aşağıdaki yöntemleri kullanabilirsiniz:

```
Error("An error message");
Warning("A warning message");
```

## <a name="converting-an-existing-file-to-a-template"></a><a name="Converting"></a>Var olan bir dosyayı şablona dönüştürme
 Şablonların yararlı bir özelliği, oluşturdukları dosyalara çok benzer bir şekilde, eklenen bazı program kodları ile birlikte görünmesidir. Bu, şablon oluşturma yararlı bir yöntemini önerir. Önce bir dosya gibi bir prototip olarak sıradan bir dosya oluşturun [!INCLUDE[csprcs](../includes/csprcs-md.md)] ve sonuç olarak ortaya çıkan dosyayı değişen nesil kod olarak tanıtın.

#### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Varolan bir dosyayı tasarım zamanı şablonuna dönüştürmek için

1. Projenize,, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya dosyası gibi oluşturmak istediğiniz türde bir dosya ekleyin `.cs` `.vb` `.resx` .

2. Çalıştığından emin olmak için yeni dosyayı test edin.

3. Çözüm Gezgini, dosya adı uzantısını **. tt**olarak değiştirin.

4. **. Tt** dosyasının aşağıdaki özelliklerini doğrulayın:

    |Özellik|Değer|
    |-|-|
    |**Özel araç =**|**TextTemplatingFileGenerator**|
    |**Derleme eylemi =**|**Yok**|

5. Dosyanın başına aşağıdaki satırları ekleyin:

    ```
    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    ```

     Şablonunuzun üretilen kodunu ' de yazmak isterseniz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , `language` özniteliğini yerine olarak ayarlayın `"VB"` `"C#"` .

     Oluşturmak istediğiniz `extension` dosya türü için özniteliği dosya adı uzantısına ayarlayın, örneğin, `.cs` `.resx` veya `.xml` .

6. Dosyayı kaydedin.

     Belirtilen uzantıya sahip bir yan kuruluş dosyası oluşturulur. Dosya türü için özellikleri doğrudur. Örneğin, bir. cs dosyasının **Build Action** özelliği **derlenir**.

     Oluşturulan dosyanın özgün dosyayla aynı içeriği içerdiğini doğrulayın.

7. Dosyanın değiştirmek istediğiniz bir bölümünü belirler. Örneğin, yalnızca belirli koşullar altında veya tekrarlanmış ya da belirli değerlerin değişebileceği bir bölüm görünür. Oluşturma kodu ekleyin. Dosyayı kaydedin ve bağlı olan dosyanın doğru bir şekilde oluşturulduğunu doğrulayın. Bu adımı yineleyin.

## <a name="guidelines-for-code-generation"></a>Kod oluşturma için yönergeler
 Lütfen [T4 Metin şablonları yazma yönergelerine](../modeling/guidelines-for-writing-t4-text-templates.md)bakın.

## <a name="next-steps"></a>Sonraki adımlar

|Sonraki adım|Konu başlığı|
|---------------|-----------|
|Yardımcı işlevler, dahil edilen dosyalar ve dış verileri kullanan kodla daha gelişmiş bir metin şablonunu yazma ve hata ayıklama.|[T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)|
|Çalışma zamanında şablonlardan belgeler oluşturun.|[T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Metin oluşturmayı dışarıda çalıştırın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|[TextTransform Yardımcı Programı ile Dosya Oluşturma](../modeling/generating-files-with-the-texttransform-utility.md)|
|Verilerinizi, etki alanına özgü dil biçiminde dönüştürün.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|
|Kendi veri kaynaklarınızı dönüştürmek için yönerge işlemcileri yazın.|[T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Ayrıca Bkz.
 [T4 Metin Şablonları Yazma Yönergeleri](../modeling/guidelines-for-writing-t4-text-templates.md)
