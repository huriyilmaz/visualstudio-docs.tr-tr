---
title: Kod analizi ihlallerini gizleme
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 4ef64528d8686267677020458374ef96143f6e34
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658522"
---
# <a name="suppress-code-analysis-violations"></a>Kod analizi ihlallerini gizleme

Bir uyarının geçerli olmadığını göstermek için genellikle yararlı olur. Bu, takım üyelerinin kodun gözden geçirdiğini ve uyarının bastırılamayacağını gösterir. Kaynak içi gizleme (ISS), <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> bir uyarının gösterilmemesi için özniteliğini kullanır. Özniteliği, uyarıyı oluşturan kod kesimine yakın şekilde yerleştirilebilir. <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Özniteliği içine yazarak kaynak dosyasına ekleyebilir veya **hata listesi** kısayol menüsünü otomatik olarak eklemek için bir uyarı üzerinde kullanabilirsiniz.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Özniteliği, yönetilen kod derlemelerinizin Il meta verilerine dahil olan ve yalnızca derleme sırasında CODE_ANALYSIS derleme sembolü tanımlanırsa koşullu bir özniteliktir.

C++/CLı ' da \_ \_ \_ \_ özniteliği eklemek için, üst bilgi dosyasındaki makrolar CA 'sı iletisini veya CA genel SUPPRESS_MESSAGE 'yi kullanın.

> [!NOTE]
> Kaynak gizleme verilerinin yanlışlıkla serbest bırakılmasını engellemek için sürüm yapılarında kaynak üzerinde gizlemeleri kullanmamalısınız. Ayrıca, kaynak içi göstermeme işleminin işlem maliyeti nedeniyle uygulamanızın performansı düşebilir.

::: moniker range="vs-2017"

> [!NOTE]
> Bir projeyi Visual Studio 2017 ' a geçirirseniz, çok sayıda kod analizi uyarısıyla aniden karşılaşabilirsiniz. Uyarıları gidermeye hazırsanız, **Analyze**  >  **çalışma kodu analizini çözümle ve etkin sorunları Gizle**' yi seçerek bunların tümünün görüntülenmesini sağlayabilirsiniz.
>
> ![Visual Studio 'da Kod analizini çalıştırma ve sorunları gösterme](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Bir projeyi Visual Studio 2019 ' a geçirirseniz, çok sayıda kod analizi uyarısıyla aniden karşılaşabilirsiniz. Uyarıları gidermeye hazırsanız, derlemeyi **Çözümle**  >  **ve etkin sorunları Gizle**' yi seçerek bunların tümünün görüntülenmesini sağlayabilirsiniz.

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage özniteliği

**Hata listesi**bir kod analizi uyarısında bağlam veya sağ tıklama menüsünden **Gizle** ' yi seçtiğinizde, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> kodunuzda veya projenin Global gizleme dosyasına bir öznitelik eklenir.

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

- **Scope** -uyarının gizlendiği hedef. Hedef belirtilmemişse, özniteliğinin hedefine ayarlanır. Desteklenen [kapsamlar](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) şunları içerir:

  - [`module`](#module-suppression-scope) -Bu kapsam, bir derlemeye karşı uyarıları göstermez. Tüm proje için geçerli olan genel bir gizleme.

  - `resource` -(yalnızca[eski FxCop](../code-quality/static-code-analysis-for-managed-code-overview.md) ) bu kapsam, modülün parçası olan kaynak dosyalarına yazılan tanılama bilgilerinde uyarıları bastırır (derleme). Bu kapsam, yalnızca kaynak dosyaları analiz eden Roslyn Çözümleyicisi tanılaması için C#/vb derleyicileri tarafından okunamaz/buna uyulmaz.

  - `type` -Bu kapsam, bir türe karşı uyarıları göstermez.

  - `member` -Bu kapsam, bir üyeye karşı uyarıları göstermez.

  - `namespace` -Bu kapsam, ad alanının kendisiyle karşı uyarıları göstermez. Ad uzayı içindeki türlere karşı uyarıları göstermez.

  - `namespaceanddescendants` -(Derleyici sürümü 3. x veya üzeri ve Visual Studio 2019) bu kapsam, bir ad alanındaki uyarıları ve tüm alt sembolleri bastırır. `namespaceanddescendants`Değer eski analiz tarafından yok sayılır.

- **Target** -uyarının bastırılmakta olduğu hedefi belirtmek için kullanılan bir tanımlayıcı. Tam nitelikli bir öğe adı içermelidir.

Visual Studio 'da uyarıları gördüğünüzde, `SuppressMessage` [genel gizleme dosyasına bir gizleme ekleyerek](../code-quality/use-roslyn-analyzers.md#suppress-violations)örneklerini görüntüleyebilirsiniz. Gizleme özniteliği ve gerekli özellikleri bir önizleme penceresinde görünür.

## <a name="suppressmessage-usage"></a>SuppressMessage kullanımı

Kod Analizi uyarıları, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> özniteliğin uygulandığı düzeyde bastırılır. Örneğin, öznitelik derleme, modül, tür, üye veya parametre düzeyinde uygulanabilir. Bunun amacı, gizleme bilgilerinin ihlalin gerçekleştiği koda sıkı bir şekilde tam olarak daha katı bir biçimde.

Gizleme 'nin Genel biçimi kural kategorisini ve kural adının isteğe bağlı olarak okunabilir bir gösterimini içeren bir kural tanımlayıcısını içerir. Örnek:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Kaynak gizleme gizleme meta verilerini en aza indirmek için kesin performans nedenleriyle, kural adı atlanabilir. Kural kategorisi ve kural KIMLIĞI birlikte yeterince benzersiz bir kural tanımlayıcısı oluşturur. Örnek:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Bakım nedenleriyle, kural adının atlanması önerilmez.

## <a name="suppress-selective-violations-within-a-method-body"></a>Yöntem gövdesinde seçmeli ihlalleri gösterme

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

## <a name="global-level-suppressions"></a>Küresel düzeyde gizlemeler

Yönetilen Kod Analizi Aracı `SuppressMessage` derleme, modül, tür, üye veya parametre düzeyinde uygulanan öznitelikleri inceler. Ayrıca, kaynaklara ve ad alanlarına karşı ihlalleri da tetikler. Bu ihlallerin genel düzeyde uygulanması ve kapsamı belirlenmiş ve hedeflenmiş olması gerekir. Örneğin, aşağıdaki ileti bir ad alanı ihlalini bastırır:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Kapsamla ilgili bir uyarıyı bastırdığınızda `namespace` , bu uyarı ad alanının kendisine karşı bastırır. Ad uzayı içindeki türlere karşı uyarıyı göstermez.

Herhangi bir gizleme açık bir kapsam belirtilerek ifade edilebilir. Bu gizlemeler küresel düzeyde canlı olmalıdır. Bir tür dekorasyon yaparak üye düzeyinde gizleme belirtemezsiniz.

Genel düzey gizlemeler, açıkça sağlanmış Kullanıcı kaynağıyla eşleşmeyen derleyici tarafından üretilen koda başvuran iletileri göstermenin tek yoludur. Örneğin, aşağıdaki kod derleyiciye yayılan bir oluşturucuya karşı bir ihlalin bastırır:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` her zaman tam öğe adını içerir.

### <a name="global-suppression-file"></a>Genel gizleme dosyası

Genel gizleme dosyası, bir hedef belirtmeyen küresel düzeyde gizlemeler veya gizlemeleri olan gizlemeleri korur. Örneğin, derleme düzeyi ihlallerin gizlemeleri bu dosyada depolanır. Ayrıca, bir form arkasındaki kod için proje düzeyi ayarları kullanılamadığından bazı ASP.NET gizlemeleri bu dosyada depolanır. **Hata listesi** penceresinde **Gizle** komutunun **Proje gizleme dosyasını** ilk kez seçtiğinizde, genel bir gizleme dosyası oluşturulur ve projenize eklenir.

### <a name="module-suppression-scope"></a>Modül gizleme kapsamı

**Modül** kapsamını kullanarak derlemenin tamamında kod kalitesi ihlallerini gizleyebilirsiniz.

Örneğin, _Globalsuppressions_ proje dosyanızdaki aşağıdaki öznitelik bir ASP.NET Core projesi Için ConfigureAwait ihlaline neden olacak:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

## <a name="generated-code"></a>Oluşturulan kod

Yönetilen kod derleyicileri ve bazı üçüncü taraf araçları, hızlı kod geliştirmeyi kolaylaştırmak için kod üretir. Kaynak dosyalarda görünen derleyici tarafından oluşturulan kod genellikle `GeneratedCodeAttribute` özniteliğiyle işaretlenir.

Kaynak kodu analizi için bir dosyadaki oluşturulan koddaki iletileri gizleyebilirsiniz `.editorconfig` . Daha fazla bilgi için bkz. [üretilen kodu hariç tutma](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code).

Eski kod analizi için, kod analizi uyarılarını ve üretilen kod hatalarını bastırıp bastırmayacağını seçebilirsiniz. Bu tür uyarıları ve hataları gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: üretilen kod uyarılarını gösterme](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Kod Analizi `GeneratedCodeAttribute` , bir derlemenin tamamına veya tek bir parametreye uygulandığında yok sayılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Kod Çözümleyicileri kullanma](../code-quality/use-roslyn-analyzers.md)
