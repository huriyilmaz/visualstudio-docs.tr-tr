---
title: Genel, Hata Ayıklama, Seçenekler İletişim Kutusu | Microsoft Dokümanlar
ms.date: 11/12/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98bbd65d11b26d9b35000e4acbe4d28a585f8ddc
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472688"
---
# <a name="general-debugging-options"></a>Genel hata ayıklama seçenekleri

Visual Studio hata ayıklama seçeneklerini ayarlamak **için, Araçlar** > **Seçenekleri'ni**seçin ve **Hata Ayıklama'nın** altında **Genel** seçeneklerin yanındaki kutuları seçin veya seçin. **Araçlar** > **Alma ve Dışa Aktarma Ayarları** > tüm**ayarları sıfırla**ile tüm varsayılan ayarları geri yükleyebilirsiniz. Ayarların bir alt kümesini sıfırlamak için, test etmek istediğiniz değişiklikleri yapmadan önce Ayarlarınızı **İçe Ve Dışa Aktar Ayarları** Sihirbazı'na kaydedin ve ardından kaydedilen ayarlarınızı aktarın.

Aşağıdaki **Genel** seçenekleri ayarlayabilirsiniz:

**Tüm kesme noktalarını silmeden önce sor**: **Tüm Kesme Noktalarını Sil** komutunu tamamlamadan önce onay gerektirir.

**Bir işlem kırıldığında tüm işlemleri bozun**: Hata ayıklamanın bağlı olduğu tüm işlemleri aynı anda, bir mola gerçekleştiğinde kırar.

**Özel durumlar AppDomain veya yönetilen/yerel sınırları geçtiğinde ara**: Yönetilen veya karma modda hata ayıklamada, ortak dil çalışma süresi, aşağıdaki koşullar doğru olduğunda uygulama etki alanı sınırlarını veya yönetilen/yerel sınırları aşan özel durumları yakalayabilir:

1. Yerel kod, COM Interop kullanarak yönetilen kodu aradığında ve yönetilen kod bir özel durum attığında. Bkz. [COM Interop'a Giriş](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Uygulama etki alanında çalışan yönetilen kod 1 uygulama etki alanı 2 yönetilen kod çağırır ve uygulama etki alanı 2 kodu bir özel durum atar. Bkz. [Uygulama etki alanları ile Programlama.](/dotnet/articles/framework/app-domains/index)

3. Kod yansımayı kullanarak bir işlevi çağırdığında ve bu işlev bir özel durum oluşturduğunda. Bkz. [Yansıma](/dotnet/framework/reflection-and-codedom/reflection).

2 ve 3. `mscorlib` Bu seçenek, yakalanan `mscorlib`özel durumlar üzerinde kırma etkilemez.

**Adres düzeyinde hata ayıklamayı etkinleştirme**: Adres düzeyinde hata ayıklama için gelişmiş özellikler sağlar **(Sökme** penceresi, **Registers** penceresi ve adres kesme noktaları).

- **Kaynak kullanılamıyorsa sökmeyi göster**: **Kaynağın** kullanılamadığı kodu hata ayıklarken Sökme penceresini otomatik olarak gösterir.

**Kesme noktası filtrelerini etkinleştir**: Filtreleri yalnızca belirli işlemleri, iş parçacıklarını veya bilgisayarları etkileyecek şekilde kesme noktalarına ayarlamanızı sağlar.

**Yeni Özel Durum Yardımcısı'nı kullanın**: Özel Durum Yardımcısı'nın yerini alan Özel Durum Yardımcısı'nı etkinleştirin. (Visual Studio 2017'den itibaren Exception Helper desteklenir)

> [!NOTE]
> Yönetilen kod için bu seçenek daha önce **özel durum yardımcısıetkinleştir** olarak adlandırıldı.

**Yalnızca Kodumu Etkinleştir**: Hata ayıklayıcı, yalnızca kullanıcı kodunu ("Kodum") görüntüler ve adımları, sistem kodunu ve en iyi duruma getirilmiş veya hata ayıklama sembolleri olmayan diğer kodları yok sayarak görüntüler.

- **Başlatmada kullanıcı kodu yoksa uyar (yalnızca Yönetilen)**: Hata ayıklama Just My Code etkinken başladığında, bu seçenek kullanıcı kodu yoksa ("Kodum") sizi uyarır.

**.NET Framework kaynak adımlamayı etkinleştir**: Hata ayıklamanın .NET Framework kaynağına adım atmasını sağlar. Bu seçeneği etkinleştirmek Yalnızca Kodum'u otomatik olarak devre dışı kılabilir. .NET Framework sembolleri önbellek konumuna indirilir. **Seçenekler** iletişim kutusu, **Hata Ayıklama** kategorisi, **Semboller** sayfası yla önbellek konumunu değiştirin.

**Özellikler ve işleçler üzerinden adım (Yalnızca Yönetilen)**: Hata ayıklayıcının yönetilen koddaki özelliklere ve işleçlere adım atmasını önler.

**Özellik değerlendirmesini ve diğer örtülü işlev çağrılarını etkinleştirme**: Değişkenler pencerelerinde ve **QuickWatch** iletişim kutusundaki özelliklerin ve örtülü işlev çağrılarının otomatik olarak değerlendirilmesi üzerine açılır.

- **Değişkenler windows (Yalnızca C# ve JavaScript) nesneleri üzerinde çağrı dize dönüştürme işlevi**: Değişkenler pencerelerinde nesneleri değerlendirirken örtülü bir dize dönüştürme çağrısı yürütür. Sonuç, tür adı yerine bir dize olarak görüntülenir. Yalnızca C# kodunda hata ayıklama sırasında geçerlidir. Bu ayar DebuggerDisplay özniteliği tarafından geçersiz kılınmış olabilir (bkz. [Hata Ayıklama Ekranı özniteliğini kullanma).](../debugger/using-the-debuggerdisplay-attribute.md)

**Kaynak sunucu desteğini etkinleştir**: Visual Studio hata ayıklayıcısına SrcSrv (`srcsrv.dll`) protokolünü uygulayan kaynak sunuculardan kaynak dosyaları almalarını söyler. Team Foundation Server ve Windows için Hata Ayıklama Araçları protokolü uygulayan iki kaynak sunuculardır. SrcSrv kurulumu hakkında daha fazla bilgi için [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) belgelerine bakın. Buna ek olarak, [bkz.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

> [!IMPORTANT]
> *.pdb* dosyalarını okumak dosyalarda rasgele kod yürütebileceğinden, sunucuya güvendiğinden emin olun.

- **Kaynak sunucu tanılama iletilerini Çıktı penceresine yazdır**: Kaynak sunucu desteği etkinleştirildiğinde, bu ayar tanılama ekranını açar.

- **Kısmi güven derlemeleri için kaynak sunucuya izin ver (Yalnızca Yönetilenler)**: Kaynak sunucu desteği etkinleştirildiğinde, bu ayar kısmi güven derlemeleri için kaynak almama varsayılan davranışını geçersiz kılar.

- **İstemdekalmadan her zaman güvenilmeyen kaynak sunucu komutlarını çalıştırın:** Kaynak sunucu desteği etkinleştirildiğinde, bu ayar güvenilmeyen bir komut çalıştırırken ilke oluşturma davranışını geçersiz kılar.

**Kaynak Bağlantı desteğini etkinleştir**: Visual Studio hata ayıkcısına Kaynak Bağlantı bilgilerini içeren *.pdb* dosyalarının kaynak dosyalarını indirmesini söyler. Kaynak Bağlantı hakkında daha fazla bilgi için [Kaynak bağlantı belirtimine](/dotnet/standard/library-guidance/sourcelink)bakın.

> [!IMPORTANT]
> Kaynak Bağlantı http veya https kullanarak dosya indireceği için *.pdb* dosyasına güvendiğinizi unutmayın.

- **Tüm Kaynak Bağlantısı istekleri için Git Kimlik Bilgisi Yöneticisi kimlik doğrulaması**geri dön : Kaynak Bağlantı desteği etkinleştirildiğinde ve Kaynak Bağlantı isteği kimlik doğrulamayı başarısız olduğunda, Visual Studio daha sonra Git Kimlik Bilgisi Yöneticisi'ni çağırır.

**Kesme noktaları ve geçerli deyim (yalnızca C++) için tüm satırı vurgulayın:** Hata ayıklayıcı bir kesme noktasını veya geçerli deyimi vurguladığında, tüm satırı vurgular.

**Kaynak dosyalarının özgün sürümle tam olarak eşleşecek**şekilde olmasını gerektirme : Hata ayıklayıcıya, bir kaynak dosyanın hata ayıklama oluşturduğunuz yürütülebilir sürümü oluşturmak için kullanılan kaynak kodun sürümüyle eşleştiğini doğrulamak için hata ayıklama aracısöyler. Sürüm eşleşmediğinde, eşleşen bir kaynak bulmanız istenir. Eşleşen bir kaynak bulunamazsa, hata ayıklama sırasında kaynak kodu görüntülenmez.

**Tüm Çıktı penceresi metnini Hemen penceresine yönlendirme**: **Çıkış** penceresinde normalde görünecek tüm hata ayıklayıcı iletilerini **Hemen** penceresine gönderir.

**Değişkenler pencerelerinde nesnelerin ham yapısını göster**: Tüm nesne yapısı görünümü özelleştirmelerini kapatır. Görünüm özelleştirmeleri hakkında daha fazla bilgi için [bkz.](../debugger/create-custom-views-of-managed-objects.md)

**Modül yükündeki JIT optimizasyonunu bastırma (Yalnızca Yönetilen)**: Bir modül yüklendiğinde yönetilen kodun JIT optimizasyonunu devre dışı kılabilir ve hata ayıklayıcı takılıyken JIT derlenir. Performans pahasına olsa da, optimizasyonun devre dışı bırakılması bazı sorunları hata ayıklamayı kolaylaştırabilir. Just My Code kullanıyorsanız, JIT optimizasyonunu bastırmak kullanıcı kodu olmayan ların kullanıcı kodu ("Kodum") olarak görünmesine neden olabilir. Daha fazla bilgi için [JIT optimizasyonu ve hata ayıklama](../debugger/jit-optimization-and-debugging.md)bölümüne bakın.

**ASP.NET için (Chrome, Microsoft Edge ve IE) JavaScript hata ayıklamaetkinleştirme:** ASP.NET uygulamalar için komut dosyası hata ayıklama sağlar. Chrome'da ilk kullanımda, yüklediğiniz Chrome uzantılarını etkinleştirmek için tarayıcıda oturum açmanız gerekebilir. Eski davranışa geri dönmek için bu seçeneği devre dışı edin.

**UWP JavaScript Uygulamaları için Kenar Geliştirici Araçlarını Etkinleştir (Deneysel)**: Microsoft Edge'deki UWP JavaScript uygulamaları için geliştirici araçlarını etkinleştirin.

**eski Chrome JavaScript hata ayıklama**ASP.NET etkinleştirin : ASP.NET uygulamalar için eski Chrome JavaScript komut dosyası ayıklama sağlar. Chrome'da ilk kullanımda, yüklediğiniz Chrome uzantılarını etkinleştirmek için tarayıcıda oturum açmanız gerekebilir.

**Visual Studio'yu Yönetici olarak çalıştırırken Chrome JavaScript hata ayıklamasını başlatmak için deneysel bir yol kullanın**: JavaScript hata ayıklama sırasında Chrome'u başlatmak için yeni bir yol denemek için Visual Studio'yu söyler.

**Yük dll dışa aktarımları (yalnızca Yerel)**: Yükler dll dışa aktarma tabloları. Windows iletileri, Windows yordamları (WindowProcs), COM nesneleri veya mareşallik veya sembolleri olmayan herhangi bir dll ile çalışıyorsanız dll dışa aktarma tablolarından gelen sembol bilgileri yararlı olabilir. DLL dışa aktarma bilgilerini okumak bazı genel giderleri içerir. Bu nedenle, bu özellik varsayılan olarak kapalıdır.

Dll'nin dışa aktarma tablosunda hangi sembollerin mevcut olduğunu görmek için . `dumpbin /exports` Semboller herhangi bir 32-bit sistem dll için kullanılabilir. Çıktıyı `dumpbin /exports` okuyarak, alfanümerik olmayan karakterler de dahil olmak üzere tam işlev adını görebilirsiniz. Bu, bir işlev bir kesme noktası ayarlamak için yararlıdır. dll dışa aktarım tablolarındaki işlev adları hata ayıklayıcının başka bir yerinde kesilmiş olarak görünebilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir. Daha fazla bilgi için [dumpbin /dışa aktarma](/cpp/build/reference/dash-exports)

**Paralel yığınlar diyagramını aşağıdan yukarıya göster**: Paralel **Yığınlar** penceresinde yığınların görüntülendiği yönü denetler.

**Yazılan veriler değeri değiştirmediyse GPU bellek erişim özel durumlarını yoksay:** Veri değişmediyse hata ayıklama sırasında algılanan yarış koşullarını yok sayar. Daha fazla bilgi için Bkz. [Hata Ayıklama GPU Kodu.](../debugger/debugging-gpu-code.md)

**Yönetilen Uyumluluk Modunu Kullan**: Varsayılan hata ayıklama motorunu, bu senaryoları etkinleştirmek için eski bir sürümle değiştirir:

- C#, Visual Basic veya F# dışında kendi İfade Değerlendiricisi sağlayan bir .NET dili kullanıyorsunuz (bu C++/CLI içerir).

- Karışık mod hata ayıklama sırasında C++ projelerinde Edit ve Continue'yi etkinleştirmek istiyorsunuz.

> [!NOTE]
> Yönetilen Uyumluluk modunu seçmek, yalnızca varsayılan hata ayıklama altyapısında uygulanan bazı özellikleri devre dışı kılabilir. Eski hata ayıklama motoru Visual Studio 2012'de değiştirildi.

**Eski C# ve VB ifade değerlendiricilerkullanın**: Hata ayıklayıcı Visual Studio 2015 Roslyn tabanlı ifade değerlendiriciler yerine Visual Studio 2013 C# veya Visual Basic ifade değerlendiriciler kullanır.

**Güvenli olmayan işlemlere karşı özel hata ayıklayıcı görüntüleyiciler kullanırken uyar (Yalnızca Yönetilen)**: Visual Studio, güvenli olmayan kod çalıştırdığı için, hata ayıklama işleminde kod çalıştıran özel bir hata ayıklayıcı görselleştiricisi kullandığınızda sizi uyarır.

**Windows hata ayıklama ayırıcısını etkinleştirin (yalnızca Yerel)**: Yığın tanılamayı geliştirmek için windows hata ayıklama yığınını etkinleştirin. Bu seçeneği etkinleştirmek hata ayıklama performansını etkiler.

**XAML için Ara Bilgi İletim Araçlarını Etkinleştirin**: Canlı Görsel Ağaç ve Canlı Özellik Keşfet pencereleri, desteklenen bir proje türünde hata ayıklamaya**başladığınızda**görünür. Daha fazla bilgi için [bkz.](../xaml-tools/inspect-xaml-properties-while-debugging.md)

- **Canlı Görsel Ağaç'ta seçili öğeleri önizleme**: Bağlamı seçilen XAML öğesi de **Canlı Görsel Ağaç** penceresinde seçilir.

- **Uygulamada çalışma zamanı araçlarını göster**: Debugged ediliyor XAML uygulamasının ana penceresinde bir araç çubuğunda Canlı Görsel **Ağaç** komutları gösterir. Bu seçenek Visual Studio 2015 Güncelleme 2'de tanıtıldı.

- **XAML Hot Reload'ı etkinleştir**: Uygulamanız çalışırken XAML koduile XAML Hot Reload özelliğini kullanmanıza olanak tanır. (Bu özellik daha önce "XAML Edit and Continue" olarak adlandırılıyordu)

::: moniker range=">= vs-2019" 
- **Sadece Benim XAML etkinleştirin**: Visual Studio 2019 sürüm 16.4'ten başlayarak, **Canlı Görsel Ağaç** varsayılan olarak yalnızca kullanıcı kodu olarak sınıflandırılan XAML'yi gösterir. Bu seçeneği devre dışı ederseniz, oluşturulan tüm XAML kodu araçta gösterilir.

- **Bir öğe seçildiğinde seçim modunu kapatma** Visual Studio 2019 sürüm 16.4'ten başlayarak, uygulama içi araç çubuğu öğesi seçici düğmesi **(Seçimi etkinleştir)** bir öğe seçildiğinde kapanır. Bu seçeneği devre dışı ederseniz, uygulama içi araç çubuğunu yeniden tıklatana kadar öğe seçimi açık kalır.
::: moniker-end

**Hata ayıklama sırasında Tanılama Araçları etkinleştirin**: Hata ayıklama sırasında **Tanılama Araçları** penceresi görüntülenir.

**Hata ayıklama sırasında geçen süreyi PerfTip göster**: Hata ayıklama sırasında kod penceresi, belirli bir yöntem çağrısının geçen süresini görüntüler.

**Etkinleştir ve Devam Et**: Hata ayıklama sırasında Edit ve Continue işlevini etkinleştirin.

- **Yerel Edit'i Etkinleştir ve Devam Et**: Yerel C++ kodunu hata ayıklarken Edit ve Continue işlevini kullanabilirsiniz. Daha fazla bilgi için [bkz.](../debugger/edit-and-continue-visual-cpp.md)

- **Devam (Yalnızca Yerel) üzerinde değişiklik uygulayın**: Visual Studio, işlemi bir mola durumundan devam ederken yaptığınız olağanüstü kod değişikliklerini otomatik olarak derler ve uygular. Seçili değilse, **Hata Ayıklama** menüsü altındaki **Kod Değişiklikleri Uygula** öğesini kullanarak değişiklikleri uygulamayı seçebilirsiniz.

- **Eski kod hakkında uyarı (yalnızca Yerel)**: Eski kod hakkında uyarılar alın.

**Hata ayıklama sırasında düzenleyicide Tıklat düğmesini göster**: Bu seçenek seçildiğinde, hata ayıklama sırasında [Tıklat'a Çalıştır](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) düğmesi gösterilir.

**Hata ayıklama dururken konsolu otomatik olarak kapatın**: Görsel Studio'ya hata ayıklama oturumunun sonunda konsolu kapatmasını söyler.

::: moniker range=">= vs-2019"
**Hızlı ifade değerlendirmesini etkinleştir (Yalnızca Yönetilen)**: Hata ayıklamanın basit özelliklerin ve yöntemleri simüle ederek daha hızlı değerlendirme denemesine olanak tanır.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Visual Studio'nun eski sürümlerinde seçenekler mevcuttur

Visual Studio'nun eski bir sürümünü kullanıyorsanız, bazı ek seçenekler olabilir.

**Özel durum yardımcısını etkinleştir**: Yönetilen kod için özel durum yardımcısını etkinleştirin. Visual Studio 2017'den itibaren, Özel Durum Yardımcısı özel durum yardımcısının yerini aldı.

**Işlenmemiş özel durumlardaki çağrı yığınını gevşetin:** **Çağrı Yığını** penceresinin, işlenmemiş özel durum oluşmadan önce çağrı yığınını noktaya geri almasına neden olur.

**Başlatmada sembol yoksa uyar (yalnızca yerel)**: Hata ayıklamanın sembol bilgisi bulunmayan bir programı hata ayıklarken bir uyarı iletişim kutusu görüntüler.

**Başlatmada komut dosyası hata ayıklama devre dışı bırakılırsa uyarı :** Hata ayıklama komut dosyası hata ayıklama devre dışı bırakıldığında bir uyarı iletişim kutusu görüntüler.

**Yerel Uyumluluk Modunu Kullan**: Bu seçenek seçildiğinde, hata ayıklama yeni yerel hata ayıklama yerine Visual Studio 2010 yerel hata ayıklama sını kullanır.

- .NET C++ kodunu hata ayıklarken bu seçeneği kullanın, çünkü yeni hata ayıklama altyapısı .NET C++ ifadelerinin değerlendirilmesini desteklemiyor. Ancak, Yerel Uyumluluk Modu'nu etkinleştirmek, geçerli hata ayıklama uygulamasının çalışmasına bağlı olan birçok özelliği devre dışı kılabilir. Örneğin, eski motor Visual Studio 2015 projelerinde `std::string` olduğu gibi yerleşik türleri için birçok görselleştirici yoksundur.   Bu gibi durumlarda en iyi hata ayıklama deneyimi için Visual Studio 2013 projelerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
