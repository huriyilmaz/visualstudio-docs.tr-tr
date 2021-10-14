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
ms.technology: vs-ide-code-analysis
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: a509aa12f59298af97245647bd971a7272ffcaef
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968182"
---
# <a name="suppress-code-analysis-violations"></a>Kod analizi ihlallerini gizleme

Bir uyarının geçerli olmadığını belirtmek genellikle yararlıdır. Bu, takım üyelerine kodun gözden geçir olduğunu ve uyarının gizlene olduğunu gösterir. Bu makalede, IDE'de kod analizi ihlallerini gizlemenin farklı Visual Studio açıklanmıştır.

::: moniker range=">=vs-2019"

## <a name="suppress-violations-using-the-editorconfig-file"></a>EditorConfig dosyasını kullanarak ihlalleri gizleme

EditorConfig **dosyasında önem** derecelerini olarak `none` ayarlayın; örneğin, `dotnet_diagnostic.CA1822.severity = none` . EditorConfig dosyası eklemek için [bkz. Projeye EditorConfig dosyası ekleme.](../ide/create-portable-custom-editor-options.md#add-and-remove-editorconfig-files)

::: moniker-end

## <a name="suppress-violations-in-source-code"></a>Kaynak kodda ihlalleri gizleme

Uyarıyı yalnızca belirli bir kod satırı için gizlemeye yönelik önişlemci yönergesi, #pragma uyarısı [(C#)](/dotnet/csharp/language-reference/preprocessor-directives#pragma-warning) veya Devre Dışı Bırak [(Visual Basic) yönergesini kullanarak kodda](/dotnet/visual-basic/language-reference/directives/disable-enable) ihlalleri bastırabilirsiniz. Veya [SuppressMessage özniteliğini kullanabilirsiniz.](#in-source-suppression-and-the-suppressmessage-attribute)

- Kod **düzenleyicisinden**

  İmleci ihlalli kod satırına yerleştirerek **Ctrl** + **Period (.)** tuşlarına basarak Hızlı Eylemler **menüsünü** açın. **CAXXXX'i Bastır'ı** seçin ve kaynak **veya Kaynak** **(öznitelik) içinde öğesini seçin.**

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

  Gizlenmelerini istediğiniz kuralları seçin ve ardından sağ tıklayın ve KaynağıNda **Bastır'ı**  >  **seçin.**

  - Kaynakta **gizlemeniz,**  Değişiklikleri Önizme iletişim kutusu açılır ve kaynak koda eklenen C# [#pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) uyarısının veya Visual Basic [#Disable](/dotnet/visual-basic/language-reference/directives/directives) yönergesi önizlemesini gösterir.

    ![Kod dosyasına #pragma önizlemesi](media/pragma-warning-preview.png)

  Değişiklikleri **Önizle iletişim** kutusunda Uygula'ya **tıklayın.**

  > [!NOTE]
  > Çözüm Gezgini'da Menüyü  bastır seçeneğini **görmüyorsanız,** ihlal büyük olasılıkla canlı analizden değil derlemeden geliyor olabilir. Hata **Listesi hem** canlı kod analizinden hem de derlemeden tanılama veya kural ihlallerini görüntüler. Derleme tanılaması eski olduğu için, örneğin, ihlali düzeltmek için kodu düzenle yaptıysanız ancak yeniden oluşturmadıysanız, bu tanılamaları Hata Listesinden **bastıramazsınız.** Canlı analizden veya IntelliSense'den gelen tanılamalar her zaman geçerli kaynaklarla günceldir ve Hata Listesinden **gizlenebilirsiniz.** Derleme *tanılamasını seçiminizin* dışında tutmak  için Hata Listesi kaynak filtresini Build + IntelliSense'den **Yalnızca IntelliSense'e geçiş yapın.**  Ardından, gizlenmelerini istediğiniz tanılamayı seçin ve daha önce açıklandığı gibi devam edin.
  >
  > ![Hata Listesi kaynak filtresi Visual Studio](media/error-list-filter.png)

## <a name="suppress-violations-using-a-global-suppression-file"></a>Genel gizleme dosyası kullanarak ihlalleri gizleme

Genel [gizleme dosyası](#global-level-suppressions) [SuppressMessage özniteliğini kullanır.](#in-source-suppression-and-the-suppressmessage-attribute)

- Hata **Listesinden,** gizlemek istediğiniz kuralları seçin ve ardından sağ tıklayın ve Gizleme Dosyasında  >  **Bastır'ı seçin.** Değişiklikleri **Önizle** iletişim kutusu açılır ve genel gizleme <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> dosyasına eklenen özniteliğin önizlemesini gösterir.

  ![SuppressMessage özniteliğini gizleme dosyasına ekleme önizlemesi](media/preview-changes-in-suppression-file.png)

- Kod **düzenleyicisinden** imleci ihlalli kod satırına yerleştirerek Hızlı eylemler ve yeniden düzenlemeler'e **basın** (veya **Ctrl Period** + **(.)** tuşlarına basarak Hızlı Eylemler **menüsünü** açın. **CAXXXX'i Bastır'ı** seçin ve ardından Dosya **Gizleme'yi seçin.** Oluşturulacak veya [değiştirilecek genel gizleme](#global-level-suppressions) dosyasının önizlemesini görebilirsiniz.

::: moniker range=">=vs-2019"

- Analiz **menüsünden,** tüm geçerli **ihlalleri** bastırmak için menü çubuğunda Derlemeyi Çözümle ve Etkin Sorunları  >   Bastır'ı seçin. Bu bazen "temel" olarak adlandırılır.

::: moniker-end
::: moniker range="vs-2017"

- Analiz **menüsünden,** tüm **geçerli** ihlalleri Code Analysis için Çalıştırmayı Çözümle'yi ve menü çubuğunda Etkin Sorunları  >   Bastır'ı seçin. Bu bazen "temel" olarak adlandırılır.
::: moniker-end

## <a name="suppress-violations-using-project-settings"></a>Proje ayarlarını kullanarak ihlalleri gizleme

Bu **Çözüm Gezgini** proje özelliklerini açın (projeye sağ tıklayın ve Özellikler'i seçin **(veya** Alt **+ Enter** tuşuna basın) ve seçenekleri yapılandırmak için **Code Analysis** sekmesini kullanın. Örneğin, canlı kod analizini veya .NET çözümleyicilerini devre dışı abilirsiniz.

## <a name="suppress-violations-using-a-rule-set"></a>Kural kümesi kullanarak ihlalleri gizleme

Kural kümesi **düzenleyicisinden,** adının yanındaki onay kutusunu temizleyin veya Eylem'i **Yok olarak** **ayarlayın.**

## <a name="in-source-suppression-and-the-suppressmessage-attribute"></a>Kaynak içinde gizleme ve SuppressMessage özniteliği

Kaynak içinde gizleme (ISS), bir uyarıyı <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> bastırmak için özniteliğini kullanır. özniteliği, uyarıyı oluşturan kod kesimine yakın bir şekilde yerleştirilebilirsiniz. özniteliğini kaynak dosyaya yazarak ekleyebilir veya Hata Listesi'nin uyarı menüsündeki kısayol menüsünü kullanarak <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> **otomatik olarak** ekleyebilirsiniz.

özniteliği, yönetilen kod derlemenizin IL meta verilerine dahil edilen bir koşullu özniteliktir, yalnızca derleme zamanında CODE_ANALYSIS derleme <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> simgesi tanımlanmışsa.

C++/CLI içinde, özniteliğini eklemek için üst bilgi dosyasında CA \_ SUPPRESS MESSAGE veya CA GLOBAL SUPPRESS_MESSAGE \_ \_ \_ makrolarını kullanın.

> [!NOTE]
> Kaynak içinde gizleme meta verilerini yanlışlıkla göndermeyi önlemek için yayın derlemelerinde kaynak içinde gizlemeler kullanmamalıdır. Ayrıca, kaynak içinde gizlemenin işleme maliyeti nedeniyle, uygulama performansını düşürebilirsiniz.

::: moniker range="vs-2017"

> [!NOTE]
> Projeyi 2017'Visual Studio geçirirken birden çok kod analizi uyarısıyla karşılaşabilirsiniz. Uyarıları düzeltmeye hazır değilsanız, Çalıştırmayı Analiz Etme ve Etkin Sorunları Code Analysis'yi seçerek  >  **bunların hepsini bastırabilirsiniz.**
>
> ![Kod analizini çalıştırma ve sorunları Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019&quot;

> [!NOTE]
> Bir projeyi Visual Studio 2019'a geçirirken birden çok kod analizi uyarısıyla karşılaşabilirsiniz. Uyarıları düzeltmeye hazır değilsanız Derlemeyi Çözümle ve Etkin Sorunları Bastır'ı seçerek  >  **bunların hepsini bastırabilirsiniz.**

::: moniker-end

### <a name=&quot;suppressmessage-attribute&quot;></a>SuppressMessage özniteliği

Hata Listesinde **bir** kod analizi uyarısının bağlamından bastır'ı veya sağ tıklama menüsünü seçerek **kodunuza** veya projenin genel gizleme dosyasına bir öznitelik <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> eklenir.

özniteliği <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> aşağıdaki biçime sahip:

```vb
<Scope:SuppressMessage(&quot;Rule Category&quot;, &quot;Rule Id&quot;, Justification = &quot;Justification&quot;, MessageId = &quot;MessageId&quot;, Scope = &quot;Scope&quot;, Target = &quot;Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

özniteliğinin özellikleri şunlardır:

- **Kategori-** Kuralın tanımlandığı kategori. Kod analizi kuralı kategorileri hakkında daha fazla bilgi için bkz. [Yönetilen kod uyarıları.](/dotnet/fundamentals/code-analysis/quality-rules/index)

- **CheckId** - Kuralın tanımlayıcısı. Destek, kural tanımlayıcısı için hem kısa hem de uzun bir ad içerir. Kısa ad CAXXXX'tir; uzun ad CAXXXX:FriendlyTypeName'tir.

- **Gerekçe** : İletiyi gizleme nedenini belgelendirmek için kullanılan metin.

- **MessageId** : Her ileti için bir sorunun benzersiz tanımlayıcısı.

- **Kapsam** - Uyarının gizlenen hedefi. Hedef belirtilmezse özniteliğinin hedefine ayarlanır. Desteklenen [kapsamlar](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) aşağıdakileri içerir:

  - [`module`](#module-suppression-scope) - Bu kapsam, bir derlemeye karşı uyarıları bastırıyor. Projenin tamamı için geçerli olan genel bir gizlemedir.

  - `resource` - ([yalnızca eski FxCop)](../code-quality/static-code-analysis-for-managed-code-overview.md) Bu kapsam, modülün parçası olan kaynak dosyalarına yazılan tanılama bilgisinde uyarıları bastırıyor (derleme). Bu kapsam, yalnızca kaynak dosyaları analiz eden Roslyn çözümleyicisi tanılamaları için C#/VB derleyicileri içinde okunmamalıdır/kabul edilemez.

  - `type` - Bu kapsam bir türe karşı uyarıları bastırıyor.

  - `member` - Bu kapsam, bir üyeye karşı uyarıları bastırıyor.

  - `namespace` - Bu kapsam, uyarıları ad alanının kendisine karşı bastırıyor. Uyarıları ad alanı içindeki türlere karşı gizlemez.

  - `namespaceanddescendants`- (Derleyicinin 3.x veya daha yüksek ve Visual Studio 2019 sürümünü gerektirir) Bu kapsam, bir ad alanı ve tüm alt sembollerinin uyarılarını bastırıyor. Değer `namespaceanddescendants` eski analiz tarafından yoksayılır.

- **Hedef** - Uyarının gizlenen hedefini belirtmek için kullanılan tanımlayıcı. Tam öğe adı içermesi gerekir.

içinde uyarı gördüğünüzde Visual Studio genel gizleme dosyasına gizleme ekleyerek `SuppressMessage` [örneklerini görüntüebilirsiniz.](../code-quality/use-roslyn-analyzers.md#suppress-violations) Gizleme özniteliği ve gerekli özellikleri bir önizleme penceresinde görüntülenir.

### <a name="suppressmessage-usage"></a>SuppressMessage kullanımı

Code Analysis uyarıları özniteliğin uygulandığı düzeyde <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> gizlenr. Örneğin, özniteliği derleme, modül, tür, üye veya parametre düzeyinde uygulanabilir. Bunun amacı, gizleme bilgilerini ihlalin oluştuğu kodla sıkı bir şekilde çift etmektir.

Gizlemenin genel biçimi kural kategorisini ve kural adının isteğe bağlı bir insan tarafından okunabilir temsilini içeren kural tanımlayıcısını içerir. Örneğin:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Kaynakta gizleme meta verilerini en aza indirmenin katı performans nedenleri varsa kural adı atlanabilir. Kural kategorisi ve kural kimliği birlikte yeterince benzersiz bir kural tanımlayıcısıdır. Örneğin:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Bakım nedeniyle kural adının yok kullanılması önerilmez.

### <a name="suppress-selective-violations-within-a-method-body"></a>Bir yöntem gövdesi içinde seçmeli ihlalleri gizleme

Gizleme öznitelikleri bir yönteme uygulanabilir, ancak bir yöntem gövdesine katıştırılamaz. Bu, özniteliğini yöntemine eklersiniz, belirli bir kuralın tüm ihlallerinin <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> gizlenecek olduğu anlamına gelir.

Bazı durumlarda, örneğin gelecekteki kodun kod analizi kuralından otomatik olarak muaf tutulmayacak şekilde ihlalin belirli bir örneğini gizlemeyi istemeyebilirsiniz. Belirli kod analizi kuralları, özniteliğinin özelliğini kullanarak `MessageId` bunu yapmaya olanak <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> sağlar. Genel olarak, belirli bir sembolde (yerel değişken veya parametre) ihlallere yönelik eski kurallar özelliğine uygun `MessageId` olur. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) böyle bir kural örneğidir. Ancak, yürütülebilir kodda (sembol olmayan) ihlallere ait eski kurallar özelliğine `MessageId` uymaz. Ayrıca, .NET Compiler Platform ("Roslyn") çözümleyicileri özelliğine saygı `MessageId` göstermez.

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

Herhangi bir gizleme, açık bir kapsam belirterek ifade olabilir. Bu gizlemelerin genel düzeyde olması gerekir. Bir türü dekore etmekle üye düzeyinde gizleme belirtemezseniz.

Genel düzey gizlemeler, açıkça sağlanan kullanıcı kaynağıyla eşleşmeden derleyici tarafından oluşturulan koda başvuran iletileri gizlemenin tek yoludur. Örneğin, aşağıdaki kod derleyici tarafından yayılan oluşturucuya karşı bir ihlali bastırıyor:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` her zaman tam öğe adını içerir.

#### <a name="global-suppression-file"></a>Genel gizleme dosyası

Genel gizleme dosyası, bir hedef belirtmeden genel düzeyde gizlemeler veya gizlemeler olan gizlemeleri sürdürür. Örneğin, derleme düzeyi ihlaller için gizlemeler bu dosyada depolanır. Buna ek olarak, ASP.NET gizlemeleri bu dosyada depolanır çünkü bir formun ardındaki kod için proje düzeyi ayarlar kullanılamaz. Genel bir gizleme dosyası oluşturulur ve Hata Listesi penceresindeki Suppress komutunun **In Project Suppression File** seçeneğini ilk kez seçerek **projenize** eklenir. 

#### <a name="module-suppression-scope"></a>Modül gizleme kapsamı

Modül kapsamını kullanarak bütün derleme için kod  kalitesi ihlallerini bastırabilirsiniz.

Örneğin, _GlobalSuppressions_ proje dosyanıza aşağıdaki öznitelik, bir ASP.NET Core için ConfigureAwait ihlalini bastırır:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

### <a name="generated-code"></a>Oluşturulan kod

Yönetilen kod derleyicileri ve bazı üçüncü taraf araçlar, hızlı kod geliştirmeyi kolaylaştırmak için kod üretir. Kaynak dosyalarda görünen derleyici tarafından oluşturulan kod genellikle özniteliğiyle `GeneratedCodeAttribute` işaretlenir.

Kaynak kodu analizi için, bir dosyada oluşturulan kodda iletileri `.editorconfig` bastırabilirsiniz. Daha fazla bilgi için [bkz. Oluşturulan kodu hariç tut.](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code)

Eski kod analizi için, oluşturulan kod için kod analizi uyarılarını ve hatalarını gizlemeyi seçebilirsiniz. Bu tür uyarıların ve hataların nasıl gizlenme hakkında bilgi için, bkz. [How to: Suppress Warnings for Generated Code](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Kod analizi bütün `GeneratedCodeAttribute` bir derlemeye veya tek bir parametreye uygulandığında yoksayıyor.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Kod çözümleyicilerini kullanma](../code-quality/use-roslyn-analyzers.md)
