---
title: Seçenekler, Metin Düzenleyici, C#, Gelişmiş
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d1d540f3a49eda22973b25a6b9a91691907efe93
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666284"
---
# <a name="options-text-editor-c-advanced"></a>Seçenekler, Metin Düzenleyici, C#, Gelişmiş

İçin C#düzenleyici biçimlendirme, kod yeniden düzenleme ve XML belge yorumlarının ayarlarını değiştirmek için **Gelişmiş** Seçenekler sayfasını kullanın. Bu seçenekler sayfasına erişmek için **araçlar**  > **Seçenekler**' i seçin ve**Gelişmiş** >   >  **C#** metin düzenleyici ' yi seçin.

> [!NOTE]
> Tüm seçenekler burada listelenmeyebilir.

## <a name="analysis"></a>Çözümleme

- Tam çözüm analizini etkinleştirme

   Yalnızca açık kod dosyalarını değil, Çözümdeki tüm dosyalarda kod analizini mümkün bir şekilde sunar. Daha fazla bilgi için bkz. [tam çözüm Analizi](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Using yönergeleri

- Using deyimlerini sıralarken ' System ' yönergelerini ilk olarak Yerleştir

   Seçildiğinde, sağ tıklama menüsündeki kullanımları **Kaldır ve Sırala** komutu `using` yönergelerini sıralar ve ' System ' ad alanlarını listenin en üstüne koyar.

   Sıralamadan önce:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Sıralama sonrasında:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Yönerge gruplarını kullanarak ayır

   Seçildiğinde, sağ tıklama menüsündeki kullanımları **Kaldır ve Sırala** komutu, aynı kök ad alanına sahip yönergelerin grupları arasına boş bir satır ekleyerek `using` yönergeleri ayırır.

   Sıralamadan önce:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Sıralama sonrasında:

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

- Başvuru derlemelerindeki türler için kullanımlar önerin
- NuGet paketlerindeki türler için kullanımlar önerin

   Bu seçenekler belirlendiğinde, bir NuGet paketini yüklemek ve başvurulmayan türler için bir `using` yönergesi eklemek üzere [hızlı bir eylem](../quick-actions.md) kullanılabilir.

   ![Visual Studio 'da NuGet paketini yüklemeye yönelik hızlı eylem](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Vurgusuz

- İmlecin altındaki simgenin başvurularını Vurgula

   İmleç bir simgenin içine konumlandırıldığında veya bir sembole tıkladığınızda, kod dosyasındaki söz konusu sembolün tüm örnekleri vurgulanır.

## <a name="outlining"></a>Anahat Oluşturma

- Dosyalar açıkken anahat oluşturma moduna gir

   Seçildiğinde, daraltılabilir kod blokları oluşturan kod dosyası otomatik olarak özetlenmektedir. Bir dosya ilk kez açıldığında, #regions blokları ve etkin olmayan kod blokları daraltılır.

- Yordam satırı ayırıcılarını göster

   Metin Düzenleyicisi, yordamların görsel kapsamını gösterir. Aşağıdaki tabloda listelenen konumlarda projenizin *. cs* kaynak dosyalarında bir çizgi çizilir:

   |. Cs kaynak dosyasındaki konum|Satır konumu örneği|
   |---------------------------------|------------------------------|
   |Bir blok bildirimi yapısının kapandıktan sonra|-Bir sınıf, yapı, modül, arabirim veya sabit listesinin sonunda<br />-Bir özellik, işlev veya Sub öğesinden sonra<br />-Bir özellikte get ve set yan tümceleri arasında değil|
   |Tek satırlık bir yapı kümesinden sonra|-İçe aktarma deyimlerinden sonra, bir sınıf dosyasındaki tür tanımından önce<br />-Öğesinden sonra, herhangi bir yordamdan önce, bir sınıfta belirtilen değişkenlerden|
   |Tek satır bildirimleri sonrasında (blok düzeyi olmayan bildirimler)|-Aşağıdaki import deyimleri, Inherits deyimlerini, değişken bildirimlerini, olay bildirimlerini, temsilci bildirimlerini ve DLL bildirme deyimlerini|

## <a name="block-structure-guides"></a>Yapı kılavuzlarını engelle

Kodunuzda süslü ayraçlar ( **{}** ) arasında noktalı dikey çizgiler göstermek için bu onay kutularını seçin. Daha sonra, bildirim düzeyinize ve kod düzeyi yapılarına yönelik ayrı kod bloklarını kolayca görebilirsiniz.

## <a name="editor-help"></a>Düzenleyici yardımı

- ///İçin XML belgesi açıklamaları oluştur

   Seçildiğinde, açıklama giriş `///` yazarak XML belge açıklamaları için XML öğelerini ekler. XML belgeleri hakkında daha fazla bilgi için bkz. [XML belge açıklamalarıC# (Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: belge oluşturmak için XML açıklamaları ekleme](../../ide/reference/generate-xml-documentation-comments.md)
- [XML belge açıklamaları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Kodunuzu XML açıklamalarıyla belgeleme (C# kılavuz)](/dotnet/csharp/codedoc)
- [Dile özgü düzenleyici seçeneklerini ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
