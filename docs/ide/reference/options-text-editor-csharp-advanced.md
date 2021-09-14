---
title: Seçenekler, Metin Düzenleyici, C#, Gelişmiş
description: C# için düzenleyici biçimlendirme, kod yeniden düzenleme ve XML belge açıklamaları için ayarları değiştirmek üzere C# bölümündeki gelişmiş sayfasını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 193b7cc73b87bee1a5332bd1b46a38276f0fb4b0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724912"
---
# <a name="options-text-editor-c-advanced"></a>Seçenekler, Metin Düzenleyici, C#, Gelişmiş

C# için düzenleyici biçimlendirme, kod yeniden düzenleme ve XML belge yorumlarının ayarlarını değiştirmek için **Gelişmiş** Seçenekler sayfasını kullanın. Bu seçenekler sayfasına erişmek için **Araçlar**  >  **Seçenekler**' i ve ardından **metin düzenleyici**  >  **C#**  >  **Gelişmiş**' i seçin.

> [!NOTE]
> Tüm seçenekler burada listelenmeyebilir.

## <a name="analysis"></a>Analiz

- Canlı kod analizi veya arka plan Analizi kapsamı

   Yönetilen kod için arka plan Analizi kapsamını yapılandırın. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod için canlı kod analizi kapsamını yapılandırma](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Using yönergeleri

- Using deyimlerini sıralarken ' System ' yönergelerini ilk olarak Yerleştir

   Seçildiğinde, sağ tıklama menüsündeki kullanımları **Kaldır ve Sırala** komutu `using` yönergeleri sıralar ve listenin en üstüne ' sistem ' ad alanlarını koyar.

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

   Seçildiğinde, sağ tıklama menüsündeki kullanımları **Kaldır ve Sırala** komutu, `using` aynı kök ad alanına sahip yönergelerin grupları arasına boş bir satır ekleyerek yönergeleri ayırır.

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

::: moniker range=">=vs-2019"                                              
- .NET Framework derlemelerindeki türler için kullanımlar önerin
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- Başvuru derlemelerindeki türler için kullanımlar önerin
::: moniker-end                                                            

- NuGet paketlerindeki türler için kullanımlar önerin

   bu seçenekler belirlendiğinde, bir NuGet paketini yüklemek ve başvurulmayan türler için bir yönerge eklemek üzere [hızlı bir eylem](../quick-actions.md) mevcuttur `using` .

   ![Visual Studio NuGet paketi yüklemek için hızlı eylem](media/nuget-lightbulb.png)

- Yapıştırma sırasında eksik using yönergelerini ekle

    Bu seçenek belirlendiğinde, `using` bir dosyaya bir tür yapıştırdığınızda yönergeler otomatik olarak kodunuza eklenir.

## <a name="highlighting"></a>Vurgulama

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

Kodunuzda süslü ayraçlar () arasında noktalı dikey çizgiler göstermek için bu onay kutularını seçin **{}** . Daha sonra, bildirim düzeyinize ve kod düzeyi yapılarına yönelik ayrı kod bloklarını kolayca görebilirsiniz.

## <a name="comments"></a>Yorumlar

- ///İçin XML belgesi açıklamaları oluştur

   Seçildiğinde, açıklama giriş yazdıktan sonra XML belge açıklamaları için XML öğelerini ekler `///` . XML belgeleri hakkında daha fazla bilgi için bkz. [XML belgeleri Yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

::: moniker range=">=vs-2019"

## <a name="inline-hints"></a>Satır içi Ipuçları

- Satır İçi Parametre Adı İpuçları 
    
    Seçildiğinde, işlev çağrılarında her bağımsız değişkenden önce sabit değerler, atama sabit değerleri ve nesne örneklemeleri için parametre adı ipuçları ekler.  
    
    ![CSharp için satır içi parametre adı Ipuçları](media/inline-parameter-name-hints-csharp.png)

- Satır içi tür Ipuçları 
    
    Seçildiğinde, çıkartılan türler ve Lambda parametre türleri olan değişkenler için tür ipuçları ekler.  
    
    ![CSharp için satır içi tür Ipuçları](media/inline-type-hints-csharp.png)

## <a name="inheritance-margin"></a>Devralma kenar boşluğu 

- Seçildiğinde, kodunuzun uygulamalarını ve geçersiz kılmalarını temsil eden kenar boşluklarına simgeler ekler. Devralma kenar boşluğu simgelerine tıkladığınızda, gitmek için seçebileceğiniz devralma seçenekleri görüntülenir.

    ![Devralma kenar boşluğu](media/inheritance-margin.png)

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: belge oluşturmak için XML açıklamaları ekleme](../../ide/reference/generate-xml-documentation-comments.md)
- [XML Belgeleri Yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Kodunuzu XML açıklamalarıyla belgeleme (C# Kılavuzu)](/dotnet/csharp/codedoc)
- [Dile özgü düzenleyici seçeneklerini ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
