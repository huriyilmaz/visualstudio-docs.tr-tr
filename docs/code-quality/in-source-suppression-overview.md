---
title: Kod analizi ihlallerini gizleme
ms.date: 05/10/2021
description: Kod analizi ihlallerini veri kaynaklarında gizlemeyi Visual Studio. Kaynak içinde gizleme için SuppressMessageAttribute özniteliğini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: fd177a96b8789760927933fad5c0320553a72f57
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973349"
---
# <a name="suppress-code-analysis-violations"></a>Kod analizi ihlallerini gizleme

Bir uyarının geçerli olmadığını belirtmek genellikle yararlıdır. Bu, takım üyelerine kodun gözden geçir olduğunu ve uyarının gizlene olduğunu gösterir. Bu makalede, IDE ile kod analizi ihlallerini gizlemenin farklı Visual Studio açıklanmıştır.

::: moniker range=">=vs-2019"

## <a name="suppress-violations-using-the-editorconfig-file"></a>EditorConfig dosyasını kullanarak ihlalleri gizleme

EditorConfig **dosyasında önem** derecelerini olarak `none` ayarlayın; örneğin, `dotnet_diagnostic.CA1822.severity = none` . EditorConfig dosyası eklemek için [bkz. Projeye EditorConfig dosyası ekleme.](../ide/create-portable-custom-editor-options.md#add-and-remove-editorconfig-files)

::: moniker-end

## <a name="suppress-violations-in-source-code"></a>Kaynak kodda ihlalleri gizleme

Bir önişlemci yönergesi, #pragma uyarısı [(C#)](/dotnet/csharp/language-reference/preprocessor-directives.md#pragma-warning) veya Devre Dışı Bırak [(Visual Basic)](/dotnet/visual-basic/language-reference/directives/disable-enable.md) yönergesini kullanarak, uyarıyı yalnızca belirli bir kod satırı için gizlemeyi kullanarak kodda ihlalleri bastırabilirsiniz. Veya [SuppressMessage özniteliğini kullanabilirsiniz.](#in-source-suppression-and-the-suppressmessage-attribute)

- Kod **düzenleyicisinden**

  İmleci ihlalli kod satırına yerleştirerek **Ctrl** + **Period (.)** tuşlarına basarak Hızlı Eylemler **menüsünü** açın. **CAXXXX'i Bastır'ı** seçin ve sonra Kaynak **veya Kaynak** **(öznitelik) içinde öğesini seçin.**

  **Kaynak'ı seçerseniz,** kodunuza eklenecek önişlemci yönergesi önizlemesini görebilirsiniz.

  ::: moniker range="vs-2017"
  :::image type="content" source="media/suppress-diagnostic-from-editor.png" alt-text="Hızlı eylemler menüsünden tanılamayı gizleme":::
  ::: moniker-end
  ::: moniker range=">=vs-2019"
  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor.png" alt-text="Hızlı eylemler menüsünden tanılamayı gizleme":::

  Kaynak **(öznitelik) içinde seçerseniz** kodunuza eklenecek [suppressMessage](#in-source-suppression-and-the-suppressmessage-attribute) özniteliğinin önizlemesini görebilirsiniz.

  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor-attribute.png" alt-text="özniteliğini kullanarak hızlı eylemler menüsünden tanılamayı gizleme":::
  ::: moniker-end

- Hata **Listesinden**

  Gizlemek istediğiniz kuralları seçin ve ardından sağ tıklayıp kaynakta **Gizle**' yi seçin  >  .

  - **Kaynakta** bastırdığınızda, **Değişiklikleri Önizle** iletişim kutusu açılır ve C# [#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) veya kaynak koda eklenen Visual Basic [#Disable uyarı](/dotnet/visual-basic/language-reference/directives/directives) yönergesinin önizlemesini gösterir.

    ![Kod dosyasında #pragma uyarı ekleme önizlemesi](media/pragma-warning-preview.png)

  **Değişiklikleri Önizle** Iletişim kutusunda **Uygula**' yı seçin.

  > [!NOTE]
  > **Çözüm Gezgini**' de **gizleme** menüsü seçeneğini görmüyorsanız, ihlalin büyük olasılıkla canlı Analize değil derlemeden geliyor. **Hata listesi** , hem canlı kod analizinden hem de derlemeden tanılama veya kural ihlalleri görüntüler. Derleme tanılaması eski olduğundan, örneğin, ihlalin giderilmesi için kodu düzenlediyseniz, ancak yeniden oluşturmadıysanız, **hata listesi** bu tanılamayı gizlenemez. Canlı Analize veya IntelliSense 'e yönelik Tanılamalar, geçerli kaynaklarla her zaman güncel değildir ve **hata listesi** gizlenmiş olabilir. *Oluşturma* tanılamayı seçiminizden dışlamak için, **hata listesi** kaynak filtresini **derleme + IntelliSense** 'den **yalnızca IntelliSense**'e geçirin. Daha sonra, gizlemek istediğiniz tanılamayı seçin ve daha önce açıklandığı gibi devam edin.
  >
  > ![Visual Studio 'da Hata Listesi kaynak filtresi](media/error-list-filter.png)

## <a name="suppress-violations-using-a-global-suppression-file"></a>Küresel bir gizleme dosyası kullanarak ihlalleri gösterme

[Genel gizleme dosyası](#global-level-suppressions) [SuppressMessage özniteliğini](#in-source-suppression-and-the-suppressmessage-attribute)kullanır.

- **Hata listesi**, gizlemek istediğiniz kuralları seçin ve sağ tıklayın ve   >  **gizleme dosyasında** Gizle ' yi seçin. **Değişiklikleri Önizle** iletişim kutusu açılır ve <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> genel gizlemeleri dosyasına eklenen özniteliğin önizlemesini gösterir.

  ![Gizleme dosyasına SuppressMessage özniteliği ekleme önizlemesi](media/preview-changes-in-suppression-file.png)

- Kod **düzenleyicisinden** imleci ihlalli kod satırına yerleştirerek  Hızlı eylemler ve yeniden düzenlemeler'e basın (veya **Ctrl** + **Period (.)** tuşlarına basarak **Hızlı Eylemler menüsünü** açın. **CAXXXX'i Bastır'ı** seçin ve ardından Dosya **Gizleme'yi seçin.** Oluşturulacak veya [değiştirilecek genel gizleme](#global-level-suppressions) dosyasının önizlemesini görebilirsiniz.

::: moniker range=">=vs-2019"

- Analiz **menüsünden,** tüm geçerli **ihlalleri** bastırmak için menü çubuğunda Derlemeyi Çözümle ve Etkin Sorunları  >   Bastır'ı seçin. Bu bazen "temel" olarak adlandırılır.

::: moniker-end
::: moniker range="vs-2017"

- Analiz **menüsünden,** tüm **geçerli** ihlalleri Code Analysis için Çalıştırmayı Çözümle'yi ve menü çubuğunda Etkin Sorunları  >   Bastır'ı seçin. Bu bazen "temel" olarak adlandırılır.
::: moniker-end

## <a name="suppress-violations-using-project-settings"></a>Proje ayarlarını kullanarak ihlalleri gizleme

Bu **Çözüm Gezgini** proje özelliklerini açın (projeye sağ tıklayın ve Özellikler'i seçin **(veya** Alt **+ Enter** tuşuna basın) ve seçenekleri yapılandırmak için **Code Analysis** sekmesini kullanın. Örneğin, canlı kod analizini veya .NET çözümleyicilerini devre dışı abilirsiniz.

## <a name="suppress-violations-using-a-rule-set"></a>Kural kümesi kullanarak ihlalleri gizleme

Kural kümesi **düzenleyicisinde adının** yanındaki onay kutusunu temizleyin veya Eylem'i Yok **olarak** **ayarlayın.**

## <a name="in-source-suppression-and-the-suppressmessage-attribute"></a>Kaynak içinde gizleme ve SuppressMessage özniteliği

Kaynak içinde gizleme (ISS), bir uyarıyı <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> bastırmak için özniteliğini kullanır. özniteliği, uyarıyı oluşturan kod kesimine yakın bir şekilde yerleştirilebilirsiniz. özniteliğini kaynak dosyaya yazarak ekleyebilir veya Hata Listesi'nin uyarı menüsündeki kısayol menüsünü <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> **kullanarak otomatik olarak** ekleyebilirsiniz.

özniteliği, yönetilen kod derlemenizin IL meta verilerine dahil edilen bir koşullu özniteliktir, yalnızca derleme zamanında CODE_ANALYSIS derleme <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> simgesi tanımlanmışsa.

C++/CLI içinde, özniteliğini eklemek için üst bilgi dosyasında CA \_ SUPPRESS MESSAGE veya CA GLOBAL SUPPRESS_MESSAGE \_ \_ \_ makrolarını kullanın.

> [!NOTE]
> Kaynak gizleme verilerinin yanlışlıkla serbest bırakılmasını engellemek için sürüm yapılarında kaynak üzerinde gizlemeleri kullanmamalısınız. Ayrıca, kaynak içi göstermeme işleminin işlem maliyeti nedeniyle uygulamanızın performansı düşebilir.

::: moniker range="vs-2017"

> [!NOTE]
> Bir projeyi Visual Studio 2017 ' a geçirirseniz, çok sayıda kod analizi uyarısıyla aniden karşılaşabilirsiniz. Uyarıları gidermeye hazırsanız,   >  **çalışma kodu analizini çözümle ve etkin sorunları Gizle**' yi seçerek bunların tümünün görüntülenmesini sağlayabilirsiniz.
>
> ![Visual Studio 'da Kod analizini çalıştırma ve sorunları gösterme](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019&quot;

> [!NOTE]
> Bir projeyi Visual Studio 2019 ' a geçirirseniz, çok sayıda kod analizi uyarısıyla aniden karşılaşabilirsiniz. Uyarıları gidermeye hazırsanız, derlemeyi **Çözümle**  >  **ve etkin sorunları Gizle**' yi seçerek bunların tümünün görüntülenmesini sağlayabilirsiniz.

::: moniker-end

### <a name=&quot;suppressmessage-attribute&quot;></a>SuppressMessage özniteliği

**Hata listesi** bir kod analizi uyarısında bağlam veya sağ tıklama menüsünden **Gizle** ' yi seçtiğinizde, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> kodunuzda veya projenin Global gizleme dosyasına bir öznitelik eklenir.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Özniteliği aşağıdaki biçimdedir:

```vb
<Scope:SuppressMessage(&quot;Rule Category&quot;, &quot;Rule Id&quot;, Justification = &quot;Justification&quot;, MessageId = &quot;MessageId&quot;, Scope = &quot;Scope&quot;, Target = &quot;Target")>
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

- **Scope** -uyarının gizlendiği hedef. Hedef belirtilmemişse, özniteliğinin hedefine ayarlanır. Desteklenen [kapsamlar](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) şunları içerir:

  - [`module`](#module-suppression-scope) - Bu kapsam, bir derlemeye karşı uyarıları bastırıyor. Projenin tamamı için geçerli olan genel bir gizlemedir.

  - `resource` - ([yalnızca eski FxCop)](../code-quality/static-code-analysis-for-managed-code-overview.md) Bu kapsam, modülün parçası olan kaynak dosyalarına yazılan tanılama bilgisinde uyarıları bastırıyor (derleme). Bu kapsam, yalnızca kaynak dosyaları analiz eden Roslyn çözümleyicisi tanılamaları için C#/VB derleyicileri içinde okunmamalıdır/kabul edilemez.

  - `type` - Bu kapsam bir türe karşı uyarıları bastırıyor.

  - `member` - Bu kapsam, bir üyeye karşı uyarıları bastırıyor.

  - `namespace` - Bu kapsam, uyarıları ad alanının kendisine karşı bastırıyor. Uyarıları ad alanı içindeki türlere karşı gizlemez.

  - `namespaceanddescendants` - (Derleyicinin 3.x veya üst sürümünü ve 2019'Visual Studio gerektirir) Bu kapsam, bir ad alanı ve tüm alt simgelerde uyarıları bastırıyor. Değer `namespaceanddescendants` eski analiz tarafından yoksayılır.

- **Hedef** - Uyarının gizlenen hedefini belirtmek için kullanılan tanımlayıcı. Tam öğe adı içermesi gerekir.

içinde uyarı gördüğünüzde Visual Studio genel gizleme dosyasına gizleme ekleyerek `SuppressMessage` [örneklerini görüntüebilirsiniz.](../code-quality/use-roslyn-analyzers.md#suppress-violations) Gizleme özniteliği ve gerekli özellikleri bir önizleme penceresinde görüntülenir.

### <a name="suppressmessage-usage"></a>SuppressMessage kullanımı

Code Analysis uyarıları özniteliğin uygulandığı düzeyde <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> gizlenr. Örneğin, özniteliği derleme, modül, tür, üye veya parametre düzeyinde uygulanabilir. Bunun amacı, gizleme bilgilerini ihlalin oluştuğu kodla sıkı bir şekilde çift etmektir.

Gizlemenin genel biçimi kural kategorisini ve kural adının isteğe bağlı bir insan tarafından okunabilir temsilini içeren kural tanımlayıcısını içerir. Örnek:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Kaynakta gizleme meta verilerini en aza indirmenin katı performans nedenleri varsa kural adı atlanabilir. Kural kategorisi ve kural KIMLIĞI birlikte yeterince benzersiz bir kural tanımlayıcısı oluşturur. Örnek:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Bakım nedenleriyle, kural adının atlanması önerilmez.

### <a name="suppress-selective-violations-within-a-method-body"></a>Yöntem gövdesinde seçmeli ihlalleri gösterme

Gizleme öznitelikleri bir yönteme uygulanabilir, ancak bir yöntem gövdesi içine Katıştırılamaz. Bu, yöntemine özniteliğini eklediğinizde belirli bir kuralın tüm ihlallerinin gizlendiği anlamına gelir <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> .

Bazı durumlarda, örneğin, gelecekteki kodun kod analizi kuralından otomatik olarak muaf olmaması gibi, ihlalin belirli bir örneğini bastırmak isteyebilirsiniz. Belirli kod analizi kuralları `MessageId` , bu özelliği özniteliğin özelliğini kullanarak yapmanıza olanak sağlar <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> . Genel olarak, belirli bir sembolde (yerel bir değişken veya parametre) ihlal için eski kurallar özelliğe göre yapılır `MessageId` . [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) , böyle bir kurala bir örnektir. Ancak, yürütülebilir koddaki (simge dışı) ihlaller için eski kurallar `MessageId` özelliğe uymaz. Ayrıca, .NET Compiler Platform ("Roslyn") Çözümleyicileri, özelliği dikkate vermez `MessageId` .

Bir kuralın belirli bir sembol ihlalini engellemek için, özniteliğin özelliğinin sembol adını belirtin `MessageId` <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> . Aşağıdaki örnek, değişken için bir tane olmak üzere [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md)için iki ihlal içeren kodu gösterir &mdash; `name` `age` . Yalnızca `age` sembol ihlali bastırılır.

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

### <a name="global-level-suppressions"></a>Küresel düzeyde gizlemeler

Yönetilen Kod Analizi Aracı `SuppressMessage` derleme, modül, tür, üye veya parametre düzeyinde uygulanan öznitelikleri inceler. Ayrıca, kaynaklara ve ad alanlarına karşı ihlalleri da tetikler. Bu ihlallerin genel düzeyde uygulanması ve kapsamı belirlenmiş ve hedeflenmiş olması gerekir. Örneğin, aşağıdaki ileti bir ad alanı ihlalini bastırır:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Kapsamla ilgili bir uyarıyı bastırdığınızda `namespace` , bu uyarı ad alanının kendisine karşı bastırır. Uyarıyı ad alanı içindeki türlere karşı gizlemez.

Herhangi bir gizleme, açık bir kapsam belirterek ifade olabilir. Bu gizlemeler genel düzeyde yaşanıyor olması gerekir. Bir türü dekore etmekle üye düzeyinde gizleme belirtemezseniz.

Genel düzey gizlemeler, açıkça sağlanan kullanıcı kaynağıyla eşleşmeden derleyici tarafından oluşturulan koda başvuran iletileri gizlemenin tek yoludur. Örneğin, aşağıdaki kod derleyici tarafından yayılan bir oluşturucuya karşı bir ihlali bastırıyor:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` her zaman tam öğe adını içerir.

#### <a name="global-suppression-file"></a>Genel gizleme dosyası

Genel gizleme dosyası, bir hedef belirtmeden genel düzeyde gizlemeler veya gizlemeler olan gizlemeleri sürdürür. Örneğin, derleme düzeyi ihlaller için gizlemeler bu dosyada depolanır. Ayrıca, proje ASP.NET bir formun ardındaki kod için kullanılabilir durumda olmadığınız için bazı önemli gizlemeler bu dosyada depolanır. Hata Listesi penceresindeKimlikle komutunun Proje Gizleme Dosyasında  seçeneğini ilk kez seçerek  projenize bir genel gizleme dosyası oluşturulur **ve eklenir.**

#### <a name="module-suppression-scope"></a>Modül gizleme kapsamı

Modül kapsamını kullanarak bütün derleme için kod kalitesi ihlallerini **bastırabilirsiniz.**

Örneğin, _GlobalSuppressions_ proje dosyanıza aşağıdaki öznitelik, ASP.NET Core projesi için ConfigureAwait ihlalini bastırır:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

### <a name="generated-code"></a>Oluşturulan kod

Yönetilen kod derleyicileri ve bazı üçüncü taraf araçlar, hızlı kod geliştirmeyi kolaylaştırmak için kod üretir. Kaynak dosyalarda görünen derleyici tarafından oluşturulan kod genellikle özniteliğiyle `GeneratedCodeAttribute` işaretlenir.

Kaynak kodu analizi için, bir dosyada oluşturulan kodda iletileri `.editorconfig` bastırabilirsiniz. Daha fazla bilgi için [bkz. Oluşturulan kodu hariç tut.](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code)

Eski kod analizi için, kod analizi uyarılarını ve üretilen kod hatalarını bastırıp bastırmayacağını seçebilirsiniz. Bu tür uyarıları ve hataları gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: üretilen kod uyarılarını gösterme](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Kod Analizi `GeneratedCodeAttribute` , bir derlemenin tamamına veya tek bir parametreye uygulandığında yok sayılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Kod Çözümleyicileri kullanma](../code-quality/use-roslyn-analyzers.md)
