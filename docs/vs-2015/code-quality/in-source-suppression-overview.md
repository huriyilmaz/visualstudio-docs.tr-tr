---
title: Kaynak gizleme görünümünde genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651569"
---
# <a name="in-source-suppression-overview"></a>Kaynak Bastırmaya Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak içi gizleme, hatalara neden olan kod segmentlerine **SuppressMessage** özniteliğini ekleyerek Yönetilen koddaki kod çözümleme ihlallerini gösterme veya yoksayma olanağıdır. **SuppressMessage** özniteliği, yönetilen kod DERLEMELERINIZIN Il meta verilerine dahil olan ve derleme zamanında CODE_ANALYSIS derleme sembolü tanımlanmışsa koşullu bir özniteliktir.

 C++/CLI ' da özniteliği eklemek için ÜSTBILGI dosyasındaki CA_SUPPRESS_MESSAGE veya CA_GLOBAL_SUPPRESS_MESSAGE makrolarını kullanın.

 Kaynak gizleme verilerinin yanlışlıkla serbest bırakılmasını engellemek için sürüm yapılarında kaynak üzerinde gizlemeleri kullanmamalısınız. Kaynak içi göstermeme işleminin işlem maliyeti nedeniyle uygulamanızın performansı, kaynak listesi gizleme meta verileri eklenerek de azaltılabilir.

> [!NOTE]
> Bu öznitelikleri kendiniz kodlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: menü öğesini kullanarak uyarıları gösterme](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Menü öğesi kod için C++ kullanılamaz.

## <a name="suppressmessage-attribute"></a>SuppressMessage özniteliği
 **Hata listesi** bir kod analizi uyarısına sağ tıklayıp iletileri göster ' e tıkladığınızda, kodunuzda veya projenin Global **gizlemeleri**dosyasına bir **SuppressMessage** özniteliği eklenir.

 **SuppressMessage** özniteliği aşağıdaki biçimdedir:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]

```

 [C++]

```
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")

```

 Konum:

- **Kural kategorisi** -kuralın tanımlandığı kategori. Kod analizi kural kategorileri hakkında daha fazla bilgi için bkz. [yönetilen kod uyarıları Için kod analizi](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Kural kimliği** -kuralın tanımlayıcısı. Destek, kural tanımlayıcısı için hem kısa hem de uzun bir ad içerir. Kısa ad CAXXXX; Long adı CAXXXX:

- **Bloklama** -iletinin nasıl bastırılamamasının nedenini belgelemek için kullanılan metin.

- **Ileti kimliği** -her ileti için bir sorunun benzersiz tanıtıcısı.

- **Scope** -uyarının gizlendiği hedef. Hedef belirtilmemişse, özniteliğinin hedefine ayarlanır. Desteklenen kapsamlar şunları içerir:

  - Modül

  - Ad Alanı

  - Kaynak

  - Tür

  - Üye

- **Target** -uyarının bastırılmakta olduğu hedefi belirtmek için kullanılan bir tanımlayıcı. Tam olarak nitelenmiş öğe adı içermesi gerekir.

## <a name="suppressmessage-usage"></a>SuppressMessage kullanımı
 Kod Analizi uyarıları, **SuppressMessage** özniteliğinin bir örneğinin uygulandığı düzeyde bastırılır. Bunun amacı, gizleme bilgilerinin ihlalin gerçekleştiği koda sıkı bir şekilde tam olarak daha katı bir biçimde.

 Gizleme genel biçimi kural kategorisini ve kural adının isteğe bağlı olarak okunabilir bir gösterimini içeren bir kural tanımlayıcısını içerir. Örneğin,

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 Kaynak gizleme gizleme meta verilerini en aza indirmek için kesin performans nedenleriyle, kural adının kendisi de bırakılabilir. Kural kategorisi ve kural KIMLIĞI birlikte yeterince benzersiz bir kural tanımlayıcısı oluşturur. Örneğin,

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 Bu biçim, bakımma sorunları nedeniyle önerilmez.

## <a name="suppressing-multiple-violations-within-a-method-body"></a>Bir yöntem gövdesinde birden çok Ihlali gizleme
 Öznitelikler yalnızca bir yönteme uygulanabilir ve Yöntem gövdesi içine Katıştırılamaz. Ancak, bir yöntem içinde ihlalin birden çok yinelemesini ayırt etmek için tanımlayıcıyı ileti KIMLIĞI olarak belirtebilirsiniz.

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>Oluşturulan kod
 Yönetilen kod derleyicileri ve bazı üçüncü taraf araçları, hızlı kod geliştirmeyi kolaylaştırmak için kod üretir. Kaynak dosyalarda görünen derleyici tarafından oluşturulan kod genellikle **GeneratedCodeAttribute** özniteliğiyle işaretlenir.

 Kod Analizi uyarılarını ve oluşturulan kod için hataları bastırıp bastırmayacağını seçebilirsiniz. Bu tür uyarıları ve hataları gösterme hakkında daha fazla bilgi için bkz. [nasıl yapılır: üretilen kod uyarılarını gösterme](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

 Kod analizinin tüm derlemeye veya tek bir parametreye uygulandığında **GeneratedCodeAttribute** yok saymadığını unutmayın. Bu durumlar nadiren oluşur.

## <a name="global-level-suppressions"></a>Küresel düzeyde gizlemeler
 Yönetilen Kod Analizi Aracı, bütünleştirilmiş kod, modül, tür, üye veya parametre düzeyinde uygulanan **SuppressMessage** özniteliklerini inceler. Ayrıca, kaynaklara ve ad alanlarına karşı ihlalleri da tetikler. Bu ihlallerin genel düzeyde uygulanması ve kapsamı belirlenmiş ve hedeflenmiş olması gerekir. Örneğin, aşağıdaki ileti bir ad alanı ihlalini bastırır:

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Ad alanı kapsamıyla bir uyarıyı bastırdığınızda, bu uyarı ad alanının kendisine karşı bastırır. Ad uzayı içindeki türlere karşı uyarıyı göstermez.

 Herhangi bir gizleme açık bir kapsam belirtilerek ifade edilebilir. Bu gizlemeler küresel düzeyde canlı olmalıdır. Bir tür dekorasyon yaparak üye düzeyinde gizleme belirtemezsiniz.

 Genel düzey gizlemeler, açıkça sağlanmış Kullanıcı kaynağıyla eşleşmeyen derleyici tarafından üretilen koda başvuran iletileri göstermenin tek yoludur. Örneğin, aşağıdaki kod derleyiciye yayılan bir oluşturucuya karşı bir ihlalin bastırır:

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> Hedef, her zaman tam olarak nitelenmiş öğe adını içerir.

## <a name="global-suppression-file"></a>Genel gizleme dosyası
 Genel gizleme dosyası, bir hedef belirtmeyen küresel düzeyde gizlemeler veya gizlemeleri olan gizlemeleri korur. Örneğin, derleme düzeyi ihlallerin gizlemeleri bu dosyada depolanır. Ayrıca, bazı ASP.NET gizlemeleri bu dosyada saklanır çünkü proje düzeyi ayarları form arkasındaki kodla kullanılamaz. Hata Listesi penceresinde **Iletileri bastır** komutunun **Proje gizleme dosyasını** ilk kez seçtiğinizde, genel bir gizleme oluşturulup projenize eklenir. Daha fazla bilgi için bkz. [nasıl yapılır: menü öğesini kullanarak uyarıları gösterme](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Diagnostics.CodeAnalysis>
