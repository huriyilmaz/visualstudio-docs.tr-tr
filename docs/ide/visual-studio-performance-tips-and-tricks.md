---
title: Performansı artırmaya yönelik ipuçları
ms.date: 08/14/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3cd7fe9781048f6612ff6bd81c0bf0cbc00a30b
ms.sourcegitcommit: 9a66f1c31cc9eba0b5231af72da1d18761a9c56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75944214"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Visual Studio performans ipuçları ve püf noktaları

Visual Studio performans önerileri, nadir durumlarda ortaya çıkabilecek düşük bellek durumları için tasarlanmıştır. Bu durumlarda, kullanmadığınız belirli Visual Studio özelliklerini iyileştirebilirsiniz. Aşağıdaki ipuçları genel öneriler olarak tasarlanmamıştır.

> [!NOTE]
> Bellek sorunları nedeniyle ürünü kullanmada zorluk yaşıyorsanız, [geri bildirim aracı](../ide/how-to-report-a-problem-with-visual-studio.md)aracılığıyla bize bilgi verin.

## <a name="use-a-64-bit-os"></a>64 bitlik bir işletim sistemi kullanın

Sisteminizi Windows 'un 32 bitlik bir sürümünden 64 bit sürümüne yükseltirseniz, Visual Studio için kullanılabilir sanal bellek miktarını 2 GB ile 4 GB arasında genişlettirsiniz. Bu, Visual Studio 'Nun 32 bit işlem olmasına rağmen önemli ölçüde daha büyük iş yüklerini işlemesini sağlar.

Daha fazla bilgi için bkz. [bellek sınırları](/windows/desktop/Memory/memory-limits-for-windows-releases) ve [64 bit Windows üzerinde/LARGEADDRESSAWARE kullanma](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Otomatik dosya geri yüklemeyi devre dışı bırak

Visual Studio, önceki oturumda açık kalan belgeleri otomatik olarak yeniden açar. Bu, proje türüne ve açılmakta olan belgelere bağlı olarak, bir çözümü %30 ' a kadar veya daha fazla yüklemeye yönelik zaman alabilir. Windows Forms ve XAML gibi tasarımcıları ve bazı JavaScript ve TypeScript dosyalarını açmak yavaş olabilir.

Otomatik belge geri yükleme bir çözümün önemli ölçüde daha yavaş yüklenmesine neden olduğunda, Visual Studio sizi sarı bir çubukta bilgilendirir. Aşağıdaki adımları izleyerek otomatik dosya yeniden açmayı devre dışı bırakabilirsiniz:

1. **Seçenekler** iletişim kutusunu açmak için **Araçlar** > **Seçenekler** ' i seçin.

1. **Projeler ve çözüm** > **genel** sayfasında, **çözüm yükünden belgeleri yeniden aç**seçimini kaldırın.

Otomatik dosya geri yüklemeyi devre dışı bırakırsanız, açmak istediğiniz dosyalara gitmenin hızlı bir yolu [Şu komutlardan birini](../ide/go-to.md) kullanmaktır:

- **İşlevselliği genel olarak belirlemek** için **Düzenle** ' yi seçin >  > **tümüne gidin**veya **CTRL**+**t**' **e** basın.

- **Düzenle** ** > kullanarak** bir çözümdeki son düzenleme konumuna atlayın > **son düzenleme konumuna gidin**veya **CTRL**+**SHIFT**+**geri**tuşuna basın.

- Bir çözümde son ziyaret edilen dosyaların listesini görmek için **en son dosyayı git** ' i kullanın. **Düzenle** > **Git** ' i seçin > **son dosyaya gidin**veya **CTRL**+**1**, **CTRL**+**R**tuşlarına basın.

## <a name="configure-debugging-options"></a>Hata ayıklama seçeneklerini yapılandırma

Genellikle hata ayıklama oturumları sırasında belleği azaldıysanız, bir veya daha fazla yapılandırma değişikliği yaparak performansı iyileştirebilirsiniz.

- **Yalnızca kendi kodum etkinleştir**

    En basit iyileştirme, yalnızca projeniz için sembolleri yükleyen **yalnızca kendi kodum** özelliğini etkinleştirmektir. Bu özelliğin etkinleştirilmesi, yönetilen uygulamalarda hata ayıklama (.NET) için önemli miktarda bellek kaydedilmesine neden olabilir. Bu seçenek, bazı proje türlerinde varsayılan olarak zaten etkindir.

    **Yalnızca kendi kodum**etkinleştirmek Için, **araçlar** > **Seçenekler** > **hata ayıklama** > **genel**' i seçin ve ardından **yalnızca kendi kodum etkinleştir**' i seçin.

- **Yüklenecek sembolleri belirtin**

    Yerel hata ayıklama için, sembol dosyalarını ( *. pdb*) yüklemek bellek kaynakları açısından pahalıdır. Hata ayıklayıcı sembol ayarlarınızı belleği korumak için yapılandırabilirsiniz. Genellikle, çözümü yalnızca projenizden modülleri yükleyecek şekilde yapılandırırsınız.

    Sembol yüklemeyi belirtmek için **araçlar** > **Seçenekler** > **hata ayıklama** > **semboller**' i seçin.

    Seçenekleri **tüm modüller** yerine **yalnızca belirtilen modüller** olarak ayarlayın ve ardından hangi modülleri yüklemek istediğinizi belirtin. Hata ayıklama sırasında, Ayrıca, simge yüküne bir modül eklemek için **modüller** penceresindeki belirli modüller ' e sağ tıklayabilirsiniz. (Hata ayıklama sırasında pencereyi açmak için **Windows** > **modülleri** > **Hata Ayıkla** ' yı seçin.)

    Daha fazla bilgi için bkz. [sembol dosyalarını anlama](/visualstudio/ide/visual-studio-performance-tips-and-tricks?view=vs-2019).

- **Tanılama Araçları devre dışı bırak**

    Kullandıktan sonra CPU profil oluşturmayı devre dışı bırakmanız önerilir. Bu özellik, büyük miktarlarda kaynak tüketebilir. CPU profili oluşturma etkinleştirildikten sonra, bu durum sonraki hata ayıklama oturumlarında kalıcı hale getirilir, bu nedenle tamamlandığında açıkça devre dışı bırakır. Belirtilen özelliklere ihtiyacınız yoksa hata ayıklarken tanılama araçlarını devre dışı bırakarak bazı kaynakları kaydedebilirsiniz.

    **Tanılama araçları**devre dışı bırakmak için bir hata ayıklama oturumu başlatın, **araçlar** > **Seçenekler** > **Tanılama araçları etkinleştir**' i seçin ve seçeneğin seçimini kaldırın.

    Daha fazla bilgi için bkz. [profil oluşturma araçları](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Araçları ve uzantıları devre dışı bırak

Bazı araçlar veya uzantılar, performansı artırmak için kapatılabilir.

> [!TIP]
> Tek seferde uzantıları kapatarak ve performansı yeniden denetleyerek performans sorunlarını yalıtabilirsiniz.

### <a name="managed-language-service-roslyn"></a>Yönetilen dil hizmeti (Roslyn)

.NET Compiler Platform ("Roslyn") performans konuları hakkında daha fazla bilgi için bkz. [büyük çözümler Için performans konuları](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Tam çözüm analizini devre dışı bırak**

    Visual Studio, bir derlemeyi çağırmadan önce hatalar hakkında zengin bir deneyim sağlamak için tüm çözümünüzün analizini gerçekleştirir. Bu özellik, hataları mümkün olan en kısa sürede belirlemek için faydalıdır. Bununla birlikte, büyük çözümler için bu özellik önemli bellek kaynaklarını kullanabilir. Bellek baskısı veya benzer sorunlar yaşıyorsanız, bu kaynakları boşaltmak için bu deneyimi devre dışı bırakabilirsiniz. Varsayılan olarak bu seçenek, Visual Basic için etkinleştirilmiştir ve için C#devre dışı bırakılır.

    **Tam çözüm analizini**devre dışı bırakmak için **araçlar** > **Seçenekler** > **metin düzenleyici**' yi seçin ve **Visual Basic** ya **C#** da seçeneğini belirleyin. **Gelişmiş** ' i seçin ve **tam çözüm analizini etkinleştir**seçimini kaldırın.

- **CodeLens 'i devre dışı bırak**

    Visual Studio, her yöntemde gösterildiği gibi **tüm başvuruları bul** görevini gerçekleştirir. CodeLens, başvuru sayısının satır içi görüntüsü gibi özellikler sağlar. İş, *Servicehub. RoslynCodeAnalysisService32*gibi ayrı bir işlemde gerçekleştirilir. Büyük çözümlerde veya kaynak kısıtlı sistemlerde, bu özellik performans üzerinde önemli bir etkiye sahip olabilir. Örneğin, 4 GB 'lik bir makineye büyük bir çözüm yüklerken veya bu işlem için yüksek CPU kullanımı gibi bellek sorunları yaşıyorsanız, kaynakları boşaltmak için CodeLens 'i devre dışı bırakabilirsiniz.

    **CodeLens**'i devre dışı bırakmak için **araçlar** > **Seçenekler** > **metin düzenleyici** ' yi > **tüm diller** > **CodeLens**' i seçin ve özelliğin seçimini kaldırın.

    > [!NOTE]
    > CodeLens, Visual Studio 'nun Professional ve Enterprise sürümlerinde kullanılabilir.

### <a name="other-tools-and-extensions"></a>Diğer araçlar ve uzantılar

- **Uzantıları devre dışı bırak**

    Uzantılar, Visual Studio 'ya eklenen ve yeni işlevsellik sağlayan veya mevcut işlevselliği genişleten ek yazılım bileşenleridir. Uzantılar, genellikle bir bellek kaynağı sorunları kaynağı olabilir. Bellek kaynağı sorunları yaşıyorsanız, bu senaryonun senaryoyu veya iş akışını nasıl etkilediğini görmek için uzantıları tek seferde devre dışı bırakmayı deneyin.

   ::: moniker range="vs-2017"

    Uzantıları devre dışı bırakmak için **araçlar** > **Uzantılar ve güncelleştirmeler**' e gidin ve belirli bir uzantıyı devre dışı bırakın.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Uzantıları devre dışı bırakmak **için uzantılara gidin** > **uzantıları yönetin**ve belirli bir uzantıyı devre dışı bırakın.

   ::: moniker-end

- **XAML Tasarımcısı devre dışı bırak**

    XAML Tasarımcısı varsayılan olarak etkindir, ancak yalnızca bir *. xaml* dosyası açarsanız kaynakları tüketir. XAML dosyaları ile çalışıyorsanız ancak tasarımcı işlevselliğini kullanmak istemiyorsanız, bazı belleği boşaltmak için bu özelliği devre dışı bırakın.

    **XAML Tasarımcısı**devre dışı bırakmak için **araçlar** > **Seçenekler** > **XAML Tasarımcısı** > **Etkinleştir**' e gidin ve seçeneğin seçimini kaldırın.

- **İş yüklerini kaldır**

    Artık kullanılmayan iş yüklerini kaldırmak için Visual Studio Yükleyicisi kullanabilirsiniz. Bu eylem, artık gerekli olmayan paketleri ve derlemeleri atlayarak başlangıç ve çalışma zamanı maliyetini kolaylaştırabilir.

## <a name="force-a-garbage-collection"></a>Çöp toplamayı zorla

CLR bir atık toplama bellek yönetim sistemi kullanır. Bu sistemde, bazı durumlarda bellek artık gerekli olmayan nesneler tarafından kullanılır. Bu durum geçicidir; Çöp toplayıcı bu belleği, performans ve kaynak kullanımı buluşsal yöntemlerini temel alarak yayımlayacaktır. CLR 'yi, Visual Studio 'da bir kısayol kullanarak kullanılmayan herhangi bir belleği toplamaya zorlayabilirsiniz. Koleksiyon için önemli miktarda çöp bekleniyor ve bir çöp toplama işlemi zorlarsanız, **Görev Yöneticisi**'nde *devenv. exe* işlem bırakması bellek kullanımını görmeniz gerekir. Bu yöntemin kullanılması nadiren gereklidir. Ancak, pahalı bir işlem tamamlandıktan sonra (tam derleme, hata ayıklama oturumu veya çözüm açma olayı gibi), işlem tarafından gerçekten ne kadar bellek kullanıldığını belirlemenize yardımcı olabilir. Visual Studio karışık olduğundan (yerel olarak yönetilen &), doğal ayırıcı ve çöp toplayıcısının sınırlı bellek kaynakları için rekabet halinde olması olasıdır. Yüksek bellek kullanımı koşulları altında çöp toplayıcısının çalışmasına zorlamaya yardımcı olabilir.

Çöp toplamayı zorlamak için kısayol tuşlarını kullanın: **ctrl**+**alt**+**shıft**+**f12**, **CTRL**+**alt**+**SHIFT**+**F12** (iki kez bas).

Çöp toplamayı güvenilir bir şekilde zorlamak senaryonuzu çalışır hale getirmek, bu davranışın bir hata olması nedeniyle Visual Studio geri bildirim aracı aracılığıyla bir rapor dosyaluyor.

CLR Atık toplayıcısının ayrıntılı bir açıklaması için bkz. [çöp toplamanın temelleri](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio performansını iyileştirme](../ide/optimize-visual-studio-performance.md)
- [Çözümleri daha hızlı yükle (Visual Studio blogu)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
