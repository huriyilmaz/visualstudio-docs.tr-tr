---
title: UML Sınıf Diyagramlarından Kod Oluştur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75120b2f09c2eba3254a1b94e78875d8130c5225
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666129"
---
# <a name="generate-code-from-uml-class-diagrams"></a>UML sınıf diyagramları aracılığıyla kod oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da UML Sınıf Diyagramlarından Visual C# .NET kodu oluşturmak için **kod üret** komutunu kullanın. Varsayılan olarak, komut seçtiğiniz her UML türü için bir C# türü oluşturur. Kod oluşturan metin şablonlarını değiştirerek veya kopyalayarak bu davranışı değiştirebilir ve genişletebilirsiniz. Modelinizdeki farklı paketlerde bulunan türler için farklı davranış belirtebilirsiniz.

 **Kod oluştur** komutu özellikle kullanıcının öğe seçiminden kod oluşturmaya ve her UML sınıfı ya da başka bir öğe için bir dosya oluşturmaya uygundur. Örneğin, ekran görüntüsü iki UML sınıfından oluşturulmuş iki C# dosyası gösterir.

 Alternatif olarak, oluşturulan dosyaların UML öğeleriyle 1:1 ilişkisi olmadığı bir kod oluşturmak istiyorsanız, **Tüm Şablonları Dönüştür** komutuyla çağrılan metin şablonları yazmayı düşünebilirsiniz. Bu yöntem hakkında daha fazla bilgi için bkz. [UML modelden dosya oluşturma](../modeling/generate-files-from-a-uml-model.md).

 ![UML sınıf diyagramı ve oluşturulan C&#35; sınıf dosyaları.](../modeling/media/oob-gencode1.png "oob_GenCode1")

 Visual Studio 'da UML sınıf diyagramları hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)

- [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)

  Visual Studio 'nun hangi sürümlerini UML sınıf diyagramlarını desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="using-the-generate-code-command"></a>Kod Oluştur Komutunu Kullanma
 Aşağıdaki yordamda **kod oluştur** komutunun varsayılan davranışı açıklanmıştır:

#### <a name="to-generate-a-separate-file-for-each-element"></a>Her öğe için ayrı bir dosya oluşturmak üzere

1. Sınıflar içeren bir UML modeli oluşturun. Model öğelerine stereotipler uygulayabilirsiniz.

    Daha fazla bilgi için bkz. [varsayılan kod oluşturma dönüşümleri](#default).

2. Bir sınıf diyagramında veya **UML Model Gezgini**' nde, kod oluşturmak istediğiniz öğeleri seçin. Aşağıdakilerden birini seçebilirsiniz:

   - Belirli bir öğe kümesi.

   - İçeriğinden kod oluşturmak için bir paket veya model.

   - Diyagramdaki tüm öğeleri seçmek için diyagram.

3. Seçili bir öğe için kısayol menüsünü açın ve **kod oluştur**' u seçin.

    Belirli bir modelde **kod oluştur** ' u ilk kez kullandığınızda bir iletişim kutusu görüntülenir. Bu iletişim kutusu, modelin kod oluşturma parametrelerini düzenlemenizi sağlar.

    Bu parametreleri değiştirmek istediğinizi bilmiyorsanız **Tamam ' ı** seçin.

    Bu iletişim kutusuna daha sonra dönmek için **UML Model Gezgini**' ni açın. Modelleme projesi kısayol menüsünü açın ve ardından **kod oluşturmayı ayarla**' yı seçin. Daha fazla bilgi için bkz. [kod Oluştur komutunu özelleştirme](#custom).

   C# kodu içeren dosyalar oluşturulur. Varsayılan durumda, her tür için bir dosya oluşturulur ve dosyalar bir C# sınıf kitaplığı projesinde oluşturulur. Ancak, bu davranışı özelleştirebilirsiniz. Daha fazla bilgi için bkz. [kod Oluştur komutunu özelleştirme](#custom).

   Bazı doğrulama testleri, C#'ye çevrilebilmesini sağlamak için modele uygulanır. Bu testler başarısız olursa, bir hata iletisi görüntülenir ve kod oluşturma gerçekleştirilemez. Doğrulama menü komutu oluşturduysanız, doğrulama komutunuzun başarısız olduğu herhangi bir öğe için kod oluşturulmaz. Daha fazla bilgi için bkz. [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="default-code-generation-transforms"></a><a name="default"></a> Varsayılan kod oluşturma dönüşümleri
 Bu bölüm, komutu özelleştirmediğiniz takdirde **kod oluştur** komutu tarafından üretilen sonuçları özetler. Daha fazla bilgi için bkz. [kod Oluştur komutunu özelleştirme](#custom).

- UML modelinde seçtiğiniz her tür için bir C# türü oluşturulur. Her tür, **GeneratedCode** klasörünün altında ayrı bir kod dosyasına yerleştirilir.

- UML türü bir paket içinde yer alıyorsa, oluşturulan C# türü bir ad alanı içine yerleştirilir ve dosya ad alanıyla aynı ada sahip bir klasörde oluşturulur.

- Bir UML sınıfının her biri için bir C# özelliği oluşturulur `Attribute` .

- Bir UML türü için C# yöntemi oluşturulur `Operation` .

- Sınıfın katıldığı her gezilebilir ilişkilendirme için bir C# alanı oluşturulur.

  Her UML türüne bir stereotip ekleyerek, oluşturulan C# türünün daha fazla özelliğini denetleyebilirsiniz.

|**Bu C# türünü oluşturmak için**|**Bu UML türünü çiz**|**Bu stereotipi Uygula**|
|---------------------------------|----------------------------|-------------------------------|
|Sınıf|Sınıf|\<none> veya<br /><br /> C# sınıfı|
|Arabirim|Arabirim|\<none> veya<br /><br /> C# arabirimi|
|Sabit Listesi|Sabit Listesi|\<none> veya<br /><br /> C# sabit listesi|
|Temsilci|Sınıf|C# temsilcisi|
|Yapı|Sınıf|C# yapısı|

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Bir türde veya başka bir öğede bir stereotip ayarlamak için

1. Diyagramda veya **UML Model Gezgini**' nde öğe için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. **Özellikler** penceresinde, **Stereotipler** özelliğindeki açılan oku seçin ve ardından uygulamak istediğiniz stereotipin onay kutusunu seçin.

   > [!TIP]
   > C# stereotipleri görünmezse, ilgilendiğiniz model öğelerini içeren model veya paket için C# Profilini etkinleştirin. **UML Model Gezgini**'nde modelin paketini veya kökünü seçin. Ardından **Özellikler** penceresinde **profil**' i seçin ve ardından C# profilini etkinleştirin.

3. Ayarlayabileceğiniz ek özellikleri görmek için **Stereotipler** özelliğini genişletin.

   Türlerin, özniteliklerin, işlemlerin ve ilişkilerin **Açıklama** özellikleri, `<summary>` oluşturulan koddaki açıklamalara yazılır. Türlere bağlı açıklama öğeleri `<remarks>` açıklamalara yazılır.

## <a name="varying-the-generated-code"></a>Oluşturulan kodu değiştirme
 Oluşturulan kod her türün, özniteliğin veya işlemin özelliklerine göre değişir. Örneğin, bir sınıfın **abstract** özelliğini true olarak ayarlarsanız `abstract` anahtar sözcüğü oluşturulan sınıfta görüntülenir. Bir özniteliğin **çokluğunu** **0. \* .** olarak ayarlarsanız, oluşturulan özelliğin `IEnumerable<>` türü olur.

 Ayrıca, her stereotip ayarlayabileceğiniz çeşitli ek özellikler sağlar. Bu değerler için C# kodunda uygun anahtar sözcüklere çevrilir. Örneğin, özelliğini `Is Static` bir sınıf üzerinde ayarlarsanız, C# sınıfı olur `static` .

 Bu ek özellikleri ayarlamak için diyagramda sınıfı veya diğer öğeyi seçin. Özellikler penceresi, **Stereotipler**' ı genişletin ve ardından C# **sınıfı**gibi c# stereotipini genişletin.  Sınıflar için bu ek özellikler şunlardır:

- CLR Öznitelikleri

- Is Partial

- Is Static

- Is Unsafe

- Paket Görünürlüğü

  Her öznitelik ve işlemde ayarlayabileceğiniz stereotip özellikleri de vardır. Yeni bir öznitelik üzerinde Özellikler görmüyorsanız, **kod üret**' i çalıştırın.

## <a name="customizing-the-generate-code-command"></a><a name="custom"></a> Kod Oluştur komutunu özelleştirme
 **Kod oluştur** komutu, model öğelerinizi bir metin şablonları kümesi kullanarak dönüştürerek işe yarar. Metin şablonları hakkında daha fazla bilgi için bkz. [kod oluşturma ve T4 Metin şablonları](../modeling/code-generation-and-t4-text-templates.md).

 Şablonlar bir *metin şablonu bağlamaları*kümesinde belirtilir. Bir metin şablonu bağlaması hangi şablonun uygulanacağını, oluşturulan çıktının nereye yerleştirileceğini ve **kod oluştur** komutunun diğer parametrelerini belirtir.

 Belirli bir modelde **kod üret** komutunu ilk kez çalıştırdığınızda, modelin köküne varsayılan bir şablon bağlamaları kümesi ekler. Bu bağlamalar, modeldeki tüm öğelere uygulanır.

 Ancak, kendi bağlamalarınızı paketlere, sınıflara veya diğer öğelere ekleyerek bu varsayılan bağlamaları geçersiz kılabilir ve bunlara ekleme yapabilirsiniz. Bağlama, bağlı olduğu öğe içinde bulunan tüm öğelere uygulanır. Örneğin, belirli bir paket içindeki tüm türlerin farklı şablonlar kümesi tarafından dönüştürülmesini veya farklı bir klasöre çıkarılmasını istiyorsanız, pakete şablon bağlamaları ekleyebilirsiniz.

 Bir model öğesine iliştirilmiş şablon bağlamalarını denetlemek için Özellikler penceresi **metin şablonu bağlamaları** özelliğindeki üç nokta **[...]** simgesini seçin.

 **Kod oluştur** komutu, seçtiğiniz her model öğesine şablonları uygular. Her öğe için uygulanan şablonlar kümesi, modelin kökü de dahil olmak üzere kapsayıcılarına eklenen birleştirilmiş şablon kümesidir.

 Bu kümedeki iki şablon bağlaması aynı ada sahipse, daha küçük kapsayıcıdaki bağlama daha büyük kapsayıcıdaki bağlamayı geçersiz kılar. Örneğin, model kökünün ad **sınıf şablonuyla**bir bağlaması vardır. Kendi şablonunuzun belirli bir paketin içeriğine uygulanmasını sağlamak için, ad **sınıfı şablonuna**sahip kendi şablon bağlamalarınızı tanımlayın.

 Model öğesine birden fazla şablon uygulanabilir. Her model öğesinden birden fazla dosya oluşturabilirsiniz.

> [!NOTE]
> Modelin köküne eklenen bağlamalar, modeldeki tüm öğeler için varsayılanlar olarak görev görür. Bu varsayılan bağlamaları görmek için **UML Model Gezgini**' ni açın. Modelleme projesinin kısayol menüsünü açın ve **kod oluşturmayı ayarla**' yı seçin. Alternatif olarak, UML Model Gezgini ' nde modelin kökünü seçebilirsiniz. Özellikler penceresi **metin şablonu bağlamaları** özelliğinde **[...]** seçeneğini belirleyin. **Kod üret** komutunu en az bir kez kullanana kadar bağlamalar görünmez. Şablon bağlamaları bir diyagrama eklenemez.

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Metin şablon bağlamalarını bir pakete veya başka bir model öğesine eklemek için

1. **UML Model Gezgini**' nde bir model öğesi için kısayol menüsünü açın ve ardından **Özellikler**' i seçin. Genellikle, metin şablon bağlamalarını bir pakete veya modelin köküne eklersiniz.

2. **Özellikler** penceresinde, **metin şablonu bağlamaları** özelliğindeki üç nokta düğmesini (**[...]**) seçin.

    **Metin şablonu bağlamaları** iletişim kutusu görüntülenir.

3. Yeni bir metin şablonu bağlaması oluşturmak için **Ekle** ' yi seçin.

    \- veya

    Düzenlemek için varolan bir bağlamayı seçin.

    Her şablon bağlaması, belirtilen bir şablonun seçtiğiniz model öğesine ve içerdiği diğer model öğelerine nasıl uygulanması gerektiğini tanımlar.

4. İletişim kutusunda, metin şablon bağlamasının özelliklerini ayarlayın.

   |    **Özellik**    |                                                                                                                                                                                                                                                                                                                    **Açıklama**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Name        |                                                                                                                                                                                                                                                  Bu bağlama için bir ad. Kapsayan bir paketten veya modelden devralınan bir bağlamayı geçersiz kılmak için geçersiz kılmak istediğiniz bağlamayla aynı adı kullanın.                                                                                                                                                                                                                                                  |
   |     Üzerine yaz      |                                                                                                                                                                                                                                                                                                      True ise, varolan tüm kodların üzerine yazılır.                                                                                                                                                                                                                                                                                                       |
   |    Hedef Adı     | Oluşturulan dosyanın adı.<br /><br /> Bu dizeye veya gibi ifadeler ekleyebilirsiniz `{Name}` `{Owner.Name}` . Örneğin, şunu yazabilirsiniz: `{Owner.Name}_{Name}` . İfade, model öğesi üzerinde değerlendirilir. Yöntemlerin değil, öğelerin özelliklerini kullanabilir. Hangi özelliklerin kullanılabileceğini öğrenmek için **Microsoft. VisualStudio. UML \* **içindeki türlerin özelliklerine bakın. \*\*Önemli: \* \* `{Name}` veya `{Owner.Name}` yalnızca **hedef adı** özelliğinde kullanılabilir.   Oluşturulan sınıfın adını değiştirmek için şablonu değiştirmeniz gerekir. Daha fazla bilgi için bkz. [metin şablonu yazma](#writing). |
   |    Proje Yolu    |                                                                      [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Dönüşümün çıkış dosyalarını içerecek projenin yolunu belirtir. Yeni bir proje oluşturmak için yazılan değerleri kullanın. Varolan bir projeyi seçmek için üç nokta düğmesini (**[...]**) seçin.<br /><br /> Yoksa yeni bir proje oluşturulacaktır. Bu bir C# sınıf kitaplığı projesi olacaktır.<br /><br /> Bunu yapmak için projeyi doğrudan yazmanız gerekir. %ProgramFiles% veya %LocalAppData% gibi ortam değişkeni makrolarını dahil edebilirsiniz.                                                                       |
   |  Hedef Dizin  |                                                                                          Hedef dosyanın oluşturulduğu klasör. Yol, proje klasörüyle ilişkilidir.<br /><br /> `{PackageStructure}`İfadeyi, kapsayan paketlerin adlarına karşılık gelen bir yol eklemek için kullanabilirsiniz. Varsayılan değer: `\GeneratedCode\{PackageStructure}`. %TEMP% veya %HomePath% gibi ortam değişkenlerini de ekleyebilirsiniz. **Önemli:** `{PackageStructure}` yalnızca **hedef dizin** özelliğinde kullanılabilir.                                                                                            |
   | Şablon Dosya Yolu |                                                                                                                                                           Dönüşümü gerçekleştirecek şablon.<br /><br /> Sağlanan şablonları kullanabilir veya kendi şablonunuzu oluşturabilirsiniz. Sağlanan şablonları aşağıdaki konumda bulabilirsiniz:<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. Bir öğeye istediğiniz kadar bağlama ekleyebilirsiniz.

## <a name="writing-a-text-template"></a><a name="writing"></a> Metin şablonu yazma
 Kendi metin şablonlarınızı yazabilirsiniz. Metin şablonları, program kodu veya başka tür bir metin dosyası oluşturabilirsiniz.

 Standart şablonların kopyalarını değiştirerek başlamanızı öneririz. Şablonları aşağıdaki konumlardan kopyalayabilirsiniz:

 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\

 Metin şablonlarını anlamak için aşağıdaki konulara bakın.

- Metin şablonu ortaya çıkan dosyanın prototipidir ve hem ortaya çıkan metni hem de modeli okuyan program kodunu içerir. Daha fazla bilgi için bkz. [kod oluşturma ve T4 Metin şablonları](../modeling/code-generation-and-t4-text-templates.md).

- Program kodundaki UML modeline gitmek için UML API'sini kullanmanız gerekir. Daha fazla bilgi için bkz. [UML modelleme genişletilebilirliği IÇIN](../modeling/api-reference-for-uml-modeling-extensibility.md) [UML modeline](../modeling/navigate-the-uml-model.md) ve API başvurusuna gitme.

  Şablonları **kod oluştur** komutuyla birlikte kullanmak Için, modelleme yönergesini dahil etmeniz gerekir. Örneğin:

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`

  `ElementType`Öznitelik, bu şablonun UYGULANDıĞı UML öğe türünü tanımlar.

  Şablonda, `this` aşağıdaki özelliklere sahip geçici bir sınıfa aittir:

- `Element` = şablonun uygulandığı UML [IElement](/previous-versions/dd516035(v=vs.140)) .

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>

- `Host`: [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

- `ModelBus`: [ModelBus](/previous-versions/ee904639(v=vs.140)). Daha fazla bilgi için bkz. [UML modellerini diğer modeller ve araçlarla tümleştirme](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- `ProfileName` = "C # profili"

- `ServiceProvider`: <xref:System.IServiceProvider>

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Bu, UML ModelStore'un uygulandığı Görselleştirme ve Modelleme SDK Deposudur. UML [IModelStore](/previous-versions/ee789385(v=vs.140))'u almak için kullanın `this.Element.GetModelStore()` .

  Metin şablonu yazarken aşağıdaki noktaları yararlı bulabilirsiniz. Bu bilgiler, [kod oluşturma ve T4 Metin şablonlarında](../modeling/code-generation-and-t4-text-templates.md)ayrıntılı olarak açıklanmıştır.

- Bu sonucun dosya adı uzantısını `Output` yönergesinde ayarlayabilirsiniz. `Output`Her metin şablonunda bir yönerge gereklidir.

- Bazı derlemelere şablon tarafından otomatik olarak başvurulur. Bu derlemeler, örneğin System.dll ve Microsoft.VisualStudio.Uml.Interfaces.dll'yi içerir.

   Oluşturulan program kodunuzda diğer derlemeleri kullanmak için bir yönergesi kullanmanız gerekir `Assembly` . Örneğin:

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`

- Gibi bazı ad alanları `System` , program kodunuza otomatik olarak içeri aktarılır. Diğer ad alanları için, `Import` yönergesini bir ifadesini kullandığınız şekilde kullanabilirsiniz `using` . Örneğin:

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`

- `Include`Başka bir dosyanın metnine başvurmak için yönergesini kullanın.

- Köşeli ayraçlar içine alınmış olan şablon bölümleri `<# ... #>` **kod oluştur** komutu tarafından yürütülür. Şablonun bu parantezlerin dışında kalan bölümleri sonuç dosyasına kopyalanır. Oluşturulan kod ile oluşturulan metni ayırt etmek çok önemlidir. Oluşturulan metin herhangi bir dilde olabilir.

- `<#= Expressions #>` değerlendirilir ve dizelere dönüştürülür.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md) [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md) [bir UML modelden dosya oluşturur](../modeling/generate-files-from-a-uml-model.md)
