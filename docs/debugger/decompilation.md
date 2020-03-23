---
title: Hata ayıklama yaparken .NET kodunu decompile | Microsoft Dokümanlar
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508751"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Hata ayıklama sırasında .NET derlemelerinden kaynak kodu oluşturma

Bir .NET uygulamasını hata ayıklarken, sahip olmadığınız kaynak kodunu görüntülemek istediğinizi görebilirsiniz. Örneğin, bir özel durum kırma veya kaynak bir konuma gitmek için arama yığını nı kullanma.

> [!NOTE]
> * Kaynak kodu oluşturma (decompilation) sadece .NET uygulamaları için kullanılabilir ve açık kaynak [ILSpy](https://github.com/icsharpcode/ILSpy) projeye dayanmaktadır.
> * Decompilation sadece Visual Studio 2019 16.5 ve sonraki yıllarda mevcuttur.
> * [SuppressIldasmAttribute'in](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) bir derlemeye veya modüle uygulanması Visual Studio'nun derleme girişiminde bulunmasını engeller.

## <a name="generate-source-code"></a>Kaynak kodu oluşturma

Hata ayıklama yaparken ve kaynak kodu yoksa, Visual Studio **Kaynak Bulunamadı** belgesini veya derleme için semboller yoksa, Sembol **Yüklemeyok** belgeyi gösterir. Her iki belgede de geçerli konum için C# kodu oluşturan bir **Decompile kaynak kodu** seçeneği vardır. Oluşturulan C# kodu diğer kaynak kodları gibi kullanılabilir. Kodu görüntüleyebilir, değişkenleri inceleyebilir, kesme noktaları ayarlayabilirsiniz.

### <a name="no-symbols-loaded"></a>Yüklü sembol yok

Aşağıdaki resimde **Sembol Yüklemeyok iletisi** gösterilmektedir.

![Sembol yüklü belgenin ekran görüntüsü](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Kaynak bulunamadı

Aşağıdaki resimde **Kaynak Bulunamadı** iletisi gösterilmektedir.

![Kaynak belgesi bulunamadı belgenin ekran görüntüsü](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Derleme için kaynak oluşturma ve gömme

Belirli bir konum için kaynak kodu oluşturmaya ek olarak, belirli bir .NET derlemesi için tüm kaynak kodu oluşturabilirsiniz. Bunu yapmak **için, Modüller** penceresine ve .NET derlemesinin bağlam menüsünden gidin ve ardından **Decompile kaynak kodu** komutunu seçin. Visual Studio derleme için bir sembol dosyası oluşturur ve sonra kaynağı sembol dosyasına yerzetir. Daha sonraki bir adımda, katıştirilen kaynak kodunu [ayıklayabilirsiniz.](#extract-and-view-the-embedded-source-code)

![Decompile kaynak komutu ile modüller penceresinde derleme bağlam menüsünün ekran görüntüsü.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Gömülü kaynak kodunu ayıklayın ve görüntüleyin

**Modüller** penceresinin bağlam menüsündeki **Kaynak Kodu** Komutunu kullanarak bir sembol dosyasına katışdırılmış kaynak dosyaları ayıklayabilirsiniz.

![Ayıklama kaynakları komutu ile modüller penceresinde derleme bağlam menüsünün ekran görüntüsü.](media/decompilation-extract-source-code.png)

Çıkarılan kaynak dosyaları çeşitli [dosyalar](../ide/reference/miscellaneous-files.md)olarak çözüme eklenir. Çeşitli dosyalar özelliği Visual Studio'da varsayılan olarak kapalıdır. Bu **özelliği, Çözüm** > Gezgini onay kutusundaki Çeşitli dosyaları Gösteren Araçlar**Seçenekleri** > **Ortamı** > **Belgeleri'nden** > **Show Miscellaneous files in Solution Explorer** etkinleştirebilirsiniz. Bu özelliği etkinleştirmeden, ayıklanan kaynak kodunu açamazsınız.

![Çeşitli dosyalar seçeneği etkin araçlar seçeneği sayfasının ekran görüntüsü.](media/decompilation-tools-options-misc-files.png)

Çıkarılan kaynak dosyaları **Çözüm Gezgini'ndeki**çeşitli dosyalarda görünür.

![Çeşitli dosyaları ile çözüm explorer ekran görüntüsü.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Bilinen sınırlamalar

### <a name="requires-break-mode"></a>Kesme modu gerektirir

Decompilation kullanarak kaynak kodu oluşturma yalnızca hata ayıklama kesme modunda olduğunda ve uygulama duraklatılmış olduğunda mümkündür. Örneğin, Visual Studio bir kesme noktasına veya bir özel duruma ulaştığında kesme moduna girer. **Tümlerini Kır (Tüm** simgeyi![](media/decompilation-break-all.png)kır) komutunu kullanarak kodunuzu bir sonraki çalıştığında kırmak için Visual Studio'yu kolayca tetikleyebilirsiniz.

### <a name="decompilation-limitations"></a>Derleme sınırlamaları

.NET derlemelerinde kullanılan ara biçimden (IL) kaynak kodu oluşturmanın bazı içsel sınırlamaları vardır. Bu nedenle, oluşturulan kaynak kodu özgün kaynak kodu gibi görünmüyor. Farklılıkların çoğu, özgün kaynak kodundaki bilgilerin çalışma zamanında gerekli olmadığı yerlerdedir. Örneğin, çalışma zamanında beyaz alan, açıklamalar ve yerel değişkenlerin adları gibi bilgilere gerek yoktur. Özgün kaynak kodunun yerine değil, programın nasıl yürütüldettiğini anlamak için oluşturulan kaynağı kullanmanızı öneririz.

### <a name="debug-optimized-or-release-assemblies"></a>Hata ayıklama optimize veya sürüm derlemeleri

Derleyici optimizasyonları kullanılarak derlenen bir derlemeden derlenen kodu ayıklarken aşağıdaki sorunlarla karşılaşabilirsiniz:
- Kesme noktaları her zaman eşleşen kaynak konumuna bağlanmayabilir.
- Stepping her zaman doğru konuma adım olmayabilir.
- Yerel değişkenlerin doğru adları olmayabilir.
- Bazı değişkenler değerlendirme için kullanılamayabilir.

Daha fazla bilgi GitHub sayısında bulunabilir: [VS Debugger icSharpCode.Decompiler entegrasyonu](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Decompilation güvenilirlik

Decompilation girişimleri nispeten küçük bir yüzdesi başarısızlığa neden olabilir. Bu ILSpy bir sıra noktası null-referans hatası kaynaklanmaktadır.  Bu sorunları yakalayarak ve derleme girişimini incelikle başarısız lığa uğratarak başarısızlığı hafifletmiş olduk.

Daha fazla bilgi GitHub sayısında bulunabilir: [VS Debugger icSharpCode.Decompiler entegrasyonu](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Async kodu ile sınırlamalar

Async/await kod desenli modüllerin derlenmesinin sonuçları eksik veya tamamen başarısız olabilir. Async / await ve verim devlet makineleri ILSpy uygulaması sadece kısmen uygulanır. 

Daha fazla bilgi GitHub sayısında bulunabilir: [PDB Jeneratör Durumu](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Yalnızca Kendi Kodum

[Just My Code (JMC)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) ayarları Visual Studio'nun sistem, çerçeve, kitaplık ve diğer kullanıcı dışı çağrıları aşmasını sağlar. Hata ayıklama oturumu **sırasında, Modüller** penceresi hata ayıklayıcının Kodum (kullanıcı kodu) olarak hangi kod modüllerini davrandığını gösterir.

Optimize edilmiş veya serbest bırakma modüllerinin decompilation kullanıcı kodu üretir. Hata ayıklayıcı, derlenmiş kullanıcı olmayan kodunuzda kırılırsa( örneğin Kaynak **Yok** penceresi görüntülenir. Yalnızca Kodumu devre dışı kalmak için,**Genel**Hata **Ayıklama** > > **Araçlar** > **Seçenekleri'ne** (veya **Hata Ayıklama** > **Seçenekleri)'ne**gidin ve ardından Yalnızca **Kodumu Etkinleştir'i**seçin.

### <a name="extracted-sources"></a>Çıkarılan kaynaklar

Bir derlemeden çıkarılan kaynak kodu aşağıdaki sınırlamaları vardır:
- Oluşturulan dosyaların adı ve konumu yapılandırılamaz.
- Dosyalar geçicidir ve Visual Studio tarafından silinir.
- Dosyalar tek bir klasöre yerleştirilir ve özgün kaynakların sahip olduğu klasör hiyerarşisi kullanılmaz.
- Her dosyanın dosya adı, dosyanın bir denetim karma sını içerir.

### <a name="generated-code-is-c-only"></a>Oluşturulan kod yalnızca C#
Decompilation yalnızca C#'da kaynak kodu dosyaları oluşturur. Başka bir dilde dosya oluşturmak için bir seçenek yoktur.
