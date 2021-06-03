---
title: Seçenekler, Metin Düzenleyici, C#, Gelişmiş
description: C# için düzenleyici biçimlendirme, kod yeniden düzenleme ve XML belge açıklamalarını değiştirmek üzere C# bölümündeki Gelişmiş sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 29f6dd2b4a101132bc7bc19664c51fd5d4b8283e
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352000"
---
# <a name="options-text-editor-c-advanced"></a>Seçenekler, Metin Düzenleyici, C#, Gelişmiş

C# **için** düzenleyici biçimlendirme, kod yeniden düzenleme ve XML belge açıklamalarını değiştirmek üzere Gelişmiş seçenekler sayfasını kullanın. Bu seçenekler sayfasına erişmek için Araçlar **Seçenekleri'ni**  >  **ve** ardından Metin Düzenleyici   >  **C# Gelişmiş'i**  >  **seçin.**

> [!NOTE]
> Tüm seçenekler burada listelenmiyor olabilir.

## <a name="analysis"></a>Analiz

- Canlı kod analizi veya Arka plan analizi kapsamı

   Yönetilen kod için arka plan analizi kapsamını yapılandırma. Daha fazla bilgi için [bkz. Nasıl yapılandırılır: Yönetilen kod için canlı kod analizi kapsamını yapılandırma.](../../code-quality/configure-live-code-analysis-scope-managed-code.md)

## <a name="using-directives"></a>Yönergeleri Kullanma

- Usings sıralamada 'System' yönergelerini ilk önce yer

   Seçildiğinde, sağ **tıklama menüsündeki** KullanarakLarı Kaldır ve Sırala komutu yönergeleri sıralar ve 'Sistem' ad alanlarını `using` listenin en üstüne yer.

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

- Kullanma yönerge gruplarını ayırma

   Seçildiğinde, **sağ** tıklama menüsündeki Kullanmaları Kaldır ve Sırala komutu, aynı kök ad alanına sahip yönerge grupları arasına boş bir satır ekerek yönergeleri birbirinden `using` ayırıyor.

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
- Derlemelerde türler için .NET Framework önerme
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- Başvuru derlemelerinde türler için kullanma önerin
::: moniker-end                                                            

- NuGet paketlerinde türler için kullanma önerin

   Bu seçenekler seçildiğinde, NuGet paketini [yüklemek](../quick-actions.md) ve bağlantı kurulmaz türler için bir yönerge eklemek `using` için bir Hızlı Eylem kullanılabilir.

   ![NuGet paketini Visual Studio'a yüklemek için hızlı Visual Studio](media/nuget-lightbulb.png)

- Yapıştırma sırasında eksik using yönergelerini ekle

    Bu seçenek seçildiğinde, `using` bir dosyaya bir tür yapıştırırsanız yönergeleri kodunuza otomatik olarak eklenir.

## <a name="highlighting"></a>Vurgulama

- İmleç altındaki sembol başvurularını vurgulama

   İmleç bir sembolün içine yerleştirilirken veya bir simgeye tıklarsanız, kod dosyasındaki bu sembolün tüm örnekleri vurgulanır.

## <a name="outlining"></a>Anahat Oluşturma

- Dosyalar açıkken açıklama modu girin

   Seçildiğinde, daraltılabilir kod blokları oluşturan kod dosyasını otomatik olarak özetler. Bir dosya ilk kez açıldığında, bloklar #regions etkin olmayan kod blokları daraltır.

- Yordam çizgisi ayırıcılarını gösterme

   Metin düzenleyicisi, yordamların görsel kapsamını gösterir. Aşağıdaki tabloda listelenen konumlarda projenizin *.cs* kaynak dosyalarında bir satır çizilir:

   |.cs Kaynak DosyasındaKi Konum|Satır Konumu Örneği|
   |---------------------------------|------------------------------|
   |Blok bildirimi yapısı kapat sonrasında|- Bir sınıfın, yapının, modülün, arabirimin veya enum'un sonunda<br />- Bir özellik, işlev veya alt işlevden sonra<br />- Bir özellikte get ve set yan tümceleri arasında değil|
   |Tek satırlı yapılardan sonra|- İçeri aktarma deyimlerini, bir sınıf dosyasındaki tür tanımından önce<br />- Herhangi bir yordamdan önce, bir sınıfta bildirilen değişkenler sonra|
   |Tek satırlı bildirimlerin ardından (blok düzeyinde olmayan bildirim)|- İçeri aktarma deyimlerini takip ediyor, deyimlerini, değişken bildirimlerini, olay bildirimlerini, temsilci bildirimlerini ve DLL bildirim deyimlerini devralıyor|

## <a name="block-structure-guides"></a>Blok Yapısı Kılavuzları

Kodundaki köşeli ayraçlar ( ) arasında noktalı dikey çizgiler görüntülemek için **{}** bu onay kutularını seçin. Daha sonra bildirim düzeyi ve kod düzeyi yapılarınız için tek tek kod bloklarını kolayca abilirsiniz.

## <a name="comments"></a>Yorumlar

- /// için XML belge yorumları oluşturma

   Seçildiğinde, siz açıklamaya giriş yazdikten sonra XML belge açıklamalarını xml `///` öğeleri ekler. XML belgeleri hakkında daha fazla bilgi için [bkz. XML Belgeleri Yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

::: moniker range=">=vs-2019"

## <a name="inline-hints"></a>Satır Içi İpuçları

- Satır İçi Parametre Adı İpuçları 
    
    Seçildiğinde, işlev çağrılarında her bağımsız değişkenden önce değişmez değer, döküm değişmez değerleri ve nesne örnek oluşturmaları için parametre adı ipuçları ekler.  
    
    ![CSharp için Satır Içi Parametre Adı İpuçları](media/inline-parameter-name-hints-csharp.png)

- Satır Içi Tür İpuçları 
    
    Seçildiğinde, ertelenmiş türlere ve lambda parametre türlerine sahip değişkenler için tür ipuçları ekler.  
    
    ![CSharp için Satır Içi Tür İpuçları](media/inline-type-hints-csharp.png)

## <a name="inheritance-margin"></a>Devralma Marjı 

- Seçildiğinde, kenar boşluklarında kodunuzun uygulama ve geçersiz kılmalarını temsil eden simgeler ekler. Devralma kenar boşluğu simgelerine tıklarsa, gitmek için seçebilirsiniz devralma seçenekleri görüntülenir.

    ![Devralma Marjı](media/inheritance-margin.png)

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Belge oluşturma için XML yorumları ekleme](../../ide/reference/generate-xml-documentation-comments.md)
- [XML Belgeleri Yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Xml açıklamalarını kullanarak kodunuzu belgele (C# Kılavuzu)](/dotnet/csharp/codedoc)
- [Dile özgü düzenleyici seçeneklerini ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
