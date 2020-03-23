---
title: Seçenekler, Metin Düzenleyici, C#, Gelişmiş
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d0e04a011612cdebebd244fc061981b713b858a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431494"
---
# <a name="options-text-editor-c-advanced"></a>Seçenekler, Metin Düzenleyici, C#, Gelişmiş

Düzenleyici biçimlendirme, kod yeniden düzenleme ve C#için XML dokümantasyon yorumlarını değiştirmek için **Gelişmiş** seçenekler sayfasını kullanın. Bu seçenekler sayfasına erişmek için **Araçlar** > **Seçenekleri'ni**seçin ve ardından **Metin Düzenleyicisi** > **C#** > **Advanced'i**seçin.

> [!NOTE]
> Tüm seçenekler burada listelenmemiş olabilir.

## <a name="analysis"></a>Analiz

- Canlı kod analizi veya Arka Plan analizi kapsamı

   Yönetilen kod için arka plan çözümleme kapsamını yapılandırın. Daha fazla bilgi için [bkz: Yönetilen kod için canlı kod çözümlemesi kapsamını yapılandırma.](../../code-quality/configure-live-code-analysis-scope-managed-code.md)

## <a name="using-directives"></a>Direktifleri Kullanma

- Kullanır sıralama yaparken önce 'Sistem' yönergelerini yerleştirin

   Seçildiğinde, Sağ tıklatma menüsündeki **Kullanımları Kaldır ve Sırala** komutu `using` yönergeleri sıralar ve 'Sistem' ad alanlarını listenin en üstüne yerleştirir.

   Sıralamadan önce:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Sıralamadan sonra:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Yönerge gruplarını ayrı kullanma

   Seçildiğinde, sağ tıklatma menüsündeki **Kullan-Kaldır komutu,** aynı kök ad alanına sahip yönerge grupları arasına boş bir satır ekleyerek `using` yönergeleri ayırır.

   Sıralamadan önce:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Sıralamadan sonra:

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

- .NET Framework derlemelerinde türleri için kullanır önerin
- NuGet paketlerindeki türler için kullanma önerin

   Bu seçenekler seçildiğinde, [Quick Action](../quick-actions.md) Bir NuGet paketi yüklemek ve başvurulmamış türler için bir `using` yönerge eklemek için hızlı eylem kullanılabilir.

   ![Visual Studio'da NuGet paketini yüklemek için hızlı aksiyon](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Vurgulama

- İmleç altında sembole yapılan başvuruları vurgulama

   İmleç bir sembolün içine yerleştirildiğinde veya bir sembolü tıklattığınızda, kod dosyasındaki bu sembolün tüm örnekleri vurgulanır.

## <a name="outlining"></a>Anahat Oluşturma

- Dosyalar açıldığında anahat modunu girin

   Seçildiğinde, otomatik olarak kod dosyası, hangi kod katlanabilir blokları oluşturur özetliyor. Bir dosya ilk açıldığında, #regions blokları ve etkin olmayan kod blokları daraltılır.

- Yordam çizgisi ayırıcılarını göster

   Metin düzenleyicisi yordamların görsel kapsamını gösterir. Aşağıdaki tabloda listelenen konumlarda projenizin *.cs* kaynak dosyalarında bir çizgi çizilir:

   |.cs Kaynak Dosyasındaki Konum|Hat Konumu Örneği|
   |---------------------------------|------------------------------|
   |Bir blok bildirimi oluşturma kapatıldıktan sonra|- Bir sınıfın sonunda, yapı, modül, arayüz veya enum<br />- Bir özellik, işlev veya alt<br />- Bir özellikteki al ve ayar yan tümceleri arasında değil|
   |Tek satır yapılarından sonra|- Alma ekstresinden sonra, sınıf dosyasındaki tür tanımından önce<br />- Bir sınıfta bildirilen değişkenlerden sonra, herhangi bir yordamdan önce|
   |Tek satır lı bildirimlerden sonra (blok düzeyinde olmayan düzey bildirimleri)|- İthalat beyannamelerini takiben, beyannameleri, değişken beyannameleri, olay beyanları, temsilci beyanları ve DLL beyan beyan beyanları|

## <a name="block-structure-guides"></a>Blok Yapı Kılavuzları

Kodunuzdaki kıvırcık köşeli ayraçlar arasında**{}** noktalı dikey çizgiler görüntülemek için bu onay kutularını seçin. Daha sonra, bildirim düzeyiniz ve kod düzeyi yapınız için tek tek kod bloklarını kolayca görebilirsiniz.

## <a name="editor-help"></a>Editör Yardımı

- Için XML dokümantasyon açıklamaları oluşturma

   Seçildiğinde, yorum girişini yazdıktan sonra XML dokümantasyon `///` açıklamaları için XML öğelerieklenir. XML belgeleri hakkında daha fazla bilgi için [Bkz. XML Dokümantasyon Yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılsın: Belge oluşturma için XML açıklamaları ekleme](../../ide/reference/generate-xml-documentation-comments.md)
- [XML Belgeleri Yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Kodunuzu XML yorumlarıyla belgele (C# Kılavuzu)](/dotnet/csharp/codedoc)
- [Dile özel düzenleyici seçeneklerini ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
