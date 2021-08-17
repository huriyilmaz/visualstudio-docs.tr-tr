---
title: İpuçları geliştirmek için
description: Performansı geliştirmeye yardımcı olmak Visual Studio bazı özelikleri iyileştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ef6452ffcf86875946a1d5092f61f53ef6257eee53146617e28b34ff4ce27f18
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386556"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Visual Studio ipuçları ve püf noktaları

Visual Studio performans önerileri, nadir durumlarda ortaya çıkabilir düşük bellek durumlarını hedeflemektedir. Bu gibi durumlarda, kullanmay bazı Visual Studio özellikleri en iyi duruma getirmenizi sağlar. Aşağıdaki ipuçları genel öneriler olarak amaçlanmaz.

> [!NOTE]
> Bellek sorunları nedeniyle ürünü kullanmada zorlukyla karşı karşımıza geçiyorsanız geri bildirim aracı aracılığıyla bize [bildirin.](../ide/how-to-report-a-problem-with-visual-studio.md)

## <a name="use-a-64-bit-os"></a>64 bit işletim sistemi kullanma

Sisteminizi 32 bitlik bir Windows sürümünden 64 bit sürüme yükseltersiniz, Visual Studio için kullanılabilir sanal bellek miktarını 2 GB'tan 4 GB'a genişletebilirsiniz. Bu, Visual Studio 32 bitlik bir işlem olsa bile önemli ölçüde daha büyük iş yüklerini işlemeye olanak sağlar.

Daha fazla bilgi için [bkz. Bellek sınırları](/windows/desktop/Memory/memory-limits-for-windows-releases) ve 64 bit veya üzerinde [/LARGEADDRESSAWARE Windows.](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/)

## <a name="disable-automatic-file-restore"></a>Otomatik dosya geri yüklemesini devre dışı bırakma

Visual Studio oturumda açık kalan belgeleri otomatik olarak yeniden açar. Bu, proje türüne ve açılan belgelere bağlı olarak bir çözümün yüklenme süresini %30 veya daha fazla uzatılabilir. Windows Forms ve XAML gibi tasarımcıların ve bazı JavaScript ve typescript dosyalarının açılması yavaş olabilir.

Visual Studio otomatik belge geri yüklemesi bir çözümün önemli ölçüde daha yavaş yüklemesini neden olduğunda sarı çubukta size bunu size iletir. Aşağıdaki adımları kullanarak otomatik dosya yeniden açma özelliğini devre dışı abilirsiniz:

1. Seçenekler **iletişim**  >  **kutusunu** açmak için Araçlar **Seçenekleri'ne** tıklayın.

1. Projeler ve **Çözüm Genel**  >  **sayfasında,** Çözüm yükü üzerinde belgeleri **yeniden aç'ın seçimini kaldırın.**

Otomatik dosya geri yükleme özelliğini devre dışı bırakmanız, açmak istediğiniz dosyalara gitmenin hızlı bir yolu Git komutlarından [birini kullanmaktır:](../ide/go-to.md)

- Genel Git işlevi **için Düzenle Tüm** Git'e   >  **Git'i** seçin  >  **veya** Ctrl T  + **tuşlarına basın.**

- Düzenle'yi Kullanarak Son Düzenleme Konuma Git veya Ctrl Shift Geri Al tuşlarına basarak çözümde son  >    >   **düzenleme** +  + **konuma atlayın.**

- Bir **çözümde son ziyaret edilen** dosyaların listesini görmek için Son Dosyaya Git'i kullanın. Son **Dosyaya**  >  **Gitmek için**  >  **Düzenle'yi seçin veya** **Ctrl 1**, + **Ctrl** R  + **tuşlarına basın.**

## <a name="configure-debugging-options"></a>Hata ayıklama seçeneklerini yapılandırma

Hata ayıklama oturumları sırasında genellikle yetersiz bellek yapıyorsanız, bir veya daha fazla yapılandırma değişikliği yaparak performansı en iyi duruma getirmeniz gerekir.

- **Yalnızca kendi kodum**

    En basit iyileştirme, yalnızca **projeniz için Yalnızca kendi kodum** yük devre dışı özelliğini etkinleştirmektir. Bu özelliğin etkinleştirilmesi, yönetilen uygulamalarda (.NET) hata ayıklama için önemli bir bellek tasarrufuna neden olabilir. Bu seçenek bazı proje türlerinde varsayılan olarak zaten etkindir.

    Bunu etkinleştirmek **Yalnızca kendi kodum,** Araçlar Seçenekleri **Hata** Ayıklama  >    >  **Genel'i**  >  **seçin** ve ardından Etkinleştir'i **Yalnızca kendi kodum.**

- **Yük için sembolleri belirtme**

    Yerel hata ayıklama için, sembol dosyalarının (*.pdb*) yüklenmesi bellek kaynakları açısından pahalıdır. Bellek tasarrufu yapmak için hata ayıklayıcı sembol ayarlarınızı yapılandırabilirsiniz. Genellikle, çözümü yalnızca projenizin modüllerini yüklemek için yapılandırabilirsiniz.

    Sembol yüklemesini belirtmek için Araçlar Seçenekler **Hata**  >  **Ayıklama**  >  **Sembolleri'ne**  >  **tıklayın.**

    Seçenekleri Tüm **modüller yerine Yalnızca belirtilen** **modüller olarak** ayarlayın ve ardından yüklemek istediğiniz modülleri belirtin. Hata ayıklama sırasında modül yükleme simgesine açıkça  bir modül eklemek için Modüller penceresinde belirli modüllere sağ tıklarsınız. (Hata ayıklama sırasında pencereyi açmak için Hata **Ayıkla'ya tıklayın**  >  **Windows**  >  **Modüller**.)

    Daha fazla bilgi için [bkz. Sembol dosyalarını anlama.](?view=vs-2019&preserve-view=true)

- **Devre dışı Tanılama Araçları**

    Kullandıktan sonra CPU profili oluşturmayı devre dışı bırakmanız önerilir. Bu özellik büyük miktarlarda kaynak tüketir. CPU profili oluşturma etkinleştirildikten sonra, bu durum sonraki hata ayıklama oturumlarında kalıcı olur, bu nedenle bittiğinde açıkça kapatmaya değer. Sağlanan özelliklere ihtiyacınız yoksa hata ayıklama sırasında tanılama araçlarını devre dışı bırakarak bazı kaynakları kaydedebilirsiniz.

    Hata ayıklama **Tanılama Araçları** devre dışı bırakmak için, Araçlar Seçenekler Hata Ayıklama Genel'i seçin ve hata ayıklama sırasında Tanılama Araçları  >    >    >   **seçeneğinin seçimini** kaldırın.

    Daha fazla bilgi için [bkz. Profil Oluşturma Araçları.](../profiling/profiling-feature-tour.md)

## <a name="disable-tools-and-extensions"></a>Araçları ve uzantıları devre dışı bırakma

Performansı artırmak için bazı araçlar veya uzantılar kapatabilirsiniz.

> [!TIP]
> Genellikle uzantıları tek tek kapatarak ve performansı yeniden kontrol etmekle performans sorunlarını yalıtabilirsiniz.

### <a name="managed-language-service-roslyn"></a>Yönetilen dil hizmeti (Roslyn)

Performans değerlendirmeleri .NET Compiler Platform ("Roslyn") hakkında daha fazla bilgi için bkz. Büyük çözümler için [performansla ilgili dikkat edilmesi gerekenler.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)

- **Tam çözüm analizini devre dışı bırakma**

    Visual Studio derlemeyi faturalamadan önce hatalar hakkında zengin bir deneyim sağlamak için tüm çözümünüz üzerinde analiz gerçekleştirir. Bu özellik hataları mümkün olan en kısa sürede belirlemek için kullanışlıdır. Ancak, büyük çözümler için bu özellik önemli miktarda bellek kaynağı tüketir. Bellek baskısı veya benzer sorunlar yaşıyorsanız bu kaynakları serbest bırakmak için bu deneyimi devre dışı abilirsiniz. Varsayılan olarak, bu seçenek C# için Visual Basic ve devre dışı bırakılmıştır.

    Tam Çözüm **Analizi'ni devre dışı** bırakmak için **Araçlar**  >  **Seçenekler**  >  **Metin Düzenleyicisi'ni** seçin ve ardından **Visual Basic** **veya C# seçin.** **Gelişmiş'i** seçin ve Tam **çözüm analizini etkinleştir'in seçimini kaldırın.**

- **CodeLens'i devre dışı bırakma**

    Visual Studio her **yöntemde görüntülenirken** bir Tüm Başvuruları Bul görevini gerçekleştirir. CodeLens, başvuru sayısının satır içi görüntüsü gibi özellikler sağlar. Çalışma *ServiceHub.RoslynCodeAnalysisService32* gibi ayrı bir işlemde gerçekleştirilir. Büyük çözümlerde veya kaynak kısıtlı sistemlerde bu özellik performans üzerinde önemli bir etkisi olabilir. Örneğin, 4 GB'lık bir makineye büyük bir çözüm yüklerken veya bu işlem için yüksek CPU kullanımı sırasında bellek sorunlarıyla karşılaşıyorsanız, kaynakları boşaltmak için CodeLens'i devre dışı indirebilirsiniz.

    **CodeLens'i devre** dışı bırakmak **için Araçlar**  >  **Seçenekler** Metin  >  **Düzenleyici** Tüm  >  **Diller**  >  **CodeLens** seçeneğini belirleyin ve özelliğin seçimini kaldırın.

    > [!NOTE]
    > CodeLens, Professional ve Enterprise sürümlerinde Visual Studio.

### <a name="other-tools-and-extensions"></a>Diğer araçlar ve uzantılar

- **Uzantıları Devre Dışı Bırakma**

    Uzantılar, yeni işlevsellik Visual Studio mevcut işlevselliği genişleten ek yazılım bileşenleridir. Uzantılar genellikle bellek kaynağı sorunları kaynağı olabilir. Bellek kaynağı sorunlarıyla karşılaşıyorsanız, senaryoyu veya iş akışını nasıl etkile olduğunu görmek için uzantıları tek tek devre dışı bırakmayı deneyin.

   ::: moniker range="vs-2017"

    Uzantıları devre dışı bırakmak için Araçlar Uzantıları **ve** > **Güncelleştirmeler'e gidin ve** belirli bir uzantıyı devre dışı bırakma.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Uzantıları devre dışı bırakmak için Uzantılar **Uzantıları** > **Yönet'e gidin ve** belirli bir uzantıyı devre dışı bırakma.

   ::: moniker-end

- **Eşleme modunu devre dışı bırakma**

    [**Harita modu,**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) kaydırma çubuğunda kod satırlarını görüntüler. Eşleme modu varsayılan olarak etkindir.

    Harita modunu devre dışı bırakmak için Araçlar Seçenekler Metin Düzenleyici Tüm Diller Kaydırma Çubukları 'ne gidin ve Davranış bölümünde Dikey kaydırma çubuğu için harita modunu kullan  >    >    >    >   **seçeneğinin seçimini** kaldırın. 

- **Sözcük kaydırmayı devre dışı bırakma**

    [**Sözcük kaydırma,**](./reference/how-to-manage-word-wrap-in-the-editor.md) kod düzenleyicisi penceresinin geçerli genişliğinin ötesine genişleten uzun bir kod satırı bölümünü görüntüler. Sözcük kaydırma varsayılan olarak açıktır.

    Üzerinde çalışmakta olan bir proje için sözcük kaydırmayı devre dışı bırakmak için Gelişmiş Sözcük   >  **Kaydırmayı**  >  **Düzenle'ye gidin.** (Aynı menü komutlarını kullanarak bu ayarı iki durumlu yapabilirsiniz.)

    Tüm projeler için sözcük kaydırmayı devre dışı bırakmak için Araçlar Seçenekler Genel Metin Düzenleyici Tüm Diller Genel'e gidin ve Ayarlar bölümünde Sözcük kaydırma  >    >    >    >    >   **seçeneğinin seçimini** kaldırın. 

- **Devre dışı XAML Tasarımcısı**

    XAML tasarımcısı varsayılan olarak etkindir, ancak yalnızca bir *.xaml* dosyası açarsanız kaynakları kullanır. XAML dosyalarıyla çalışıyor ancak tasarımcı işlevini kullanmak çalışmıyorsanız, biraz bellek serbest bırakmak için bu özelliği devre dışı bırakabilirsiniz.

    Bu XAML Tasarımcısı için Araçlar   >  **Seçenekler'e gidin**  >  **XAML Tasarımcısı**  >  **Etkinleştir XAML Tasarımcısı** seçeneğinin seçimini kaldırın.

- **İş yüklerini kaldırma**

    Artık kullanmayan Visual Studio Yükleyicisi kaldırmak için aşağıdakini kullanabilirsiniz. Bu eylem, artık gerekli olmayan paketleri ve derlemeleri atlayarak başlatma ve çalışma zamanı maliyetini kolaylaştırabilirsiniz.

- **Yerel .gitignore'a izlenmeyen dosyalar ekleme**

    Visual Studio depoya yeni dosyalar eklerken sorunsuz bir deneyim sağlamak için Git komutunu `git status` izlenmeyen dosyalarla çalıştırır. Çok sayıda izlenmeyen dosya olduğunda, `git status` fazladan bellek tüketir. Bu dosyaları yoksaymak ve performansını artırmak için, bu dosyaları veya klasörleri yerel `git status` .gitignore dosyanıza ebilirsiniz. Dosyaya erişmek için Git Ayarlar  >    >  **Git Deposu'Ayarlar.** Ardından Git dosyaları bölümünde **Ekle'ye** tıklar ve bir .gitignore dosyası oluşturun veya varsa Düzenle'ye tıklayın.  

## <a name="force-a-garbage-collection"></a>Çöp toplamaya zorlama

CLR bir çöp toplama bellek yönetim sistemi kullanır. Bu sistemde bazen bellek artık gerekli olan nesneler tarafından kullanılır. Bu durum geçicidir; atık toplayıcısı, performansına ve kaynak kullanımına dayalı olarak bu belleği serbest bırakacaktır. ClR'yi, bir kısayol tuşu kullanarak kullanılmayan bellekleri toplamaya zorlayabilirsiniz Visual Studio. Toplama için bekleyen önemli miktarda çöp varsa ve bir çöp toplamaya zorlarsanız, Görev Yöneticisi'ndedevenv.exeişleminin bellek **kullanımını görüyorsanız.**  Bu yöntemin kullanımı nadiren gereklidir. Ancak, pahalı bir işlem tamamlandıktan sonra (tam derleme, hata ayıklama oturumu veya çözüm açık olayı gibi), işlem tarafından gerçekten ne kadar bellek kullanılı olduğunu belirlemenize yardımcı olabilir. Yerel Visual Studio karma (yönetilen & yerel) olduğundan, zaman zaman yerelocator ve atık toplayıcının sınırlı bellek kaynakları için rekabet etmeleri mümkündür. Yüksek bellek kullanımı koşulları altında, atık toplayıcıyı çalıştırmaya zorlamaya yardımcı olabilir.

Çöp toplamayı zorlamak için şu kısayol tuşunu kullanın: **Ctrl** + **Alt** + **Shift** + **F12**, **Ctrl** + **Alt** + **Shift** + **F12** (iki kez basın).

Çöp toplamayı güvenilir bir şekilde zorlama senaryonun çalışmasını sağlarsa, bu davranış büyük olasılıkla bir hata Visual Studio geri bildirim aracı aracılığıyla bir rapor kaydedin.

CLR çöp toplayıcının ayrıntılı açıklaması için bkz. [Çöp toplamanın temelleri.](/dotnet/standard/garbage-collection/fundamentals)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio performansını iyileştirme](../ide/optimize-visual-studio-performance.md)
- [Çözümleri daha hızlı yükleme (Visual Studio blog)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)