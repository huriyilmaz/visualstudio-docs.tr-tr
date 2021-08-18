---
title: Genel, hata ayıklama, Seçenekler Iletişim kutusu | Microsoft Docs
description: Visual Studio hata ayıklayıcı seçeneklerini hata ayıklama gereksinimlerinizi karşılayacak şekilde ayarlayın. Kesme davranışını, hata ayıklama düzeylerini, görüntüleme davranışını ve daha fazlasını yapılandırabilirsiniz.
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
ms.openlocfilehash: 8ea6e78f6913eee9872c99a499834ea4c64ccca27dfbc5909090335aa0489dea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436062"
---
# <a name="general-debugging-options"></a>Genel hata ayıklama seçenekleri

Visual Studio hata ayıklayıcı seçeneklerini ayarlamak için **araçlar**  >  **seçenekler**' i seçin ve **hata ayıklama** altında **genel** seçenekler ' in yanındaki kutuları seçin veya seçimi kaldırın. tüm varsayılan ayarları **araçlar**  >  **içeri aktar ve dışarı aktar Ayarlar**  >  **tüm ayarları sıfırla** geri yükleyebilirsiniz. bir ayar alt kümesini sıfırlamak için, test etmek istediğiniz değişiklikleri yapmadan önce ayarları **içeri ve dışarı aktarma Ayarlar sihirbazı** ile kaydedin, sonra kaydedilen ayarlarınızı daha sonra içeri aktarın.

Aşağıdaki **genel** seçenekleri belirleyebilirsiniz:

**Tüm kesme noktalarını silmeden önce sor**: **tüm kesme noktalarını Sil** komutu tamamlanmadan önce onay gerektirir.

**Bir işlem kesildiğinde tüm Işlemleri kes**: aynı anda, bir kesme gerçekleştiğinde hata ayıklayıcının eklendiği tüm işlemleri eşzamanlı olarak keser.

**Özel durum AppDomain veya yönetilen/yerel sınırları olduğunda kes**: yönetilen veya karma mod hata ayıklamada, ortak dil çalışma zamanı, aşağıdaki koşullar doğru olduğunda, uygulama etki alanı sınırlarını veya yönetilen/yerel sınırları barındıran özel durumları yakalayabilir:

1. Yerel kod, yönetilen kodu COM birlikte çalışabilirliği kullanarak çağırdığında ve yönetilen kod bir özel durum oluşturduğunda. Bkz. [com birlikte çalışabilirliğine giriş](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Uygulama etki alanı 1 ' de çalıştırılan yönetilen kod, uygulama etki alanı 2 ' deki Yönetilen kodu çağırdığında ve uygulama etki alanı 2 ' deki kod bir özel durum oluşturur. Bkz. [uygulama etki alanlarıyla programlama](/dotnet/articles/framework/app-domains/index).

3. Kod, yansıma kullanarak bir işlevi çağırdığında ve bu işlev bir özel durum oluşturursa. Bkz. [yansıma](/dotnet/framework/reflection-and-codedom/reflection).

2 ve 3. koşullarda, özel durum bazen `mscorlib` ortak dil çalışma zamanı yerine içindeki yönetilen kod tarafından yakalanır. Bu seçenek tarafından yakalanan özel durumların kesilmesini etkilemez `mscorlib` .

**Adres düzeyinde hata ayıklamayı etkinleştir**: Adres düzeyinde hata ayıklama için gelişmiş özellikleri etkinleştirir ( **ayrıştırılmış** pencere, **Yazmaçları** penceresi ve adres kesme noktaları).

- **Kaynak kullanılamıyorsa ayrıştırılmış derlemeyi göster**: kaynağın kullanılamayan kodu hata ayıkladığınızda otomatik olarak **ayrıştırılmış** pencereyi gösterir.

**Kesme noktası filtrelerini etkinleştir**: kesme noktalarında yalnızca belirli işlem, iş parçacığı veya bilgisayarları etkileyecek şekilde filtre ayarlamanıza olanak sağlar.

**Yeni özel durum yardımcısını kullan**: özel durum Yardımcısı 'nın yerini alan özel durum yardımcısını sunar. (özel durum yardımcısı Visual Studio 2017 ' den itibaren desteklenir)

> [!NOTE]
> Yönetilen kod için bu seçenek daha önce **özel durum Yardımcısı 'Nı etkinleştir** olarak adlandırılmıştı.

**Yalnızca kendi kodum etkinleştir**: hata ayıklayıcı yalnızca Kullanıcı kodu ("kodum") içinde gösterilir ve adımları, en iyileştirilmiş olan veya hata ayıklama sembolleri olmayan diğer kodları yoksayar.

- **Başlatma üzerinde Kullanıcı kodu yoksa uyar (yalnızca yönetilen)**: hata ayıklama yalnızca kendi kodum etkinken başlatıldığında, Kullanıcı kodu yoksa ("My Code") Bu seçenek sizi uyarır.

**.NET Framework kaynak adımlamayı etkinleştir**: hata ayıklayıcının .NET Framework kaynak üzerinde yer almasına izin verir. Bu seçeneğin etkinleştirilmesi Yalnızca kendi kodum otomatik olarak devre dışı bırakır. .NET Framework semboller, bir önbellek konumuna indirilir. Önbellek konumunu **Seçenekler** iletişim kutusu, **hata ayıklama** kategorisi, **semboller** sayfası ile değiştirin.

**Özellikler ve işleçler üzerinde adımla (yalnızca yönetilen)**: hata ayıklayıcının Yönetilen koddaki Özellikler ve işleçlere erişmesini önler.

**Özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**: değişkenler penceresi ve **QuickWatch** iletişim kutusunda özelliklerin otomatik olarak değerlendirilmesini ve örtük işlev çağrılarını etkinleştirir.

- **Değişkenler penceresinde nesnelerde dize dönüştürme Işlevini çağırın (yalnızca C# ve JavaScript)**: değişkenler penceresinde nesneleri değerlendirirken örtük bir dize dönüştürme çağrısı yürütür. Sonuç tür adı yerine bir dize olarak görüntülenir. Yalnızca C# kodunda hata ayıklanırken geçerlidir. Bu ayar DebuggerDisplay özniteliği tarafından geçersiz kılınabilir (bkz. [DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md)).

**kaynak sunucu desteğini etkinleştir**: Visual Studio hata ayıklayıcıya srcsrv () protokolünü uygulayan kaynak sunuculardan kaynak dosyaları almasını söyler `srcsrv.dll` . Team Foundation Server ve Windows hata ayıklama araçları, protokolü uygulayan iki kaynak sunucularıdır. SrcSrv kurulumu hakkında daha fazla bilgi için bkz. [srcsrv](/windows-hardware/drivers/debugger/srcsrv) belgeleri. Ayrıca bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> *. Pdb* dosyalarını okuma dosyalarında rastgele kod yürütebildiğinden, sunucuya güvendiğinizden emin olun.

- **Kaynak sunucusu tanılama Iletilerini çıkış penceresine Yazdır**: kaynak sunucu desteği etkinleştirildiğinde, bu ayar tanılama görüntüsünü etkinleştirir.

- **Kısmi güven derlemeleri (yalnızca yönetilen) için kaynak sunucuya Izin ver**: kaynak sunucu desteği etkinleştirildiğinde, bu ayar kısmi güven derlemeleri için kaynakları almamanın varsayılan davranışını geçersiz kılar.

- **Güvenilmeyen kaynak sunucu komutlarını her zaman sormadan Çalıştır**: kaynak sunucu desteği etkinleştirildiğinde, bu ayar Güvenilmeyen bir komutu çalıştırırken sorma işleminin varsayılan davranışını geçersiz kılar.

**kaynak bağlantısı desteğini etkinleştir**: Visual Studio hata ayıklayıcıya kaynak bağlantı bilgilerini içeren *. pdb* dosyalarının kaynak dosyalarını indirmesini söyler. Kaynak bağlantısı hakkında daha fazla bilgi için bkz. [kaynak bağlantı belirtimi](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Kaynak bağlantısı, http veya https kullanarak dosyaları indirileceği için, *. pdb* dosyasına güvendiğinizden emin olun.

- **tüm kaynak bağlantısı istekleri için git credential Manager kimlik doğrulamasına geri dön**: kaynak bağlantısı desteği etkinken ve bir kaynak bağlantı isteği kimlik doğrulaması başarısız olursa, Visual Studio git kimlik bilgileri yöneticisi 'ni çağırır.

**Kesme noktaları ve geçerli deyimin tüm kaynak satırını Vurgula (yalnızca C++)**: hata ayıklayıcı bir kesme noktasını veya geçerli ifadeyi vurguladığınızda, tüm satırı vurgular.

**Kaynak dosyalarının özgün sürümle tam olarak eşleşmesini gerektir**: hata ayıklayıcıya bir kaynak dosyanın, hata ayıklaması yaptığınız yürütülebilir dosyayı oluşturmak için kullanılan kaynak kodun sürümüyle eşleştiğini doğrulamasını söyler. Sürüm eşleşmediği zaman, eşleşen bir kaynak bulmanız istenir. Eşleşen bir kaynak bulunamazsa, hata ayıklama sırasında kaynak kodu gösterilmez.

**Tüm çıkış penceresi metnini komut penceresine yeniden yönlendir**: normalde **Çıkış** penceresinde görüntülenen tüm hata ayıklayıcı iletilerini **hemen** bir pencereye gönderir.

**Değişkenler penceresinde nesnelerin ham yapısını göster Windows**: tüm nesne yapısı görünümü özelleştirmelerini kapatır. Özelleştirmeleri görüntüle hakkında daha fazla bilgi için bkz. [yönetilen nesnelerin özel görünümlerini oluşturma](../debugger/create-custom-views-of-managed-objects.md).

**Modül YÜKLEMESINDE JIT Iyileştirmesini bastır (yalnızca yönetilen)**: bir modül yüklendiğinde YÖNETILEN kodun JIT iyileştirmesini devre dışı bırakır ve hata AYıKLAYıCı eklendiğinde JIT derlenir. İyileştirmenin devre dışı bırakılması, performans masrafına karşın bazı sorunların hatalarını ayıklamanızı kolaylaştırabilir. Yalnızca kendi kodum kullanıyorsanız, JıT iyileştirmesini gizleme Kullanıcı dışı kodun kullanıcı kodu ("My Code") olarak görünmesine neden olabilir. Daha fazla bilgi için bkz. [JIT İyileştirmesi ve hata ayıklama](../debugger/jit-optimization-and-debugging.md).

**ASP.NET için JavaScript hata ayıklamasını etkinleştir (Chrome, Microsoft Edge ve ıe)**: ASP.NET uygulamalar için betik hata ayıklayıcısını etkinleştirir. Chrome 'da ilk kez kullanırken, yüklemiş olduğunuz Chrome uzantılarını etkinleştirmek için tarayıcıda oturum açmanız gerekebilir. Eski davranışa dönmek için bu seçeneği devre dışı bırakın.

::: moniker range=">= vs-2019"
**Geçerli hedeflerde JavaScript 'te hata ayıklama için çoklu hedef JavaScript hata ayıklayıcısını kullanmayı etkinleştirin (hata ayıklama yeniden başlatması gerekir)** Tarayıcıya ve arka uca bağlantı sağlar. böylece, düzenleyiciden istemci ve sunucu üzerinde çalışan kodunuzun hatalarını ayıklamanıza olanak tanır.
::: moniker-end

**DLL dışarı aktarmaları yükle (yalnızca yerel)**: dll dışa aktarma tablolarını yükler. dll dışarı aktarma tablolarından sembol bilgileri, Windows iletileri, Windows yordamlar (windowprocs), COM nesneleri veya sıralama ya da sembolleri olmayan herhangi bir dll ile çalışıyorsanız yararlı olabilir. Dll dışa aktarma bilgilerini okuma bazı ek yük içerir. Bu nedenle, bu özellik varsayılan olarak kapalıdır.

Dll 'nin dışarı aktarma tablosunda hangi simgelerin kullanılabildiğini görmek için kullanın `dumpbin /exports` . Semboller, 32 bit sistem dll 'si için kullanılabilir. Çıktıyı okuyarak, `dumpbin /exports` alfasayısal olmayan karakterler de dahil olmak üzere tam işlev adını görebilirsiniz. Bu, bir işlev bir kesme noktası ayarlamak için yararlıdır. DLL dışarı aktarma tablolarındaki işlev adları, hata ayıklayıcının başka bir yerinde kesilmiş görünebilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir. Daha fazla bilgi için bkz. [dumpbin/dışarı aktarmalar](/cpp/build/reference/dash-exports).

**Paralel Yığınlar diyagramını aşağıdan yukarı göster**: yığınların **Paralel Yığınlar** penceresinde gösterileceği yönü denetler.

**Yazılan veriler değeri değiştirmediyse, GPU bellek erişimi özel durumlarını yoksay**: veri değiştirilmediyse hata ayıklama sırasında algılanan yarış koşullarını yoksayar. Daha fazla bilgi için bkz. [GPU kodunda hata ayıklama](../debugger/debugging-gpu-code.md).

**Yönetilen uyumluluk modunu kullan**: Bu senaryoları etkinleştirmek için varsayılan hata ayıklama altyapısını eski bir sürümle değiştirir:

- kendi ifade değerlendiricisi sağlayan C#, Visual Basic veya F # dışında bir .net dili kullanıyorsunuz (C++/clı 'yı içerir).

- Karışık modda hata ayıklama sırasında C++ projeleri için Düzenle ve devam et 'i etkinleştirmek istiyorsunuz.

> [!NOTE]
> Yönetilen Uyumluluk modunu seçme, yalnızca varsayılan hata ayıklama altyapısında uygulanan bazı özellikleri devre dışı bırakır. eski hata ayıklama altyapısı Visual Studio 2012 ' de değiştirildi.

::: moniker range="vs-2017"
**eski C# ve VB ifadesi kullanın değerlendiricileri**: hata ayıklayıcı, Visual Studio 2015 roslyn tabanlı ifade değerlendiricileri yerine Visual Studio 2013 C# veya Visual Basic expression değerlendiricileri kullanacaktır.
::: moniker-end

**güvenli olmayan işlemlere karşı özel hata ayıklama görselleştiricileri kullanıldığında uyar (yalnızca yönetilen)**: Visual Studio, hata ayıklama işleminde kodu çalıştıran özel bir hata ayıklayıcı görselleştirmesini kullanırken, güvenli olmayan kod çalıştırdığından sizi uyarır.

**Windows hata ayıklama yığın ayırıcısını etkinleştir (yalnızca yerel)**: yığın tanılamayı geliştirmek için Windows hata ayıklama yığınını etkinleştirir. Bu seçeneğin etkinleştirilmesi, hata ayıklama performansını etkiler.

**XAML için Kullanıcı arabirimi hata ayıklama araçlarını etkinleştir**: canlı görsel ağaç ve canlı özellik Windows ' u keşfet, hata ayıklamayı başlattığınızda (**F5**) desteklenen bir proje türü görüntülenir. Daha fazla bilgi için bkz. [hata ayıklama SıRASıNDA xaml özelliklerini inceleme](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Canlı görsel ağaçta seçili öğeleri önizleyin**: bağlamı SEÇILI olan xaml öğesi, **canlı görsel ağaç** penceresinde de seçilidir.

- **Uygulamada çalışma zamanı araçlarını göster**: **canlı görsel ağaç** komutlarını, hata ayıklamakta olan xaml uygulamasının ana penceresindeki bir araç çubuğunda gösterir. bu seçenek Visual Studio 2015 güncelleştirme 2 ' de sunulmuştur.

- **Xaml Hot Reload 'ı etkinleştir**: uygulamanız çalışıyorsa XAML kodu Ile xaml etkin yeniden yükleme özelliğini kullanmanıza olanak sağlar. (Bu özellik daha önce "XAML Düzenle ve devam et" olarak adlandırılmıştı)

::: moniker range=">= vs-2019" 
- **yalnızca xaml 'yi etkinleştir**: Visual Studio 2019 sürüm 16,4 ' den başlayarak, varsayılan olarak **canlı görsel ağaç** yalnızca kullanıcı kodu olarak sınıflandırılan XAML 'yi gösterir. Bu seçeneği devre dışı bırakırsanız, tüm oluşturulan XAML kodu araç içinde gösterilir.

- **Bir öğe seçildiğinde seçim modunu** kapat Visual Studio 2019 sürüm 16,4 ' den başlayarak, bir öğe seçildiğinde uygulama içi araç çubuğu öğe seçicisi düğmesine (**seçimi etkinleştir**) geçiş yapın. Bu seçeneği devre dışı bırakırsanız, uygulama içi araç çubuğu düğmesine yeniden tıklayana kadar öğe seçimi açık kalır.

- **Belge KAYDEDERKEN xaml etkin yeniden yükleme Uygula** Visual Studio 2019 sürüm 16,6 ' den başlayarak, belgenizi kaydettiğinizde XAML etkin yeniden yükleme uygular.

::: moniker-end

**Hata ayıklarken tanılama araçları etkinleştir**: hata ayıklarken **Tanılama araçları** pencere görüntülenir.

**Hata ayıklama sırasında Perftıp geçen süreyi göster**: kod penceresi, hata ayıklarken belirli bir yöntem çağrısının geçen süresini gösterir.

**Düzenle ve devam et 'ı etkinleştir**: hata ayıklarken Düzenle ve devam et işlevlerini etkinleştirir.

- **Yerel Düzenle ve devam et 'ı etkinleştir**: Yerel C++ kodunda hata ayıklarken Düzenle ve devam et işlevini kullanabilirsiniz. Daha fazla bilgi için bkz. [Düzenle ve devam et (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **değişiklikleri devam ederken uygula (yalnızca yerel)**: Visual Studio, işleme bir kesme durumundan devam ederken yaptığınız bekleyen kod değişikliklerini otomatik olarak derler ve uygular. Seçili değilse, **hata ayıklama** menüsünün altındaki **kod değişikliklerini Uygula** öğesini kullanarak değişiklikleri uygulamayı seçebilirsiniz.

- **Eski kod hakkında uyar (yalnızca yerel)**: eski kod hakkında uyarı alın.

**Hata ayıklama sırasında düzenleyicide tıklama düğmesine tıklayın**: Bu seçenek belirlendiğinde, hata ayıklanırken [tıklama düğmesine Çalıştır](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) düğmesi gösterilir.

**hata ayıklama durdurulduğunda konsolu otomatik olarak kapat**: hata ayıklama oturumunun sonunda konsolu kapatmak Visual Studio söyler.

::: moniker range=">= vs-2019"
**Hızlı ifade değerlendirmesini etkinleştir (yalnızca yönetilen)**: hata ayıklayıcının basit özellikler ve yöntemlerin yürütülmesini taklit ederek daha hızlı değerlendirmeyi denemesini sağlar.

**Dış işlemde hata ayıklama sembollerini yükle (yalnızca yerel)** Hata ayıklarken bu [bellek iyileştirmesini](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/) sağlar.

**hata ayıklayıcıda kesme yaparken Visual Studio ön plana getir** hata ayıklayıcıda durakladığınızda Visual Studio ön plana geçirir.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Visual Studio eski sürümlerinde kullanılabilen seçenekler

Visual Studio eski bir sürümünü kullanıyorsanız bazı ek seçenekler mevcut olabilir.

**UWP JavaScript uygulamaları (deneysel) Için Edge geliştirici araçları etkinleştirme**: MICROSOFT Edge 'Da UWP JavaScript uygulamaları için geliştirici araçları sağlar.

**ASP.NET için eski chrome javascript hata ayıklayıcısını etkinleştir**: ASP.NET uygulamalar için eski chrome javascript betiği hata ayıklayıcısını etkinleştirir. Chrome 'da ilk kez kullanırken, yüklemiş olduğunuz Chrome uzantılarını etkinleştirmek için tarayıcıda oturum açmanız gerekebilir.

**Özel durum yardımcısını etkinleştir**: yönetilen kod için özel durum yardımcısını etkinleştirir. Visual Studio 2017 ' den başlayarak, özel durum yardımcısı özel durum yardımcısını değiştirdi.

**İşlenmeyen özel durumlarda çağrı yığınını geriye doğru izleme**: **çağrı** yığınını, işlenmeyen özel durum yapılmadan önceki noktaya geri almasına neden olur.

**Visual Studio yönetici olarak çalıştırırken chrome JavaScript hata ayıklamayı başlatmak için deneysel bir yöntem kullanın**: JavaScript hata ayıklaması sırasında chrome 'ı başlatmak için Visual Studio söyler.

**Başlatma üzerinde hiçbir sembol yoksa uyar (yalnızca yerel)**: hata ayıklayıcının sembol bilgisi olmayan bir programda hata ayıklaması yaparken uyarı iletişim kutusu görüntüler.

**Başlatma sırasında betik hata ayıklaması devre dışıysa uyar**: hata ayıklayıcı betiği hata ayıklama devre dışıyken başlatıldığında bir uyarı iletişim kutusu görüntüler.

**yerel uyumluluk modunu kullan**: bu seçenek belirlendiğinde, hata ayıklayıcı yeni yerel hata ayıklayıcı yerine 2010 yerel bir hata ayıklayıcı Visual Studio kullanır.

- .NET c++ kodunda hata ayıklarken bu seçeneği kullanın, çünkü yeni hata ayıklama altyapısı .NET C++ ifadelerini değerlendirmeyi desteklemez. Ancak, yerel uyumluluk modunu etkinleştirmek, geçerli hata ayıklayıcı uygulamasına bağımlı birçok özelliği çalışır şekilde devre dışı bırakır. örneğin, eski altyapıda Visual Studio 2015 projelerinde olduğu gibi yerleşik türler için çok sayıda görselleştiriciler yoktur `std::string` .   bu durumlarda en iyi hata ayıklama deneyimi için Visual Studio 2013 projelerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
