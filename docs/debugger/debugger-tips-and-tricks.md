---
title: İpuçları ayıklayıcıda hata ayıklayıcıda hata ayıklama ve püf noktaları
description: Visual Studio hata ayıklayıcısı tarafından desteklenen daha az bilinen özellikler hakkında bilgi Visual Studio öğrenin
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 342386b8e9c0ae3a25639857cf508223a3e57c73955917ff551959859caa3e7f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454620"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Visual Studio'İpuçları Hata Ayıklayıcı için Üretkenlik Ve Püf Noktaları hakkında Visual Studio

Hata ayıklayıcısıyla ilgili üretkenlik ipuçları ve püf noktaları hakkında bilgi edinmek Visual Studio okuyun. Hata ayıklayıcının temel özelliklerine bakmak için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md) Bu konu başlığında, özellik turunda yer alan bazı alanlar açıklanmıştır.

## <a name="pin-data-tips"></a>Veri ipuçlarını sabitleme

Hata ayıklama sırasında sık sık veri ipuçlarının üzerine gelmeniz, kendinize hızlı erişim vermek için değişkenin veri ipucuna sabitlemek istiyor olabilir. Değişken yeniden başlatıldıktan sonra bile sabitlenmiş olarak kalır. Veri ipucu sabitlemek için üzerine gelinken sabitleme simgesine tıklayın. Birden çok değişkeni sabitleyebilirsiniz.

![Veri İpucu Sabitleme](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Kodunuzu düzenleyin ve hata ayıklamaya devam edin (C#, VB, C++)

Uygulama tarafından desteklenen çoğu Visual Studio, hata ayıklama oturumunun ortasında kodunuzu düzenleyebilir ve hata ayıklamaya devam edersiniz. Bu özelliği kullanmak için hata ayıklayıcıda duraklatılmış durumdayken imlecinizi kullanarak kodunuzla tıklayın, düzenlemeler yapmak ve hata ayıklamaya devam etmek için **F5**, **F10** veya **F11'e** basın.

![Düzenleme ve hata ayıklamaya devam](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Özelliği kullanma ve özellik sınırlamaları hakkında daha fazla bilgi için bkz. [Düzenle ve Devam Edin.](../debugger/edit-and-continue.md)

## <a name="edit-xaml-code-and-continue-debugging"></a>XAML kodunu düzenleme ve hata ayıklamaya devam

Hata ayıklama oturumu sırasında XAML kodunu değiştirmek için bkz. XAML kodunu kullanarak [XAML kodu yazma ve hata XAML Çalışırken Yeniden Yükleme.](../xaml-tools/xaml-hot-reload.md)

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Yeniden oluşturması zor olan hata ayıklama sorunları

Uygulamanıza belirli bir durumu yeniden oluşturmak zor veya zaman alan bir durumsa, koşullu kesme noktasının kullanımının yardımcı olup olmadığını göz önünde bulundurabilirsiniz. Uygulama istenen [durumuna](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) girene kadar (örneğin, değişkenin hatalı verileri depolması durumu) uygulama kodunuza girmekten kaçınmak için koşullu kesme noktaları ve filtre kesme noktaları kullanabilirsiniz. İfadeleri, filtreleri, isabet sayılarını ve diğer tüm ifadeleri kullanarak koşulları ayarlayabilirsiniz.

#### <a name="to-create-a-conditional-breakpoint"></a>Koşullu kesme noktası oluşturmak için

1. Bir kesme noktası simgesine (kırmızı top) sağ tıklayın ve Koşullar'ı **seçin.**

2. Kesme **noktası Ayarlar** bir ifade yazın.

    ![Koşullu Kesme Noktası](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Başka bir koşul türüyle ilgileniyorsanız  Kesme  Noktası İletişim Kutusunda Koşullu ifade yerine **Filtrele'yi Ayarlar** ve ardından filtre ipuçlarını izleyin.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Verileri hata ayıklayıcıda gösterecek şekilde yapılandırma

C#, Visual Basic ve C++ (yalnızca C++/CLI kodu) için, hata ayıklayıcıya [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) özniteliğini kullanarak hangi bilgileri göster gösterebilirsiniz. C++ kodu için aynı şeyi [Natvis görselleştirmelerini kullanarak da oluşturabilirsiniz.](create-custom-views-of-native-objects.md)

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

Hata ayıklayıcı bir kod satırı üzerinde duraklatılmışken, sol tarafta sarı ok işaretçisini almak için fareyi kullanın. Sarı ok işaretçisini kod yürütme yolundaki farklı bir noktaya taşıma. Ardından uygulamayı çalıştırmaya devam etmek için F5 veya bir adım komutu kullanın.

![Yürütme İşaretçisini Taşıma](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Yürütme İşaretçisini Taşıma")

Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etmek veya hata ayıklayıcıyı yeniden başlatmadan kodu yeniden çalıştırma gibi şeyler yapabiliriz.

> [!WARNING]
> Genellikle bu özellikle dikkatli olmalısınız ve araç ipucunda bir uyarı görüyorsunuz. Başka uyarılar da görebilir. İşaretçiyi hareket ettiren uygulama önceki bir uygulama durumuna geri döndürülebilir.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Kapsam dışında bir nesneyi izleme (C#, Visual Basic)

İzleme penceresi gibi hata ayıklayıcı pencerelerini kullanarak değişkenleri görüntülemek **kolaydır.** Ancak, bir değişken İzleme penceresinde kapsamın **dışında** olduğunda, değişkenin gri renkte olduğunu farkedebilirsiniz. Bazı uygulama senaryolarında değişken kapsam dışında olsa bile değişkenin değeri değişebilir ve bunu yakından izlemek (örneğin, bir değişken atık toplanabilir) istiyor olabilir. İzleme penceresinde değişkeni için bir Nesne Kimliği oluşturarak **izleyebilirsiniz.**

#### <a name="to-create-an-object-id"></a>Nesne kimliği oluşturmak için

1. Izlemek istediğiniz değişkenin yakınında bir kesme noktası ayarlayın.

2. Hata ayıklayıcısını (**F5**) ve kesme noktası üzerinde durdurun.

3. Değişkeni Yereller  penceresinde bulun ( Yereller'de **> Windows >** ayıkla), değişkene sağ tıklayın ve Nesne Kimliği **Yapma'yı seçin.**

    ![Nesne Kimliği oluşturma](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. YerelLer penceresinde **$** artı bir sayı görüyor **gerekir.** Bu değişken nesne kimliğidir.

5. Nesne kimliği değişkenine sağ tıklayın ve İzleme **Ekle'yi seçin.**

Daha fazla bilgi için [bkz. Nesne Kimliği oluşturma.](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)

## <a name="view-return-values-for-functions"></a>İşlevler için dönüş değerlerini görüntüleme

İşlevlerinize göre dönüş değerlerini görüntülemek için, kodunuz boyunca adım adım **ilerlerken** Otomatikler penceresinde görünen işlevlere bakın. Bir işlevin dönüş değerini görmek için ilgilendiğinizi işlevin zaten yürütülür olduğundan emin olun (işlev çağrısında durdurulduysanız **F10'a** bir kez basın). Pencere kapalı ise, Otomatikler **penceresini açmak > Windows > Otomatikler'de** Hata **Ayıkla'ya** tıklayın.

![Otomatikler Penceresi](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Ayrıca, dönüş değerlerini görüntülemek için **Hemen penceresine** işlevler girebilirsiniz. (Anında Hata Ayıklama **kullanarak > Windows > açın.)**

![Anlık Pencere](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Ayrıca, İzle ve Hemen penceresinde  [gibi](../debugger/pseudovariables.md) sözde **değişkenleri** de kullanabilirsiniz. `$ReturnValue`

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Görselleştiricide dizeleri inceleme

Dizelerle çalışırken, biçimlendirilmiş dizenin tamamını görüntülemek yararlı olabilir. Düz metin, XML, HTML veya JSON dizesini görüntülemek için, dize değeri içeren bir değişkenin üzerine gelinken büyüteç simgesi ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") simgesine tıklayın.

![Dize Görselleştiricisi açma](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Dize görselleştirici, dize türüne bağlı olarak bir dizenin yanlış biçimlendirilmiş olup olmadığını bulamanıza yardımcı olabilir. Örneğin boş bir **Değer alanı,** dizenin görselleştirici türü tarafından tanınmaz olduğunu gösterir. Daha fazla bilgi için [bkz. Dize Görselleştiricisi İletişim Kutusu.](../debugger/string-visualizer-dialog-box.md)

![JSON Dize Görselleştiricisi](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Hata ayıklayıcı pencerelerinde görünen DataSet ve DataTable nesneleri gibi diğer birkaç tür için, yerleşik bir görselleştirici de açabilirsiniz.

## <a name="break-into-code-on-handled-exceptions"></a>Ele alınan özel durumlarda kodun içine girin

Hata ayıklayıcısı, iş alınemeyen özel durumlarda kodunuzla birlikte kırılır. Ancak, işlenmiş özel durumlar (örneğin, bir bloğun içinde oluşan özel durumlar) bir hata kaynağı olabilir ve bunların ne `try/catch` zaman oluştuğu hakkında araştırma yapmak istiyor olabilir. Hata ayıklayıcıyı, hem işilen özel durumlar için koda hem de Özel Durum Yapılandırma iletişim kutusundaki seçenekleri **yapılandırarak Ayarlar** yapılandırabilirsiniz. Bu iletişim kutusunu açmak için Hata **Ayıkla'> Windows > Özel Durum Ayarlar.**

Özel **durum Ayarlar** iletişim kutusu, hata ayıklayıcıya belirli özel durumlarda kodun içinde hata ayıklamasını söylemenizi sağlar. Aşağıdaki çizimde, hata ayıklayıcı her oluştuğunda kodunuzda `System.NullReferenceException` kırılır. Daha fazla bilgi için [bkz. Özel durumları yönetme.](../debugger/managing-exceptions-with-the-debugger.md)

![Özel Ayarlar İletişim Kutusu](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Kilitlenmeler ve yarış durumlarını ayıklama

Çok iş parçacıklı uygulamalarda sık karşılaşılan sorun türlerde hata ayıklamanız gerekirse, hata ayıklama sırasında genellikle iş parçacıklarının konumunu görüntülemeye yardımcı olur. Bunu Kolayca Kaynakta İş Parçacıklarını **Göster düğmesini kullanarak yapabilirsiniz.**

#### <a name="to-show-threads-in-your-source-code"></a>İş parçacıklarını kaynak kodunda göstermek için

1. Hata ayıklama sırasında Hata Ayıklama araç **çubuğundaki Kaynakta** İş Parçacıklarını Göster düğmesine ![Kaynakta](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") İş **Parçacıklarını Göster'e** tıklayın.

2. Pencerenin sol tarafındaki oluklara bakın. Bu satırda, iki iş *parçacığına benzeyen* bir  ![iş](../debugger/media/dbg-thread-marker.png "ThreadMarker") parçacığı işaretçisi simgesi İş Parçacığı İşaretçisi'ni görüyorsunuz. İş parçacığı işaretçisi, bir iş parçacığının bu konumda durdurulmuş olduğunu gösterir.

    Bir iş parçacığı işaretçisi bir kesme noktası tarafından kısmen hataya neden olabilir.

3. İşaretçiyi iş parçacığı işaretçisinin üzerine gelin. Bir DataTip görüntülenir. DataTip, durdurulan her iş parçacığı için ad ve iş parçacığı kimliği numarasını söyler.

    İş parçacıklarının konumunu Paralel Yığınlar penceresinde [de görüntüebilirsiniz.](../debugger/get-started-debugging-multithreaded-apps.md)

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Web hizmetleri ve ağ kaynakları (UWP) için yük inceleme

UWP uygulamaları içinde, API kullanılarak gerçekleştirilen ağ işlemlerini analiz `Windows.Web.Http` edersiniz. Web hizmet ve ağ kaynaklarda hata ayıklamaya yardımcı olmak için bu aracı kullanabilirsiniz. Aracı kullanmak için Hata **ayıkla'> Performans Profili Oluşturucu.** **Ağ'ı** ve ardından Başlat'ı **seçin.** Uygulamanıza, kullanan senaryoyu gidin ve ardından `Windows.Web.Http` Raporu oluşturmak için Koleksiyonu **durdur'a** seçin.

![Ağ Kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Daha fazla ayrıntı görüntülemek için özet görünümünde bir işlem seçin.

![Ağ Kullanımı aracında ayrıntılı bilgiler](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Daha fazla bilgi için [bkz. Ağ Kullanımı.](../profiling/network-usage.md)
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Hata ayıklayıcının uygulamanıza nasıl ekli olduğu hakkında daha fazla bilgi (C#, C++, Visual Basic, F#)

Çalışan uygulamanıza eklemek için hata ayıklayıcısı hata ayıklamaya çalıştığınız uygulamanın tam olarak aynı derlemesi için oluşturulan sembol (.pdb) dosyalarını yükler. Bazı senaryolarda sembol dosyaları hakkında biraz bilgi sahibi olmak yararlı olabilir. Modüller penceresini Visual Studio sembol dosyalarını nasıl **yükleyen bir dosya olduğunu inceebilirsiniz.**

Hata ayıklama **sırasında Modüller** penceresini açmak için Modüllerde **Hata Ayıkla'> Windows > seçin.** Modüller **penceresi,** hata ayıklayıcının kullanıcı kodu olarak hangi modülleri veya [*Kodum*](../debugger/just-my-code.md)olarak işlemektedir ve modülün sembol yükleme durumunu size söyler. Çoğu senaryoda, hata ayıklayıcı kullanıcı kodu için sembol dosyalarını otomatik olarak bulur, ancak .NET koduna, sistem koduna veya üçüncü taraf kitaplık koduna gitmek (veya hata ayıklamak) için doğru sembol dosyalarını almak için ek adımlar gerekir.

![Modüller penceresinde sembol bilgilerini görüntüleme](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Sembol bilgilerini doğrudan Modüller penceresinden **yüklemek için sağ** tıklar ve Sembolleri Yükle'ye **tıklarsınız.**

Bazen, uygulama geliştiricileri uygulamaları eşleşen sembol dosyaları olmadan (ayak izini azaltmak için) iletir, ancak daha sonra yayımlanan bir sürümde hata ayıklamak için derleme için eşleşen sembol dosyalarının bir kopyasını tutabilirsiniz.

Hata ayıklayıcının kodu kullanıcı kodu olarak nasıl sınıflara ayırarak olduğunu bulmak için bkz. [Yalnızca kendi kodum.](../debugger/just-my-code.md) Sembol dosyaları hakkında daha fazla bilgi için hata ayıklayıcısında sembol [(.pdb)](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)ve kaynak Visual Studio bakın.

## <a name="learn-more"></a>Daha fazla bilgi edinin

Ek ipuçları ve püf noktaları ve daha ayrıntılı bilgi için şu blog gönderilerini ziyaret edin:

- [Visual Studio'de hata ayıklama için 7 daha az bilinen saldırı](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio'de 7 gizli gem](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Ayrıca bkz.

[Klavye Kısayolları](../ide/productivity-shortcuts.md)
