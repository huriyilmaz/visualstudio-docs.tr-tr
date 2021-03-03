---
title: Performansı artırmaya yönelik ipuçları
description: Performansı artırmaya yardımcı olmak için kullanmadığınız belirli Visual Studio özelliklerini iyileştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e2187426fbd2e8892d41672c1cf682ed0b93592
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683766"
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

1.   >  **Seçenekler** iletişim kutusunu açmak için Araçlar **seçeneklerini** belirleyin.

1. **Projeler ve çözüm**  >  **genel** sayfasında, **çözüm yükünden belgeleri yeniden aç** seçimini kaldırın.

Otomatik dosya geri yüklemeyi devre dışı bırakırsanız, açmak istediğiniz dosyalara gitmenin hızlı bir yolu [Şu komutlardan birini](../ide/go-to.md) kullanmaktır:

- İşlevlere genel **Git** ' **i seçerek**  >    >  **Tümünü git**' i seçin veya **CTRL** + **T**' ye basın.

- **Düzenle** git ' i kullanarak bir çözümdeki son düzenleme konumuna atlayın  >    >  ve **son düzenleme konumuna gidin** veya **CTRL** + **SHIFT** + **Backspace** tuşuna basın.

- Bir çözümde son ziyaret edilen dosyaların listesini görmek için **en son dosyayı git** ' i kullanın.   >    >  **Son dosyaya gitmek** için Düzenle git ' i seçin veya **CTRL** + **1**, **CTRL** + **R** tuşlarına basın.

## <a name="configure-debugging-options"></a>Hata ayıklama seçeneklerini yapılandırma

Genellikle hata ayıklama oturumları sırasında belleği azaldıysanız, bir veya daha fazla yapılandırma değişikliği yaparak performansı iyileştirebilirsiniz.

- **Yalnızca kendi kodum etkinleştir**

    En basit iyileştirme, yalnızca projeniz için sembolleri yükleyen **yalnızca kendi kodum** özelliğini etkinleştirmektir. Bu özelliğin etkinleştirilmesi, yönetilen uygulamalarda hata ayıklama (.NET) için önemli miktarda bellek kaydedilmesine neden olabilir. Bu seçenek, bazı proje türlerinde varsayılan olarak zaten etkindir.

    **Yalnızca kendi kodum** etkinleştirmek için **Araçlar**  >  **Seçenekler**  >  **Genel hata ayıklama**  >  ' ı seçin ve ardından **yalnızca kendi kodum etkinleştir**' i seçin.

- **Yüklenecek sembolleri belirtin**

    Yerel hata ayıklama için, sembol dosyalarını (*. pdb*) yüklemek bellek kaynakları açısından pahalıdır. Hata ayıklayıcı sembol ayarlarınızı belleği korumak için yapılandırabilirsiniz. Genellikle, çözümü yalnızca projenizden modülleri yükleyecek şekilde yapılandırırsınız.

    Sembol yüklemeyi belirtmek için **Araçlar**  >  **Seçenekler**  >  **hata ayıklama**  >  **sembolleri**' ni seçin.

    Seçenekleri **tüm modüller** yerine **yalnızca belirtilen modüller** olarak ayarlayın ve ardından hangi modülleri yüklemek istediğinizi belirtin. Hata ayıklama sırasında, Ayrıca, simge yüküne bir modül eklemek için **modüller** penceresindeki belirli modüller ' e sağ tıklayabilirsiniz. (Hata ayıklarken pencereyi açmak için **Hata Ayıkla**  >  ' yı seçin. **Windows**  >  **Modüller**.)

    Daha fazla bilgi için bkz. [sembol dosyalarını anlama](?view=vs-2019&preserve-view=true).

- **Tanılama Araçları devre dışı bırak**

    Kullandıktan sonra CPU profil oluşturmayı devre dışı bırakmanız önerilir. Bu özellik, büyük miktarlarda kaynak tüketebilir. CPU profili oluşturma etkinleştirildikten sonra, bu durum sonraki hata ayıklama oturumlarında kalıcı hale getirilir, bu nedenle tamamlandığında açıkça devre dışı bırakır. Belirtilen özelliklere ihtiyacınız yoksa hata ayıklarken tanılama araçlarını devre dışı bırakarak bazı kaynakları kaydedebilirsiniz.

    **Tanılama araçları** devre dışı bırakmak için bir hata ayıklama oturumu başlatın,   >  genel olarak hata ayıklama Araçlar **seçeneklerini** belirleyin  >    >  ve ardından **hata ayıklama sırasında tanılama araçları etkinleştir** seçeneğini kaldırın.

    Daha fazla bilgi için bkz. [profil oluşturma araçları](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Araçları ve uzantıları devre dışı bırak

Bazı araçlar veya uzantılar, performansı artırmak için kapatılabilir.

> [!TIP]
> Tek seferde uzantıları kapatarak ve performansı yeniden denetleyerek performans sorunlarını yalıtabilirsiniz.

### <a name="managed-language-service-roslyn"></a>Yönetilen dil hizmeti (Roslyn)

.NET Compiler Platform ("Roslyn") performans konuları hakkında daha fazla bilgi için bkz. [büyük çözümler Için performans konuları](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

- **Tam çözüm analizini devre dışı bırak**

    Visual Studio, bir derlemeyi çağırmadan önce hatalar hakkında zengin bir deneyim sağlamak için tüm çözümünüzün analizini gerçekleştirir. Bu özellik, hataları mümkün olan en kısa sürede belirlemek için faydalıdır. Bununla birlikte, büyük çözümler için bu özellik önemli bellek kaynaklarını kullanabilir. Bellek baskısı veya benzer sorunlar yaşıyorsanız, bu kaynakları boşaltmak için bu deneyimi devre dışı bırakabilirsiniz. Varsayılan olarak, bu seçenek Visual Basic için etkinleştirilmiştir ve C# için devre dışı bırakılır.

    **Tam çözüm analizini** devre dışı bırakmak için **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**' yi seçin ve **Visual Basic** veya **C#**' ı seçin. **Gelişmiş** ' i seçin ve **tam çözüm analizini etkinleştir** seçimini kaldırın.

- **CodeLens 'i devre dışı bırak**

    Visual Studio, her yöntemde gösterildiği gibi **tüm başvuruları bul** görevini gerçekleştirir. CodeLens, başvuru sayısının satır içi görüntüsü gibi özellikler sağlar. İş, *Servicehub. RoslynCodeAnalysisService32* gibi ayrı bir işlemde gerçekleştirilir. Büyük çözümlerde veya kaynak kısıtlı sistemlerde, bu özellik performans üzerinde önemli bir etkiye sahip olabilir. Örneğin, 4 GB 'lik bir makineye büyük bir çözüm yüklerken veya bu işlem için yüksek CPU kullanımı gibi bellek sorunları yaşıyorsanız, kaynakları boşaltmak için CodeLens 'i devre dışı bırakabilirsiniz.

    **CodeLens**'i devre dışı bırakmak için **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **tüm diller**  >  **CodeLens**' i seçin ve özelliğin seçimini kaldırın.

    > [!NOTE]
    > CodeLens, Visual Studio 'nun Professional ve Enterprise sürümlerinde kullanılabilir.

### <a name="other-tools-and-extensions"></a>Diğer araçlar ve uzantılar

- **Uzantıları devre dışı bırak**

    Uzantılar, Visual Studio 'ya eklenen ve yeni işlevsellik sağlayan veya mevcut işlevselliği genişleten ek yazılım bileşenleridir. Uzantılar, genellikle bir bellek kaynağı sorunları kaynağı olabilir. Bellek kaynağı sorunları yaşıyorsanız, bu senaryonun senaryoyu veya iş akışını nasıl etkilediğini görmek için uzantıları tek seferde devre dışı bırakmayı deneyin.

   ::: moniker range="vs-2017"

    Uzantıları devre dışı bırakmak için **Araçlar** > **Uzantılar ve güncelleştirmeler**' e gidin ve belirli bir uzantıyı devre dışı bırakın.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Uzantıları devre dışı bırakmak **için Uzantılar** > **Uzantıları Yönet**' e gidin ve belirli bir uzantıyı devre dışı bırakın.

   ::: moniker-end

- **Harita modunu devre dışı bırak**

    [**Harita modu**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) , kod satırlarını, kaydırma çubuğunda küçük olarak görüntüler. Eşleme modu varsayılan olarak etkindir.

    Harita modunu devre dışı bırakmak için, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **tüm diller**  >  **kaydırma çubukları**' na gidin ve **davranış** bölümünde **Dikey kaydırma çubuğu için eşleme modunu kullan** seçeneğini kaldırın.

- **Sözcük kaydırmayı devre dışı bırak**

    [**Sözcük kaydırması**](./reference/how-to-manage-word-wrap-in-the-editor.md) , kod Düzenleyicisi penceresinin geçerli genişliğinin ötesinde uzun bir kod satırının bölümünü görüntüler. Sözcük kaydırması varsayılan olarak açık.

    Üzerinde çalışmakta olduğunuz bir proje için sözcük kaydırmayı devre dışı bırakmak için   >  **Gelişmiş**  >  **sözcük kaydırmayı** Düzenle ' ye gidin. (Aynı menü komutlarını kullanarak bu ayarı değiştirebilirsiniz.)

    Tüm projeler için sözcük kaydırmayı devre dışı bırakmak için, **Araçlar**  >  **Seçenekler**  >  **genel**  >  **metin Düzenleyicisi**  >  **tüm diller**  >  **genel**' e gidin ve **Ayarlar** bölümünde, **sözcük kaydır** seçeneğinin seçimini kaldırın.

- **XAML Tasarımcısı devre dışı bırak**

    XAML Tasarımcısı varsayılan olarak etkindir, ancak yalnızca bir *. xaml* dosyası açarsanız kaynakları tüketir. XAML dosyaları ile çalışıyorsanız ancak tasarımcı işlevselliğini kullanmak istemiyorsanız, bazı belleği boşaltmak için bu özelliği devre dışı bırakın.

    XAML Tasarımcısı devre dışı bırakmak için,   >    >    >  **XAML Tasarımcısı etkinleştirmek** XAML Tasarımcısı Araçlar Seçenekler ' e gidin ve seçeneğin seçimini kaldırın.

- **İş yüklerini kaldır**

    Artık kullanılmayan iş yüklerini kaldırmak için Visual Studio Yükleyicisi kullanabilirsiniz. Bu eylem, artık gerekli olmayan paketleri ve derlemeleri atlayarak başlangıç ve çalışma zamanı maliyetini kolaylaştırabilir.

- **Yerel. gitignore 'e izlenmeyen dosyalar ekleyin**

    Visual Studio, `git status` bir depoya yeni dosyalar eklediğinizde sorunsuz bir deneyim sağlamak Için Git komutunu izlenmeyen dosyalarla çalıştırır. İzlenmeyen dosya sayısı çok `git status` fazla olduğunda fazla bellek kullanabilir. Bu dosyaları yoksaymak ve performansını geliştirmek için `git status` Bu dosya veya klasörleri Local. gitignore dosyanıza ekleyebilirsiniz. Dosyaya erişmek **için git**  >  **ayarları**  >  **Git deposu ayarları**' na gidin. Ardından, **Git dosyaları** bölümünde, **Ekle** ' ye tıklayarak bir. gitignore dosyası oluşturun veya zaten varsa **Düzenle** ' yi tıklatın.

## <a name="force-a-garbage-collection"></a>Çöp toplamayı zorla

CLR bir atık toplama bellek yönetim sistemi kullanır. Bu sistemde, bazı durumlarda bellek artık gerekli olmayan nesneler tarafından kullanılır. Bu durum geçicidir; Çöp toplayıcı bu belleği, performans ve kaynak kullanımı buluşsal yöntemlerini temel alarak yayımlayacaktır. CLR 'yi, Visual Studio 'da bir kısayol kullanarak kullanılmayan herhangi bir belleği toplamaya zorlayabilirsiniz. Koleksiyon için önemli miktarda çöp bekleniyor ve bir çöp toplama işlemi zorlarsanız, **Görev Yöneticisi**'nde *devenv.exe* işlem bırakma bellek kullanımını görmeniz gerekir. Bu yöntemin kullanılması nadiren gereklidir. Ancak, pahalı bir işlem tamamlandıktan sonra (tam derleme, hata ayıklama oturumu veya çözüm açma olayı gibi), işlem tarafından gerçekten ne kadar bellek kullanıldığını belirlemenize yardımcı olabilir. Visual Studio karışık olduğundan (yerel olarak yönetilen &), doğal ayırıcı ve çöp toplayıcısının sınırlı bellek kaynakları için rekabet halinde olması olasıdır. Yüksek bellek kullanımı koşulları altında çöp toplayıcısının çalışmasına zorlamaya yardımcı olabilir.

Çöp toplamayı zorlamak için kısayol tuşunu kullanın: **CTRL** + **alt** + **SHIFT** + **F12**, **CTRL** + **alt** + **SHIFT** + **F12** (iki kez basın).

Çöp toplamayı güvenilir bir şekilde zorlamak senaryonuzu çalışır hale getirmek, bu davranışın bir hata olması nedeniyle Visual Studio geri bildirim aracı aracılığıyla bir rapor dosyaluyor.

CLR Atık toplayıcısının ayrıntılı bir açıklaması için bkz. [çöp toplamanın temelleri](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio performansını iyileştirme](../ide/optimize-visual-studio-performance.md)
- [Çözümleri daha hızlı yükle (Visual Studio blogu)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)