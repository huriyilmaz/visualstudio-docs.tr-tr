---
title: Performansı artırmak için ipuçları
ms.date: 08/14/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3cd7fe9781048f6612ff6bd81c0bf0cbc00a30b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303024"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Visual Studio performans ipuçları ve püf noktaları

Visual Studio performans önerileri, nadir durumlarda ortaya çıkabilecek düşük bellek durumları için tasarlanmıştır. Bu gibi durumlarda, kullanmadığınız belirli Visual Studio özelliklerini optimize edebilirsiniz. Aşağıdaki ipuçları genel öneriler olarak tasarlanmamıştır.

> [!NOTE]
> Bellek sorunları nedeniyle ürünü kullanmakta zorlanıyorsanız, geri bildirim [aracı](../ide/how-to-report-a-problem-with-visual-studio.md)aracılığıyla bize bildirin.

## <a name="use-a-64-bit-os"></a>64 bit işletim sistemi kullanma

Sisteminizi Windows'un 32 bit sürümünden 64 bit sürümüne yükseltirseniz, Visual Studio'nun kullanabileceği sanal bellek miktarını 2 GB'dan 4 GB'a kadar genişletirsiniz. Bu, Visual Studio'nun 32 bit işlem olmasına rağmen önemli ölçüde daha büyük iş yüklerini işlemesini sağlar.

Daha fazla bilgi için bkz: [Bellek sınırları](/windows/desktop/Memory/memory-limits-for-windows-releases) ve [64 bit Windows'da /LARGEADDRESSAWARE kullanın.](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/)

## <a name="disable-automatic-file-restore"></a>Otomatik dosya geri yüklemeyi devre dışı

Visual Studio, önceki oturumda açık bırakılan belgeleri otomatik olarak yeniden açar. Bu, proje türüne ve açılan belgelere bağlı olarak bir çözümü yüklemek için gereken süreyi %30 veya daha fazla uzatabilir. Windows Forms ve XAML gibi tasarımcılar ve bazı JavaScript ve typescript dosyaları, açmak için yavaş olabilir.

Visual Studio, otomatik belge geri yüklemesi çözümün önemli ölçüde daha yavaş yüklenmesine neden olduğunda sizi sarı bir çubukta size bildirimde tür. Aşağıdaki adımları izleyerek otomatik dosya nın yeniden açılmasını devre dışı kullanabilirsiniz:

1. **Seçenekler** iletişim kutusunu açmak için **Araçlar** > **Seçenekleri'ni** seçin.

1. Projeler **ve Çözüm** > **Genel** sayfasında, **çözüm yüküyle ilgili belgeleri yeniden aç'ı**seçin.

Otomatik dosya geri yüklemesini devre dışı bdiler, açmak istediğiniz dosyalara gitmenin hızlı bir yolu [Go To](../ide/go-to.md) komutlarından birini kullanmaktır:

- Genel **Go To** işlevi için,**Tümüne** > **Git'i** **Edit'i** > seçin veya **Ctrl**+**T**tuşuna basın.

- **Düzenleme** > **Yap'ı** > Kullanarak Bir Çözümdeki son düzenleme konumuna geç,**Son Düzenleme Konumuna Git**' e gidin veya **Ctrl**+**Shift**+**Backspace tuşuna**basarak .

- Bir çözümde en son ziyaret edilen dosyaların listesini görmek **için Son Dosyaya Git'i** kullanın.  > En Son**Dosyaya** > **Git'e Git'i** **Seç'i**seçin veya **Ctrl**+**1**, **Ctrl**+**R**tuşuna basın.

## <a name="configure-debugging-options"></a>Hata ayıklama seçeneklerini yapılandırma

Hata ayıklama oturumları sırasında genellikle bellek azalıyorsanız, bir veya daha fazla yapılandırma değişikliği yaparak performansı en iyi duruma getirebilirsiniz.

- **Sadece Kodumu Etkinleştir**

    En basit optimizasyon, yalnızca projeniz için semboller yükleyen **Just My Code** özelliğini etkinleştirmektir. Bu özelliği etkinleştirmek, yönetilen uygulamaların (.NET) hata ayıklanması için önemli bir bellek tasarrufuna neden olabilir. Bu seçenek, bazı proje türlerinde varsayılan olarak zaten etkinleştirilir.

    Just **My Code'u**etkinleştirmek için, Genel Hata**Ayıklama** > **General** **Araçları** > **Seçeneklerini** > seçin ve ardından **Yalnızca Kodumu Etkinleştir'i**seçin.

- **Yüklemek için semboller belirtin**

    Yerel hata ayıklama için, simge dosyalarını yükleme (*.pdb*) bellek kaynakları açısından pahalıdır. Hata ayıklama simge ayarlarınızı bellek tasarrufu için yapılandırabilirsiniz. Genellikle, çözümü yalnızca projenizden gelen modülleri yükecek şekilde yapılandırın.

    Sembol yüklemesini belirtmek **için, Araçlar** > **Seçenekleri** > **Hata Ayıklama** > **Sembolleri'ni**seçin.

    Seçenekleri Tüm **modüller** yerine yalnızca belirtilen **modüllere** ayarlayın ve ardından hangi modülleri yüklemeyi önemsediğinizi belirtin. Hata ayıklama sırasında, modüller penceresindeki belirli **modülleri** sağ tıklatarak sembol yüküne açıkça bir modül ekleyebilirsiniz. (Hata ayıklama sırasında pencereyi açmak için **Hata Ayıklama** > **Windows** > **Modülleri'ni**seçin.)

    Daha fazla bilgi için [bkz.](/visualstudio/ide/visual-studio-performance-tips-and-tricks?view=vs-2019)

- **Tanılama Araçlarını Devre Dışı**

    Kullanımdan sonra CPU profil oluşturmayı devre dışı bırakmamanız önerilir. Bu özellik büyük miktarda kaynak tüketebilir. CPU profil oluşturma etkinleştirildikten sonra, bu durum sonraki hata ayıklama oturumları arasında kalıcıdır, bu nedenle yapıldığında açıkça kapatmaya değer. Sağlanan özelliklere ihtiyacınız yoksa hata ayıklama sırasında tanılama araçlarını devre dışı bırakarak bazı kaynakları kaydedebilirsiniz.

    **Tanılama Araçlarını**devre dışı kalmak için, hata ayıklama oturumu başlatın, **Araçlar** > **Seçenekleri** > **Tanılama Araçlarını Etkinleştir'i**seçin ve seçeneği seçin.

    Daha fazla bilgi için [Profil Oluşturma Araçları'na](../profiling/profiling-feature-tour.md)bakın.

## <a name="disable-tools-and-extensions"></a>Araçları ve uzantıları devre dışı

Performansı artırmak için bazı araçlar veya uzantılar kapatılabilir.

> [!TIP]
> Uzantıları teker teker kapatıp performansı yeniden denetleyerek performans sorunlarını genellikle yalıtabilirsiniz.

### <a name="managed-language-service-roslyn"></a>Yönetilen dil hizmeti (Roslyn)

.NET Derleyici Platformu ("Roslyn") performans konuları hakkında bilgi [için, büyük çözümler için Performans hususları](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)konusuna bakın.

- **Tam çözüm analizini devre dışı**

    Visual Studio, bir yapıyı kurmadan önce hatalar hakkında zengin bir deneyim sağlamak için tüm çözümünüz üzerinde analiz yapar. Bu özellik, hataları mümkün olan en kısa sürede tanımlamak için yararlıdır. Ancak, büyük çözümler için bu özellik önemli bellek kaynaklarını tüketebilir. Bellek baskısı veya benzeri sorunlarla karşınıza çıkıyorsa, bu kaynakları boşaltmak için bu deneyimi devre dışı kullanabilirsiniz. Varsayılan olarak, bu seçenek Visual Basic için etkinleştirilir ve C#için devre dışı bırakılır.

    Tam Çözüm **Çözümlemesi**devre dışı kalmak için, **Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi'ni**seçin, ardından Visual **Basic** veya **C#** seçeneğini seçin. **Gelişmiş'i** seçin ve **tam çözüm çözümanalizini etkinleştir'i**seçin.

- **CodeLens'i devre dışı**

    Visual Studio, görüntülendiği gibi her yöntemde **Tüm Başvuruları Bul** görevini gerçekleştirir. CodeLens, başvuru sayısının satır satır içinde görüntülenmesi gibi özellikler sağlar. Çalışma *ServiceHub.RoslynCodeAnalysisServiceService32*gibi ayrı bir işlemle gerçekleştirilir. Büyük çözümlerde veya kaynak kısıtlı sistemlerde, bu özelliğin performans üzerinde önemli bir etkisi olabilir. Örneğin, 4 GB'lık bir makineye büyük bir çözüm yüklerken veya bu işlem için yüksek CPU kullanımı yla bellek sorunları yaşıyorsanız, CodeLens'in kaynakları boşaltmasını devre dışı kullanabilirsiniz.

    **CodeLens'i**devre dışı kalmak **için, Araçlar** > **Seçenekleri** > Metin**Düzenleyicisi** > **Text Editor** > Tüm Diller**KoduLens'i**seçin ve özelliği seçin.

    > [!NOTE]
    > CodeLens Visual Studio'nun Profesyonel ve Kurumsal sürümlerinde mevcuttur.

### <a name="other-tools-and-extensions"></a>Diğer araçlar ve uzantılar

- **Uzantıları Devre Dışı**

    Uzantılar, Visual Studio'ya yeni işlevler sağlayan veya varolan işlevselliği genişleten ek yazılım bileşenleridir. Uzantılar genellikle bellek kaynak sorunları kaynağı olabilir. Bellek kaynağı sorunları yaşıyorsanız, uzantıları senaryoyu veya iş akışını nasıl etkilediğini görmek için teker teker devre dışı bırakmayı deneyin.

   ::: moniker range="vs-2017"

    Uzantıları devre dışı **bırakıp, Araçlar** > **Uzantıları ve Güncelleştirmeleri'ne**gidin ve belirli bir uzantıyı devre dışı bırakın.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Uzantıları devre dışı kalmak için **Uzantıları** > **Yönet uzantılarına**gidin ve belirli bir uzantıyı devre dışı bırakın.

   ::: moniker-end

- **XAML Tasarımcısını devre dışı**

    XAML tasarımcısı varsayılan olarak etkinleştirilir, ancak yalnızca bir *.xaml* dosyasını açtığınızda kaynakları tüketir. XAML dosyalarıyla çalışıyorsanız ancak tasarımcı işlevini kullanmak istemiyorsanız, bazı bellekleri boşaltmak için bu özelliği devre dışı edin.

    **XAML Tasarımcısı**devre dışı kalmak için, **Tools** > **Options** > **XAML Designer** > **Enable XAML Designer'a**gidin ve seçeneği seçin.

- **İş yüklerini kaldırma**

    Artık kullanılmayan iş yüklerini kaldırmak için Visual Studio Yükleyici'yi kullanabilirsiniz. Bu eylem, artık gerekli olmayan paketleri ve derlemeleri atlayarak başlangıç ve çalışma zamanı maliyetini kolaylaştırabilir.

## <a name="force-a-garbage-collection"></a>Çöp toplamayı zorlama

CLR bir çöp toplama bellek yönetim sistemi kullanır. Bu sistemde, bazen bellek artık gerekli olmayan nesneler tarafından kullanılır. Bu durum geçicidir; çöp toplayıcı performansı ve kaynak kullanımı buluşsal dayalı bu bellek serbest bırakacaktır. Visual Studio'da hotkey kullanarak CLR'yi kullanılmayan herhangi bir bellek toplamaya zorlayabilirsiniz. Toplama için bekleyen önemli miktarda çöp varsa ve bir çöp toplama yı zorluyorsanız, **Görev Yöneticisi'ndeki** *devenv.exe* işleminin bellek kullanımını görmeniz gerekir. Bu yöntemi kullanmak için nadiren gereklidir. Ancak, pahalı bir işlem tamamlandıktan sonra (tam oluşturma, hata ayıklama oturumu veya çözüm açık olay gibi), işlem tarafından gerçekten ne kadar bellek kullanıldığını belirlemenize yardımcı olabilir. Visual Studio karışık olduğundan (yerel & yönetilen), bazen yerel ayırıcı ve çöp toplayıcısının sınırlı bellek kaynakları için rekabet etmesi mümkündür. Yüksek bellek kullanımı koşullarında, çöp toplayıcısını çalıştırmaya zorlamaya yardımcı olabilir.

Çöp toplamayı zorlamak için hotkey kullanın: **Ctrl**+**Alt**+**Shift**+**F12**, **Ctrl**+**Alt**+**Shift**+**F12** (iki kez basın).

Çöp toplamayı zorlamak senaryonuzun güvenilir bir şekilde çalışmasını sağlıyorsa, bu davranışın bir hata olma olasılığı yüksek olduğundan Visual Studio geri bildirim aracı aracılığıyla bir rapor hazırlanın.

CLR çöp toplayıcısının ayrıntılı bir açıklaması [için, çöp toplamanın temellerine](/dotnet/standard/garbage-collection/fundamentals)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio performansını iyileştirme](../ide/optimize-visual-studio-performance.md)
- [Çözümleri daha hızlı yükleyin (Visual Studio blog)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
