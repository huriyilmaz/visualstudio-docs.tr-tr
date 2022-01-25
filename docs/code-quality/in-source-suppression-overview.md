---
title: Kod analizi ihlallerini gizleme
ms.date: 01/18/2022
description: Visual Studio 'de kod çözümleme ihlallerini nasıl bastıralabileceğinizi öğrenin. Kaynak içi gizleme için SuppressMessageAttribute özniteliğini nasıl kullanacağınızı anlayın.
ms.custom: SEO-VS-2020, devdivchpfy22
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 1479ccadd85ecb45686810a896d2f07cf0796c30
ms.sourcegitcommit: e469966b336e939c9271e10d187f1c3696b967d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "137749686"
---
# <a name="suppress-code-analysis-violations"></a>Kod analizi ihlallerini gizleme

Bir uyarının geçerli olmadığını göstermek için genellikle yararlı olur. Kod Analizi ihlallerinin gizlenmesi, takım üyelerinin kodun incelendiğini belirtir ve uyarı bastırılabilir. aşağıdaki bölümlerde, Visual Studio ıde 'yi kullanarak kod analizi ihlallerini görüntülemenin farklı yolları açıklanır.

::: moniker range=">=vs-2019"

## <a name="suppress-violations-using-the-editorconfig-file"></a>EditorConfig dosyasını kullanarak ihlalleri gösterme

Bir **Editorconfig dosyasında** önem derecesini, `none` Örneğin, olarak ayarlayın `dotnet_diagnostic.CA1822.severity = none` . Bir EditorConfig dosyası eklemek için bkz. [bir projeye editorconfig dosyası ekleme](../ide/create-portable-custom-editor-options.md#add-and-remove-editorconfig-files).

::: moniker-end

## <a name="suppress-violations-in-source-code"></a>Kaynak kodundaki ihlalleri gösterme

bir önişlemci yönergesi kullanarak koddaki ihlaller, [#pragma warning (C#)](/dotnet/csharp/language-reference/preprocessor-directives#pragma-warning) veya [Disable (Visual Basic)](/dotnet/visual-basic/language-reference/directives/disable-enable) yönergesini, yalnızca belirli bir kod satırıyla ilgili uyarıyı bastırmak için kaldırabilirsiniz. [SuppressMessage özniteliğini](#in-source-suppression-and-the-suppressmessage-attribute)de kullanabilirsiniz.

- **Kod düzenleyicisinden**

  İmleci kod satırına yerleştirin ve  + **hızlı eylemler** menüsünü açmak için CTRL **dönemi (.)** tuşuna basın. **CAXXXX 'ı Gizle**' yi seçin ve ardından **kaynak** veya **kaynakta (öznitelik)** öğesini seçin.

  **Kaynak '** ı seçerseniz, kodunuza eklenecek Önişlemci yönergesinin önizlemesini görürsünüz.

  ::: moniker range="vs-2017"
  :::image type="content" source="media/suppress-diagnostic-from-editor.png" alt-text="Hızlı Eylemler menüsünden tanılamayı gösterme":::
  ::: moniker-end
  ::: moniker range=">=vs-2019"
  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor.png" alt-text="Hızlı Eylemler menüsünden tanılamayı gösterme":::

  **Kaynak (öznitelik)** seçeneğini belirlerseniz, kodunuza eklenecek [SuppressMessage özniteliğinin](#in-source-suppression-and-the-suppressmessage-attribute) bir önizlemesini görürsünüz.

  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor-attribute.png" alt-text="Özniteliği kullanarak hızlı eylemler menüsünden tanılamayı gösterme":::
  ::: moniker-end

- **Hata listesi**

  Gizlemek istediğiniz kuralları seçin ve ardından sağ tıklayıp kaynakta **Gizle**' yi seçin  >  .

  - **kaynakta** bastırdığınızda, **değişiklikleri önizle** iletişim kutusu açılır ve C# [#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) veya kaynak koda eklenen Visual Basic [#Disable uyarı](/dotnet/visual-basic/language-reference/directives/directives) yönergesinin önizlemesini gösterir.

    ![Kod dosyasında #pragma uyarı ekleme önizlemesi](media/pragma-warning-preview.png)

  **Değişiklikleri Önizle** Iletişim kutusunda **Uygula**' yı seçin.

  > [!NOTE]
  > **Çözüm Gezgini**' de **gizleme** menüsü seçeneğini görmüyorsanız, ihlalin büyük olasılıkla canlı Analize değil derlemeden geliyor. **Hata listesi** , hem canlı kod analizinden hem de derlemeden tanılama veya kural ihlalleri görüntüler. Derleme tanılaması eski olduğundan, örneğin, ihlalin giderilmesi için kodu düzenlediyseniz, ancak yeniden oluşturmadıysanız, **hata listesi** bu tanılamayı gizlenemez. Canlı Analize veya IntelliSense 'e yönelik Tanılamalar, geçerli kaynaklarla her zaman güncel değildir ve **hata listesi** gizlenmiş olabilir. *Oluşturma* tanılamayı seçiminizden dışlamak için, **hata listesi** kaynak filtresini **derleme + IntelliSense** 'den **yalnızca IntelliSense**'e geçirin. Daha sonra, gizlemek istediğiniz tanılamayı seçin ve daha önce açıklandığı gibi devam edin.
  >
  > ![Visual Studio Hata Listesi kaynak filtresi](media/error-list-filter.png)

## <a name="suppress-violations-using-a-global-suppression-file"></a>Küresel bir gizleme dosyası kullanarak ihlalleri gösterme

[Genel gizleme dosyası](#global-level-suppressions) [SuppressMessage özniteliğini](#in-source-suppression-and-the-suppressmessage-attribute)kullanır.

- **Hata listesi**, gizlemek istediğiniz kuralları seçin ve sağ tıklayın ve   >  **gizleme dosyasında** Gizle ' yi seçin. **Değişiklikleri Önizle** iletişim kutusu açılır ve <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> genel gizlemeleri dosyasına eklenen özniteliğin önizlemesini gösterir.

  ![Gizleme dosyasına SuppressMessage özniteliği ekleme önizlemesi](media/preview-changes-in-suppression-file.png)

- **Kod düzenleyicisinden**, imleci kod satırına ihlale yerleştirip **Hızlı Eylemler ve yeniden düzenlemeler** (ya da **CTRL** + **Period (.)** tuşlarına basarak) **hızlı eylemler** menüsünü açın. **CAXXXX 'ı Gizle**' yi seçin ve **gizleme dosyası**' nı seçin. Oluşturulacak veya değiştirilecek [Global gizleme dosyasının](#global-level-suppressions) önizlemesini görürsünüz.

::: moniker range=">=vs-2019"

- **Çözümle** menüsünde,   >  geçerli ihlallerin tümünü bastırmak için derlemeyi çözümle ve menü çubuğunda **etkin sorunları Gizle** ' yi seçin. Tüm geçerli ihlallerin gizlenmesi bazen "taban çizgisi oluşturma" olarak adlandırılır.

::: moniker-end
::: moniker range="vs-2017"

- **çözümle** menüsünde, çalışma Code Analysis **çözümle**' yi seçin  >  ve tüm geçerli ihlallerin görüntülenmesini sağlamak için menü çubuğundaki **etkin sorunları gizleyin** . Tüm geçerli ihlallerin gizlenmesi bazen "taban çizgisi oluşturma" olarak adlandırılır.
::: moniker-end

## <a name="suppress-violations-using-project-settings"></a>Proje ayarlarını kullanarak ihlalleri gösterme

**Çözüm Gezgini**, projenin özelliklerini açın (projeye sağ tıklayın ve **özellikler** ' i seçin (veya **Alt + enter** tuşlarına basın) ve seçenekleri yapılandırmak için **Code Analysis** sekmesini kullanın. Örneğin, Canlı Kod analizini devre dışı bırakabilir veya .NET Çözümleyicileri devre dışı bırakabilirsiniz.

## <a name="suppress-violations-using-a-rule-set"></a>Bir kural kümesi kullanarak ihlalleri gösterme

**Kural kümesi düzenleyicisinden** adının yanındaki onay kutusunu temizleyin veya **eylemi** **none** olarak ayarlayın.

## <a name="in-source-suppression-and-the-suppressmessage-attribute"></a>Kaynak içi gizleme ve SuppressMessage özniteliği

Kaynak içi gizleme (ISS), <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> bir uyarının gösterilmemesi için özniteliğini kullanır. Özniteliği, uyarıyı oluşturan kod kesimine yakın şekilde yerleştirilebilir. <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Özniteliği içine yazarak kaynak dosyasına ekleyebilir veya **hata listesi** kısayol menüsünü otomatik olarak eklemek için bir uyarı üzerinde kullanabilirsiniz.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Özniteliği, yönetilen kod derlemelerinizin Il meta verilerinde bulunan koşullu bir özniteliktir. Bu öznitelik yalnızca derleme sırasında CODE_ANALYSIS derleme sembolü tanımlanırsa dahil edilir.

C++/CLı ' da \_ \_ \_ \_ özniteliği eklemek için, üst bilgi dosyasındaki makrolar CA 'sı iletisini veya CA genel SUPPRESS_MESSAGE 'yi kullanın.

> [!NOTE]
> Kaynak gizleme verilerinin yanlışlıkla serbest bırakılmasını engellemek için sürüm yapılarında kaynak üzerinde gizlemeleri kullanmamalısınız. Ayrıca, kaynak içi göstermeme işleminin işlem maliyeti nedeniyle uygulamanızın performansı düşebilir.

::: moniker range="vs-2017"

> [!NOTE]
> bir projeyi Visual Studio 2017 ' ye geçirirseniz, aniden çok sayıda kod analizi uyarısı ile karşılaşabilirsiniz. uyarıları gidermeye hazırsanız, çalıştır Code Analysis **çözümle**' yi  >  **ve etkin sorunları gizle**' yi seçerek bunların hepsini gizleyebilirsiniz.
>
> ![Kod analizini çalıştırın ve Visual Studio sorunları gizleyin](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> bir projeyi Visual Studio 2019 ' ye geçirirseniz, aniden çok sayıda kod analizi uyarısı ile karşılaşabilirsiniz. Uyarıları gidermeye hazırsanız, derlemeyi **Çözümle**  >  **ve etkin sorunları Gizle**' yi seçerek bunların tümünün görüntülenmesini sağlayabilirsiniz.

::: moniker-end

### <a name="suppressmessage-attribute"></a>SuppressMessage özniteliği

**Hata listesi** bir kod analizi uyarısında bağlam veya sağ tıklama menüsünden **Gizle** ' yi seçtiğinizde, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> kodunuzda veya projenin Global gizleme dosyasına bir öznitelik eklenir.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Özniteliği aşağıdaki biçimdedir:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Özniteliğin özellikleri şunları içerir:

- **Kategori** -kuralın tanımlandığı kategori. Kod analizi kural kategorileri hakkında daha fazla bilgi için bkz. [yönetilen kod uyarıları](/dotnet/fundamentals/code-analysis/quality-rules/index).

- **CheckId** -kuralın tanımlayıcısı. Destek, kural tanımlayıcısı için hem kısa hem de uzun bir ad içerir. Kısa ad CAXXXX; Long adı CAXXXX:

- **Bloklama** -iletinin nasıl bastırılamamasının nedenini belgelemek için kullanılan metin.

- **MessageID** -her ileti için bir sorunun benzersiz tanıtıcısı.

- **Scope** -uyarının gizlendiği hedef. Hedef belirtilmemişse, özniteliğinin hedefine ayarlanır. Desteklenen [kapsamlar](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) şunlardır:

  - [`module`](#module-suppression-scope) -Bu kapsam, bir derlemeye karşı uyarıları göstermez. Tüm proje için geçerli olan genel bir gizleme.

  - `resource` -(yalnızca[eski FxCop](../code-quality/static-code-analysis-for-managed-code-overview.md) ) bu kapsam, modülün parçası olan kaynak dosyalarına yazılan tanılama bilgilerinde uyarıları bastırır (derleme). Bu kapsam, yalnızca kaynak dosyaları analiz eden Roslyn Çözümleyicisi tanılaması için C#/vb derleyicileri tarafından okunamaz veya buna uyulmaz.

  - `type` -Bu kapsam, bir türe karşı uyarıları göstermez.

  - `member` -Bu kapsam, bir üyeye karşı uyarıları göstermez.

  - `namespace` -Bu kapsam, ad alanının kendisiyle karşı uyarıları göstermez. Ad uzayı içindeki türlere karşı uyarıları göstermez.

  - `namespaceanddescendants`-(derleyici sürümü 3. x veya üzeri gerektirir ve Visual Studio 2019) bu kapsam, bir ad alanındaki uyarıları ve tüm alt simgelerini bastırır. `namespaceanddescendants`Değer eski analiz tarafından yok sayılır.

- **Target** -uyarının bastırılmakta olduğu hedefi belirtmek için kullanılan bir tanımlayıcı. Tam nitelikli bir bileşen adı içermelidir.

Visual Studio uyarıları gördüğünüzde, `SuppressMessage` [genel gizleme dosyasına bir gizleme ekleyerek](../code-quality/use-roslyn-analyzers.md#suppress-violations)örneklerini görüntüleyebilirsiniz. Gizleme özniteliği ve gerekli özellikleri bir önizleme penceresinde görünür.

### <a name="suppressmessage-usage"></a>SuppressMessage kullanımı

Code Analysis uyarılar, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğin uygulandığı düzeyde bastırılır. Örneğin, öznitelik derleme, modül, tür, üye veya parametre düzeyinde uygulanabilir. Bu özniteliği uygulamanın amacı, gizleme bilgilerinin ihlalin gerçekleştiği koda sıkı bir şekilde daha sıkı bir şekilde bir şekilde uygulanmasını sağlar.

Gizleme 'nin Genel biçimi kural kategorisini ve kural adının isteğe bağlı olarak okunabilir bir gösterimini içeren bir kural tanımlayıcısını içerir. Örnek:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Kaynak gizleme gizleme meta verilerini en aza indirmek için kesin performans nedenleriyle, kural adı atlanabilir. Kural kategorisi ve kural KIMLIĞI birlikte yeterince benzersiz bir kural tanımlayıcısı oluşturur. Örnek:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Bakım nedeniyle kural adının yok kullanılması önerilmez.

### <a name="suppress-selective-violations-within-a-method-body"></a>Bir yöntem gövdesi içinde seçmeli ihlalleri gizleme

Gizleme öznitelikleri bir yönteme uygulanabilir, ancak bir yöntem gövdesine katıştırılamaz. özniteliğini yöntemine eklersiniz, belirli bir kuralın tüm <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> ihlalleri gizlenr.

Bazı durumlarda, ihlalin belirli bir örneğini gizlemeyi istemeysiniz. Gelecekteki kodun kod analizi kuralından otomatik olarak muaf tutulmay olduğu örneği göz önünde bulundurabilirsiniz. Belirli kod analizi kuralları, özniteliğinin özelliğini kullanarak ihlalin belirli bir örneğini `MessageId` gizlemeye olanak <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> sağlar. Genel olarak, belirli bir sembolde (yerel değişken veya parametre) ihlallere yönelik eski kurallar özelliğine uygun `MessageId` olur. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) böyle bir kural örneğidir. Ancak, yürütülebilir kodda (sembol olmayan) ihlallere ait eski kurallar özelliğine `MessageId` uymaz. Ayrıca, .NET Compiler Platform ("Roslyn") çözümleyicileri özelliğine saygı `MessageId` göstermez.

Bir kuralın belirli bir sembol ihlallerini bastırmak için özniteliğinin özelliği `MessageId` için sembol adını <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> belirtin. Aşağıdaki örnek [ca1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md)iki ihlali olan kodu gösterir değişken için bir ve &mdash; değişken için `name` `age` bir. Yalnızca sembolün `age` ihlali gizlenr.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

### <a name="global-level-suppressions"></a>Genel düzeyde gizlemeler

Yönetilen kod analizi aracı derleme, modül, tür, üye veya parametre düzeyinde uygulanan `SuppressMessage` öznitelikleri inceler. Ayrıca kaynaklara ve ad alanlarına karşı ihlaller de sağlar. Bu ihlaller genel düzeyde uygulanmalıdır ve kapsamlı ve hedeflidir. Örneğin, aşağıdaki ileti ad alanı ihlallerini bastırıyor:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Bir uyarıyı kapsamla `namespace` bastırarak, uyarıyı ad alanının kendisine karşı bastırıyor. Uyarıyı ad alanı içindeki türlere karşı gizlemez.

Herhangi bir gizleme, açık bir kapsam belirterek ifade olabilir. Bu gizlemelerin genel düzeyde olması gerekir. Bir türü değiştirerek üye düzeyinde gizleme belirtemezseniz.

Genel düzey gizlemeler, açıkça sağlanan kullanıcı kaynağıyla eşleşmeden derleyici tarafından oluşturulan koda başvuran iletileri gizlemenin tek yoludur. Örneğin, aşağıdaki kod derleyici tarafından yayılan bir oluşturucuya karşı bir ihlali bastırıyor:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` her zaman tam öğe adını içerir.

#### <a name="global-suppression-file"></a>Genel gizleme dosyası

Genel gizleme dosyası, bir hedef belirtmeden genel düzeyde gizlemeler veya gizlemeler olan gizlemeleri sürdürür. Örneğin, derleme düzeyi ihlaller için gizlemeler bu dosyada depolanır. Ayrıca, proje ASP.NET bir formun ardındaki kod için kullanılabilir durumda olmadığınız için bazı önemli gizlemeler bu dosyada depolanır. Hata Listesi penceresindeki Gizleme komutunun In **Project Suppression File** seçeneğini ilk kez seçerek  projenize genel bir gizleme dosyası **oluşturulur ve** eklenir.

#### <a name="module-suppression-scope"></a>Modül gizleme kapsamı

Modül kapsamını kullanarak bütün derleme için kod kalitesi ihlallerini **bastırabilirsiniz.**

Örneğin, _GlobalSuppressions_ proje dosyanıza aşağıdaki öznitelik, bir ASP.NET Core için ConfigureAwait ihlalini bastırır:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

### <a name="generated-code"></a>Oluşturulan kod

Yönetilen kod derleyicileri ve bazı üçüncü taraf araçlar, hızlı kod geliştirmeye yardımcı olmak için kod üretir. Kaynak dosyalarda görünen derleyici tarafından oluşturulan kod özniteliğiyle `GeneratedCodeAttribute` işaretlenir.

Kaynak kodu analizi için, bir dosyada oluşturulan kodda iletileri `.editorconfig` bastırabilirsiniz. Daha fazla bilgi için [bkz. Oluşturulan kodu hariç tut.](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code)

Eski kod analizi için, oluşturulan kod için kod analizi uyarılarını ve hatalarını gizlemeyi seçebilirsiniz. Bu tür uyarıların ve hataların nasıl gizlenme hakkında bilgi için, bkz. [How to: Suppress Warnings for Generated Code](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Kod analizi bütün `GeneratedCodeAttribute` bir derlemeye veya tek bir parametreye uygulandığında yoksayıyor.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Kod çözümleyicilerini kullanma](../code-quality/use-roslyn-analyzers.md)
