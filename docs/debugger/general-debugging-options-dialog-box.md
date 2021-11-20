---
title: Genel, Hata Ayıklama, Seçenekler İletişim Kutusu | Microsoft Docs
description: Hata Visual Studio hata ayıklayıcısı seçeneklerini ayarlayın. Kesme davranışını, hata ayıklama düzeylerini, görüntüleme davranışını ve çok daha fazlasını yapılandırabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 06/04/2020
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a7dd8d85284cb615f3e203e638bec2e26a83f97a
ms.sourcegitcommit: 8b44ba7864f67afa476708d5092729345e689f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132861542"
---
# <a name="general-debugging-options"></a>Genel hata ayıklama seçenekleri

Hata ayıklayıcı Visual Studio ayarlamak için Araçlar Seçenekleri'ne tıklayın ve Hata ayıklama altında Genel seçeneklerinin yanındaki kutuları seçin  >   **veya seçimi** kaldırın.  Araçlar İçeri ve Dışarı Aktarma ile tüm **varsayılan ayarları geri** yükleyebilir ve  >  **Ayarlar**  >  **sıfırlayabilirsiniz.** Ayarların bir alt kümesini sıfırlamak için, test etmek istediğiniz değişiklikleri **Ayarlar** önce İçeri ve Dışarı Aktarma Sihirbazı ile ayarlarınızı kaydedin ve ardından kaydedilen ayarlarınızı içeri aktarın.

Aşağıdaki Genel seçenekleri **ayarlayın:**

**Tüm kesme noktaları silmeden önce sorun:** Tüm Kesme Noktaları Sil komutunu **tamamlamadan önce onay** gerektirir.

**Bir işlem sonarsa tüm işlemleri kesme:** Bir kesme oluştuğunda hata ayıklayıcının ekli olduğu tüm işlemleri aynı anda kırar.

**AppDomain veya yönetilen/yerel** sınırlar arasında özel durumlar olduğunda kesme: Yönetilen veya karma mod hata ayıklamada, aşağıdaki koşullar doğru olduğunda ortak dil çalışma zamanı uygulama etki alanı sınırlarını veya yönetilen/yerel sınırları aşacak özel durumları yakalayabilir:

1. Yerel kod COM Birlikte Çalışma kullanarak yönetilen kodu çağırsa ve yönetilen kod bir özel durum oluşturur. Bkz. [COM Birlikte Çalışma'ya Giriş.](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop)

2. Uygulama etki alanı 1'de çalışan yönetilen kod, uygulama etki alanı 2'de yönetilen kodu çağırsa ve uygulama etki alanı 2'de kod bir özel durum oluşturur. Bkz. [Uygulama etki alanlarıyla programlama.](/dotnet/articles/framework/app-domains/index)

3. Kod yansıma kullanarak bir işlevi çağırsa ve bu işlev bir özel durum oluşturur. Bkz. [Yansıma](/dotnet/framework/reflection-and-codedom/reflection).

2. ve 3. koşullarda, özel durum bazen ortak dil çalışma zamanı yerine `mscorlib` içinde yönetilen kod tarafından yakalanabilir. Bu seçenek tarafından yakalanan özel durumlar için bozmayı `mscorlib` etkilemez.

**Adres düzeyinde hata ayıklamayı** etkinleştir: Adres düzeyinde hata ayıklama için gelişmiş özelliklere olanak sağlar (Disassembly penceresi,  **Yazmaçlar** penceresi ve adres kesme noktaları).

- **Kaynak kullanılamıyorsa,** disassembly göster: Kaynağın kullanılamamasına neden olan kodun hata ayıklaması yapılırken Otomatik olarak Deassembly penceresini gösterir. 

**Kesme noktası filtrelerini** etkinleştir: Kesme noktalarında yalnızca belirli işlemleri, iş parçacıklarını veya bilgisayarları etkileyecek şekilde filtreler ayarlamaya olanak sağlar.

**Yeni Özel Durum Yardımcısı'nın kullanımı:** Özel durum yardımcısının yerini alan Özel Durum Yardımcısı'nın kullanımını sağlar. (Özel Durum Yardımcı, 2017'Visual Studio başlayarak de desteklene)

> [!NOTE]
> Yönetilen kod için bu seçenek daha önce Özel durum **yardımcıyı etkinleştir olarak çağrıldı.**

**Etkinleştirme Yalnızca kendi kodum:** Hata ayıklayıcı sistem kodunu ve iyileştirilmiş veya hata ayıklama sembollerine sahip olan diğer kodu yoksayarak yalnızca kullanıcı kodunu ("Kodum") görüntüler ve adımlarını gösterir.

- Başlatma sırasında kullanıcı kodu yoksa uyar **(Yalnızca yönetilen)**: Hata ayıklama Yalnızca kendi kodum etkinleştirildiğinde, kullanıcı kodu ("Kodum") yoksa bu seçenek sizi uyarıyor.

**Kaynak .NET Framework etkinleştirme:** Hata ayıklayıcının kaynakta adım .NET Framework sağlar. Bu seçeneğin etkinleştirilmesi, otomatik olarak Yalnızca kendi kodum. .NET Framework simgeleri bir önbellek konuma indirilir. Seçenekler iletişim kutusu, Hata **ayıklama kategorisi,** **Semboller sayfası** ile önbellek **konumunu** değiştirme.

**Özellikler ve işleçler üzerinde adımlama (yalnızca yönetilen)**: Hata ayıklayıcının yönetilen kodda özelliklere ve işleçlere adımlamasını önler.

**Özellik değerlendirmesini ve diğer örtülü işlev** çağrılarını etkinleştir: Değişkenlerin pencerelerinde ve **QuickWatch** iletişim kutusunda özelliklerin otomatik değerlendirilmesini ve örtülü işlev çağrılarını etkinleştirir.

- **Değişken pencerelerinin nesnelerinde dize** dönüştürme işlevini çağırma (yalnızca C# ve JavaScript) : Değişkenlerin pencerelerine nesneleri değerlendirirken örtülü bir dize dönüştürme çağrısı yürütür. Sonuç, tür adı yerine dize olarak görüntülenir. Yalnızca C# kodunda hata ayıklama sırasında geçerlidir. Bu ayar DebuggerDisplay özniteliği tarafından geçersiz kılınabilir [(bkz. DebuggerDisplay özniteliğini kullanma).](../debugger/using-the-debuggerdisplay-attribute.md)

**Kaynak sunucu desteğini etkinleştir:** Visual Studio ( ) protokolünü uygulayan kaynak sunuculardan kaynak dosyaları almak için hata `srcsrv.dll` ayıklayıcıya söyler. Team Foundation Server için Hata Ayıklama Araçları Windows protokolü uygulayan iki kaynak sunucu vardır. SrcSrv kurulumu hakkında daha fazla bilgi için [SrcSrv belgelerine](/windows-hardware/drivers/debugger/srcsrv) bakın. Ayrıca bkz. [Sembol (.pdb) ve kaynak dosyalarını belirtme.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

> [!IMPORTANT]
> *.pdb dosyalarını okumak* dosyalarda rastgele kod yürütebebilir, çünkü sunucuya güvenin.

- **Kaynak sunucu tanılama iletilerini Çıkış penceresine yazdır:** Kaynak sunucu desteği etkinleştirildiğinde, bu ayar tanılama görüntülemeyi açar.

- Kısmi güven derlemeleri için kaynak sunucuya izin ver **(yalnızca yönetilen)**: Kaynak sunucu desteği etkinleştirildiğinde, bu ayar kısmi güven derlemeleri için kaynakları almama varsayılan davranışını geçersiz kılar.

- **Her zaman güvenilmeyen kaynak** sunucu komutlarını istemi olmadan çalıştırın: Kaynak sunucu desteği etkinleştirildiğinde, bu ayar güvenilmeyen bir komut çalıştırarak varsayılan istem davranışını geçersiz kılar.

**Kaynak Bağlantısı desteğini etkinleştir:** Visual Studio hata ayıklayıcısına Kaynak Bağlantı bilgilerini içeren *.pdb* dosyaları için kaynak dosyaları indirmelerini söyler. Kaynak Bağlantı hakkında daha fazla bilgi için bkz. [Kaynak bağlantısı belirtimi.](/dotnet/standard/library-guidance/sourcelink)

> [!IMPORTANT]
> Kaynak Bağlantı http veya https kullanarak dosyaları indirecek olduğundan, *.pdb dosyasına güvenin.*

- **Tüm Kaynak Bağlantı istekleri Kimlik Bilgileri Yöneticisi Git** bağlantı kimlik doğrulamasına geri dön: Kaynak Bağlantı desteği etkinleştirildiğinde ve Kaynak Bağlantı isteği kimlik doğrulaması başarısız olduğunda, Visual Studio Git Kimlik Bilgileri Yöneticisi.

Kesme noktaları ve geçerli deyim için kaynak satırın tamamını vurgula **(yalnızca C++)**: Hata ayıklayıcı bir kesme noktası veya geçerli deyimi vurgularsa, satırın tamamını vurgular.

**Kaynak dosyaların özgün sürümle** tam olarak eşleşmesi gerektir: Hata ayıklayıcıya, kaynak dosyanın hata ayıklamakta olduğunuz yürütülebilir dosyayı oluşturmak için kullanılan kaynak kodun sürümüyle eş olduğunu doğrulamasını söyler. Sürüm eşleşmediğinde eşleşen bir kaynak bulmanız istenir. Eşleşen bir kaynak bulunamazsa, hata ayıklama sırasında kaynak kodu görüntülenmez.

**Tüm Çıkış penceresi metnini Hemen penceresine yeniden yönlendir:** Normalde Çıkış penceresinde  görünecek olan tüm hata ayıklayıcı iletilerini hemen **penceresine** gönderir.

**Değişkenlerin pencerelerinde nesnelerin ham yapısını göster:** Tüm nesne yapısı görünümü özelleştirmelerini kapatma. Görünüm özelleştirmeleri hakkında daha fazla bilgi için [bkz. Yönetilen nesnelerin özel görünümlerini oluşturma.](../debugger/create-custom-views-of-managed-objects.md)

**Modül yükünde JIT** iyileştirmesini gizleme (yalnızca yönetilen) : Hata ayıklayıcı ekliyken bir modül yüklendiğinde ve JIT derlenmiş olduğunda yönetilen kodun JIT iyileştirmesini devre dışı gösterir. İyileştirmeyi devre dışı bırakmak, performansa rağmen bazı sorunlarda hata ayıklamayı kolaylaştırır. JIT iyileştirmeyi Yalnızca kendi kodum, kullanıcı olmayan kodun kullanıcı kodu ("Kodum") olarak görünmesine neden olabilir. Daha fazla bilgi için [bkz. JIT iyileştirme ve hata ayıklama.](../debugger/jit-optimization-and-debugging.md)

**ASP.NET (Chrome, Microsoft Edge ve IE)** için JavaScript hata ayıklamasını etkinleştirme: Tüm uygulamalar için betik hata ASP.NET etkinleştirir. Chrome'da ilk kez kullanıyorsanız, yüklü Chrome uzantılarını etkinleştirmek için tarayıcıda oturum açmanız gerekir. Eski davranışa dönmek için bu seçeneği devre dışı bırakma.

::: moniker range=">= vs-2019"
**Geçerli hedeflerde JavaScript'te hata ayıklamak için** çok hedefli JavaScript hata ayıklayıcısını kullanmayı etkinleştirin (hata ayıklamanın yeniden başlatılması gerekir) Tarayıcı ve arka uç bağlantısını aynı anda sağlayarak istemcide ve sunucuda çalışan kodunuzun hatasını düzenleyiciden ayıklamanıza olanak sağlar.
::: moniker-end

**Dll dışarı aktarmalarını yükleme (yalnızca yerel)**: Dll dışarı aktarma tablolarını yükler. Dll dışarı aktarma tablolarından sembol bilgileri; Windows iletileri, Windows yordamları (WindowProcs), COM nesneleri veya sıralama ya da sembollerin sahip olmadığınız herhangi bir dll ile çalışıyorsanız yararlı olabilir. Dll dışarı aktarma bilgilerini okumak biraz ek yük getirir. Bu nedenle, bu özellik varsayılan olarak kapalıdır.

Dll'nin dışarı aktarma tablosunda hangi simgelerin kullanılabilir olduğunu görmek için `dumpbin /exports` kullanın. Semboller tüm 32 bit sistem dll'leri için kullanılabilir. Çıkışı `dumpbin /exports` okuyarak alfasayısal olmayan karakterler de dahil olmak üzere tam işlev adını görebilir. Bu, bir işlev bir kesme noktası ayarlamak için yararlıdır. Dll dışarı aktarma tablolarından işlev adları hata ayıklayıcının başka bir yerinde kesilmiş görünebilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir. Daha fazla bilgi için bkz. [dumpbin /exports](/cpp/build/reference/dash-exports).

**Paralel yığınlar diyagramını altta göster:** Yığınların Paralel Yığınlar penceresinde görüntülenme **yönünü** kontrol eder.

**Yazılan veriler değerini değiştirmezse GPU bellek** erişimi özel durumlarını yoksayın: Veriler değişmese hata ayıklama sırasında algılanan yarış koşullarını yoksayır. Daha fazla bilgi için bkz. [GPU Kodunda Hata Ayıklama.](../debugger/debugging-gpu-code.md)

::: moniker range="<= vs-2019"
**Yönetilen Uyumluluk Modunu Kullan:** Bu senaryoları etkinleştirmek için varsayılan hata ayıklama altyapısını eski bir sürümle değiştirir:

- Kendi İfade Değerlendiricisini sağlayan (C++/CLI dahil) C#, Visual Basic veya F# dışında bir .NET dili kullanıyorsanız.

- Karma modda hata ayıklama sırasında C++ projeleri için Düzenle ve Devam'ı etkinleştirmek istiyorsunuz.

> [!NOTE]
> Yönetilen Uyumluluk modu seçiliyor, yalnızca varsayılan hata ayıklama altyapısında uygulanan bazı özellikleri devre dışı bırakıyor. Eski hata ayıklama altyapısı, 2012'Visual Studio değiştirilmiştir.
::: moniker-end

::: moniker range="vs-2017"
**Eski C# ve VB** ifade değerlendiricilerini kullanma: Hata ayıklayıcı, Visual Studio 2015 Roslyn tabanlı ifade değerlendiricileri yerine Visual Studio 2013 C# veya Visual Basic ifade değerlendiricilerini kullanır.
::: moniker-end

**Güvenli olmayabilecek** işlemlere karşı özel hata ayıklayıcı görselleştiricileri kullanırken uyar (yalnızca yönetilen) : Visual Studio, güvenli olmayan kod çalıştırmış olabilecek, hata ayıklama işlemi içinde kod çalıştıran özel bir hata ayıklayıcı görselleştiricisi kullanırken sizi uyarıyor.

**Yığın Windows ayırmayı etkinleştirme (yalnızca yerel)**: Yığın tanılamayı geliştirmek için Windows hata ayıklama yığınını etkinleştirir. Bu seçeneğin etkinleştirilmesi hata ayıklama performansını etkiler.

**XAML için KULLANıCı** Arabirimi Hata Ayıklama Araçlarını Etkinleştir: Desteklenen bir proje türü olan hata ayıklamayı (**F5**) başlatsanız Canlı Görsel Ağaç ve Canlı Özellik Keşfetme pencereleri görüntülenir. Daha fazla bilgi için [bkz. Hata ayıklama sırasında XAML özelliklerini inceleme.](../xaml-tools/inspect-xaml-properties-while-debugging.md)

- **Canlı Görsel Ağaç'da seçili** öğelerin önizlemesini görüntüleyin: Canlı Görsel Ağaç penceresinde bağlamı seçilen XAML **öğesi** de seçilir.

- **Uygulamada çalışma zamanı araçlarını göster:** Hata ayıklanacak XAML uygulamasının ana penceresindeki araç çubuğundaKi Canlı Görsel Ağaç komutlarını gösterir.  Bu seçenek, Visual Studio 2015 Güncelleştirme 2'de tanıtıldı.

- **Şu XAML Çalışırken Yeniden Yükleme** etkinleştir: Uygulamanız XAML Çalışırken Yeniden Yükleme XAML koduyla birlikte uygulama özelliğini kullanmanızı sağlar. (Bu özellik daha önce "XAML Düzenle ve Devam" olarak adlandırılırdı)

::: moniker range=">= vs-2019" 
- **Yalnızca Benim XAML'mi** Etkinleştir: Visual Studio 2019 sürüm 16.4'te başlayarak, Canlı Görsel Ağaç varsayılan olarak yalnızca kullanıcı kodu olarak sınıflandırılan XAML'yi gösterir.  Bu seçeneği devre dışı bıraksanız, oluşturulan tüm XAML kodu araçta gösterilir.

- **Öğe seçildiğinde seçim modunu kapatma** 2019 Visual Studio 16.4 sürümünden başlayarak, bir öğe seçildiğinde uygulama içinde araç çubuğu öğe seçici **düğmesi**( Seçimi etkinleştir ) devre dışıdır. Bu seçeneği devre dışı bıraktığınızda, uygulama içinde araç çubuğu düğmesine yeniden tıklanana kadar öğe seçimi devam ediyor.

- **Belge XAML Çalışırken Yeniden Yükleme uygulama** 2019 Visual Studio 16.6 sürümünden başlayarak, XAML Çalışırken Yeniden Yükleme kaydedenler için geçerlidir.

::: moniker-end

**Hata Tanılama Araçları etkinleştir:** **Hata Tanılama Araçları** hata ayıklarken hata ayıklama penceresi görüntülenir.

**Hata ayıklama sırasında PerfTip** geçen zamanı göster: Kod penceresinde hata ayıklama sırasında belirli bir yöntem çağrısının geçen zamanı görüntülenir.

**Düzenle ve Devam'ı** Etkinleştir: Hata ayıklama sırasında Düzenle ve Devam'ı etkinleştirir.

- **Yerel Düzenleme ve Devam'ı** Etkinleştir: Yerel C++ kodunda hata ayıklarken Düzenle ve Devam'ı kullanabilirsiniz. Daha fazla bilgi için [bkz. Düzenle ve Devam Edin (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Devam eden değişiklikler uygula (yalnızca yerel)**: Visual Studio otomatik olarak derlenir ve işleme bir kesme durumdan devam edilirken yaptığınız tüm bekleyen kod değişikliklerini uygular. Seçili değilse, Hata Ayıklama menüsünün altındaki Kod **Değişikliklerini** Uygula öğesini kullanarak değişiklikleri **uygulayabilirsiniz.**

- **Eski kod hakkında uyar (yalnızca yerel)**: Eski kod hakkında uyarı al.

**Hata ayıklama sırasında düzenleyicide Tıklanacak** Şekilde Çalıştır düğmesini [](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) göster: Bu seçenek seçildiğinde hata ayıklama sırasında Tıklanacak Şekilde Çalıştır düğmesi gösterilir.

**Hata ayıklama durduğunda konsolu otomatik olarak kapatın:** Hata Visual Studio sonunda konsolunu kapatmasını söyler.

::: moniker range=">= vs-2019"
**Hızlı ifade değerlendirmesini etkinleştir (yalnızca yönetilen):** Hata ayıklayıcının basit özellikler ve yöntemlerin yürütülmesinin simülasyonu ile daha hızlı değerlendirmeyi denemesine izin verir.

**Dış işlemde hata ayıklama simgelerini yükleme (yalnızca yerel)** Hata ayıklama [sırasında bu bellek](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/) iyileştirmeyi sağlar.

**Hata Visual Studio hata ayıklayıcısında** hata ayıklayıcıda duraklatma sırasında ön plana Visual Studio ön plana geçişler sırasında ön plana getirin.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Önceki sürümlerde kullanılabilen seçenekler Visual Studio

Uygulamanın eski bir sürümünü kullanıyorsanız Visual Studio bazı ek seçenekler olabilir.

**UWP JavaScript Geliştirici Araçları Edge uygulamalarını etkinleştirme (Deneysel):** Uygulama içinde UWP JavaScript uygulamaları için geliştirici Microsoft Edge.

**Eski Chrome JavaScript hata ayıklayıcısını** ASP.NET: Eski Chrome JavaScript betik hata ayıklayıcısını ASP.NET etkinleştirir. Chrome'da ilk kez kullanıyorsanız, yüklü Chrome uzantılarını etkinleştirmek için tarayıcıda oturum açmanız gerekir.

**Özel durum yardımcıyı etkinleştirme:** Yönetilen kod için özel durum yardımcıyı etkinleştirir. 2017'Visual Studio başlayarak, özel durum yardımcısının yerini Özel Durum Yardımcısı aldı.

**İşlenemeyen özel** durumlar üzerinde çağrı  yığınını geriye doğru izleme: Çağrı Yığını penceresinin çağrı yığınını işlanmamış özel durum olmadan önceki noktaya geri alma neden olur.

**Yönetici olarak Visual Studio** chrome javascript hata ayıklamasını başlatmak için deneysel bir yol kullanın: Visual Studio JavaScript hata ayıklaması sırasında Chrome'u başlatmanın yeni bir yolunu denemelerini söyler.

Başlatma sırasında simge yoksa uyar **(yalnızca yerel)**: Hata ayıklayıcının sembol bilgisi olmadığını programda hata ayıklarken bir uyarı iletişim kutusu görüntüler.

**Başlatma sırasında betik hata ayıklama devre dışı bırakılırsa** uyar: Hata ayıklayıcı betik hata ayıklama devre dışı bırakarak başlatıldı olduğunda bir uyarı iletişim kutusu görüntüler.

**Yerel Uyumluluk Modunu Kullan:** Bu seçenek seçildiğinde, hata ayıklayıcı yeni yerel hata ayıklayıcı yerine Visual Studio 2010 yerel hata ayıklayıcısını kullanır.

- Yeni hata ayıklama altyapısı .NET C++ ifadelerini değerlendirmeyi desteklemez, çünkü .NET C++ kodunda hata ayıklarken bu seçeneği kullanın. Ancak, Yerel Uyumluluk Modu'un etkinleştirilmesi, geçerli hata ayıklayıcı uygulamasının çalışmasına bağlı olan birçok özelliği devre dışı bırakmanızı sağlar. Örneğin, eski altyapıda 2015 projelerinde olduğu gibi yerleşik `std::string` türler için Visual Studio görselleştiricisi yok.   Bu Visual Studio 2013 en iyi hata ayıklama deneyimi için projelerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
