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
ms.openlocfilehash: 55beb1375dd4f1befa8a18ee404dbc2b0e10d0f8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081024"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Visual Studio'İpuçları Hata Ayıklayıcı için Üretkenlik Ve Püf Noktaları hakkında Visual Studio

Hata ayıklayıcısıyla ilgili üretkenlik ipuçları ve püf noktaları hakkında bilgi edinmek Visual Studio okuyun. Hata ayıklayıcının temel özelliklerine bakmak için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md) Bu konu başlığında, özellik turunda yer alan bazı alanlar açıklanmıştır.

## <a name="pin-data-tips"></a>Veri ipuçlarını sabitleme

Hata ayıklama sırasında sık sık veri ipuçlarının üzerine gelmeniz, kendinize hızlı erişim vermek için değişkenin veri ipucuna sabitlemek istiyor olabilir. Değişken yeniden başlatıldıktan sonra bile sabitlenmiş olarak kalır. Veri ipucu sabitlemek için üzerine gelinken sabitleme simgesine tıklayın. Birden çok değişkeni sabitleyebilirsiniz.

![Veri İpucu Sabitleme](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Kodunuzu düzenleyin ve hata ayıklamaya devam edin (C#, VB, C++)

Uygulama tarafından desteklenen çoğu Visual Studio, hata ayıklama oturumunun ortasında kodunuzu düzenleyebilir ve hata ayıklamaya devam edersiniz. Bu özelliği kullanmak için hata ayıklayıcıda duraklatılmış durumdayken imlecinizi kullanarak kodunuzla tıklayın, düzenlemeler yapmak ve hata ayıklamaya devam etmek için **F5**, **F10** veya **F11** tuşuna basın.

![Düzenleme ve hata ayıklamaya devam](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Özelliği kullanma ve özellik sınırlamaları hakkında daha fazla bilgi için bkz. [Düzenle ve Devam Edin.](../debugger/edit-and-continue.md)

## <a name="edit-xaml-code-and-continue-debugging"></a>XAML kodunu düzenleme ve hata ayıklamaya devam

Hata ayıklama oturumu sırasında XAML kodunu değiştirmek için bkz. XAML kodunu kullanarak [XAML kodu yazma ve hata XAML Çalışırken Yeniden Yükleme.](../xaml-tools/xaml-hot-reload.md)

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Yeniden oluşturması zor olan hata ayıklama sorunları

Uygulamanıza belirli bir durumu yeniden oluşturmak zor veya zaman alan bir durumsa, koşullu kesme noktasının kullanımının yardımcı olup olmadığını göz önünde bulundurabilirsiniz. Uygulama istenen [durumuna](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) girene kadar (örneğin, değişkenin hatalı verileri depolması durumu) uygulama kodunuza girmekten kaçınmak için koşullu kesme noktaları ve filtre kesme noktaları kullanabilirsiniz. koşulları ifadeleri, filtreleri, isabet sayılarını ve diğer tüm ifadeleri kullanarak ayarlayabilirsiniz.

#### <a name="to-create-a-conditional-breakpoint"></a>Koşullu kesme noktası oluşturmak için

1. Bir kesme noktası simgesine (kırmızı top) sağ tıklayın ve Koşullar'ı **seçin.**

2. Kesme **noktası Ayarlar** bir ifade yazın.

    ![Koşullu Kesme Noktası](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Başka bir koşul türüyle ilgileniyorsanız  Kesme  Noktası İletişim Kutusunda Koşullu ifade yerine Filtrele'yi **Ayarlar** ve ardından filtre ipuçlarını izleyin.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Verileri hata ayıklayıcıda gösterecek şekilde yapılandırma

C#, Visual Basic ve C++ (yalnızca C++/CLI kodu) için, hata ayıklayıcıya [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) özniteliğini kullanarak hangi bilgileri göster gösterebilirsiniz. C++ kodu için aynı şeyi [Natvis görselleştirmelerini kullanarak da yapabiliriz.](create-custom-views-of-native-objects.md)

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

Hata ayıklayıcı bir kod satırı üzerinde duraklatılmışken, sol tarafta sarı ok işaretçisini almak için fareyi kullanın. Sarı ok işaretçisini kod yürütme yolundaki farklı bir noktaya taşıma. Ardından uygulamayı çalıştırmaya devam etmek için F5 veya bir adım komutu kullanın.

![Yürütme İşaretçisini Taşıma](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Yürütme Işaretçisini taşı")

Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etmek veya hata ayıklayıcıyı yeniden başlatmadan kodu yeniden çalıştırma gibi şeyler yapabiliriz.

> [!WARNING]
> Genellikle bu özellikle dikkatli olmalısınız ve araç ipucunda bir uyarı görüyorsunuz. Başka uyarılar da görebilir. İşaretçiyi hareket ettiren uygulama önceki bir uygulama durumuna geri döndürülebilir.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Kapsam dışında bir nesneyi izleme (C#, Visual Basic)

İzleme penceresi gibi hata ayıklayıcı pencerelerini kullanarak değişkenleri görüntülemek **kolaydır.** Ancak, bir değişken İzleme penceresinde kapsamın **dışında** olduğunda, değişkenin gri renkte olduğunu farkedebilirsiniz. Bazı uygulama senaryolarında değişken kapsam dışında olsa bile değişkenin değeri değişebilir ve bunu yakından izlemek (örneğin, bir değişken atık toplanabilir) istiyor olabilir. İzleme penceresinde değişkeni için bir Nesne Kimliği oluşturarak **izleyebilirsiniz.**

#### <a name="to-create-an-object-id"></a>Nesne kimliği oluşturmak için

1. Izlemek istediğiniz değişkenin yakınında bir kesme noktası ayarlayın.

2. Hata ayıklayıcısını (**F5**) ve kesme noktası üzerinde durdurun.

3. Değişkeni Yereller  penceresinde bulun ( Yereller'de **> Windows >** ayıkla), değişkene sağ tıklayın ve Nesne Kimliğini **Yapma'yı seçin.**

    ![Nesne Kimliği oluşturma](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. YerelLer penceresinde **$** artı bir sayı görüyor **gerekir.** Bu değişken nesne kimliğidir.

5. Nesne kimliği değişkenine sağ tıklayın ve İzleme **Ekle'yi seçin.**

Daha fazla bilgi için [bkz. Nesne Kimliği oluşturma.](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)

## <a name="view-return-values-for-functions"></a>İşlevler için dönüş değerlerini görüntüleme

İşlevlerinize göre dönüş değerlerini görüntülemek için, kodunuz boyunca adım adım **ilerlerken** Otomatikler penceresinde görünen işlevlere bakın. Bir işlevin dönüş değerini görmek için ilgilendiğinizi işlevin zaten yürütülür olduğundan emin olun (işlev çağrısında durdurulduysanız **F10'a** bir kez basın). Pencere kapalı ise, Otomatikler **penceresini açmak > Windows > Otomatikler'de** hata **ayıkla'ya** tıklayın.

![Otomatikler Penceresi](../debugger/media/dbg-tips-autos-window.png "Oto penceresi")

Ayrıca, dönüş değerlerini görüntülemek için **Hemen penceresine** işlevler girebilirsiniz. (Anında Hata Ayıklama **kullanarak > Windows > açın.)**

![Anlık Pencere](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Ayrıca, İzle [ve Hemen](../debugger/pseudovariables.md) penceresinde  gibi sözde **değişkenleri** de `$ReturnValue` kullanabilirsiniz.

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Görselleştiricide dizeleri inceleme

Dizelerle çalışırken, biçimlendirilmiş dizenin tamamını görüntülemek yararlı olabilir. Düz metin, XML, HTML veya JSON dizesini görüntülemek için, dize değeri içeren bir değişkenin üzerine gelinken büyüteç simgesi ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") simgesine tıklayın.

![Dize Görselleştiricisi açma](../debugger/media/dbg-tips-string-visualizers.png "Openstringgörselleştiricisi")

Dize görselleştirici, dize türüne bağlı olarak bir dizenin yanlış biçimlendirilmiş olup olmadığını bulamanıza yardımcı olabilir. Örneğin boş bir **Değer alanı,** dizenin görselleştirici türü tarafından tanınmaz olduğunu gösterir. Daha fazla bilgi için [bkz. Dize Görselleştiricisi İletişim Kutusu.](../debugger/string-visualizer-dialog-box.md)

![JSON Dize Görselleştiricisi](../debugger/media/dbg-tips-string-visualizer-json.png "Jsonstringgörselleştiricisi")

Hata ayıklayıcı pencerelerinde görünen DataSet ve DataTable nesneleri gibi diğer birkaç tür için, yerleşik bir görselleştirici de açabilirsiniz.

## <a name="break-into-code-on-handled-exceptions"></a>Ele alınan özel durumlarda kodun içine girin

Hata ayıklayıcısı, iş alınemeyen özel durumlarda kodunuzla birlikte kırılır. Ancak, işlenmiş özel durumlar (örneğin, bir bloğun içinde oluşan özel durumlar) bir hata kaynağı olabilir ve bunların ne `try/catch` zaman oluştuğu hakkında araştırma yapmak istiyor olabilir. Hata ayıklayıcıyı, hem işilen özel durumlar için koda hem de Özel Durum Bilgileri iletişim kutusundaki seçenekleri **yapılandırarak Ayarlar** yapılandırabilirsiniz. Bu iletişim kutusunu açmak için Hata **ayıkla'> Windows > Özel Durum Ayarlar.**

Özel **durum Ayarlar** iletişim kutusu, hata ayıklayıcıya belirli özel durumlarda kodun içinde hata ayıklamasını söylemenizi sağlar. Aşağıdaki çizimde, hata ayıklayıcı her oluştuğunda kodunuzda `System.NullReferenceException` hata ayıklayıcıyı kırar. Daha fazla bilgi için [bkz. Özel durumları yönetme.](../debugger/managing-exceptions-with-the-debugger.md)

![Özel Ayarlar Özel Durum İletişim Kutusu](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Kilitlenmeler ve yarış durumlarını ayıklama

Çok iş parçacıklı uygulamalarda sık karşılaşılan sorun türlerde hata ayıklamanız gerekirse, hata ayıklama sırasında genellikle iş parçacıklarının konumunu görüntülemeye yardımcı olur. Bunu, Kaynakta İş Parçacıklarını **Göster düğmesini kullanarak kolayca yapabilirsiniz.**

#### <a name="to-show-threads-in-your-source-code"></a>Kaynak kodunda iş parçacıklarını göstermek için

1. Hata ayıklama sırasında Hata Ayıklama araç **çubuğundaki Kaynakta** İş Parçacıklarını Göster düğmesine ![Kaynakta](../debugger/media/dbg-multithreaded-show-threads.png "Threadişaretleyici") İş **Parçacıklarını Göster'e** tıklayın.

2. Pencerenin sol tarafındaki oluklara bakın. Bu satırda, iki iş *parçacığına benzeyen*  ![bir iş](../debugger/media/dbg-thread-marker.png "Threadişaretleyici") parçacığı işaretçisi simgesi İş Parçacığı İşaretçisi'ni görüyorsunuz. İş parçacığı işaretçisi, bir iş parçacığının bu konumda durdurulmuş olduğunu gösterir.

    Bir iş parçacığı işaretçisi bir kesme noktası tarafından kısmen hataya neden olabilir.

3. İşaretçiyi iş parçacığı işaretçisinin üzerine gelin. Bir DataTip görüntülenir. DataTip, durdurulan her iş parçacığı için ad ve iş parçacığı kimliği numarasını söyler.

    İş parçacıklarının konumunu Paralel Yığınlar penceresinde [de görüntüebilirsiniz.](../debugger/get-started-debugging-multithreaded-apps.md)

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Web hizmetleri ve ağ kaynakları (UWP) için yük inceleme

UWP uygulamaları içinde, API kullanılarak gerçekleştirilen ağ işlemlerini analiz `Windows.Web.Http` edersiniz. Web hizmet ve ağ kaynaklarda hata ayıklamaya yardımcı olmak için bu aracı kullanabilirsiniz. Aracı kullanmak için Hata **ayıkla'> Performans Profili Oluşturucu.** **Ağ'ı** ve ardından Başlat'ı **seçin.** Uygulamanıza, kullanan senaryoyu gidin ve ardından `Windows.Web.Http` Raporu oluşturmak için Koleksiyonu **durdur'a** seçin.

![Ağ Kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Daha fazla ayrıntı görüntülemek için Özet görünümünde bir işlem seçin.

![Ağ kullanımı aracında ayrıntılı bilgiler](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Daha fazla bilgi için bkz. [ağ kullanımı](../profiling/network-usage.md).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>hata ayıklayıcının uygulamanıza nasıl ilişi hakkında daha fazla bilgi edinin (C#, C++, Visual Basic, F #)

Çalışan uygulamanıza iliştirmek için hata ayıklayıcı, hata ayıklamaya çalıştığınız uygulamanın tam olarak aynı derlemesi için oluşturulan sembol (. pdb) dosyalarını yükler. Bazı senaryolarda sembol dosyalarının küçük bir bilgisi yararlı olabilir. **modüller** penceresini kullanarak Visual Studio sembol dosyalarını nasıl yüklediğini inceleyebilirsiniz.

hata ayıklama **> Windows > modüller**' i seçerek **modüller** penceresini açın. **Modüller** penceresi, hata ayıklayıcının Kullanıcı kodu veya [*kodum*](../debugger/just-my-code.md)olarak hangi modülleri olduğunu ve modülün sembol yükleme durumunu söyleyebilir. Çoğu senaryoda, hata ayıklayıcı Kullanıcı kodu için sembol dosyalarını otomatik olarak bulur, ancak .NET kodu, sistem kodu veya üçüncü taraf kitaplık kodu içine (veya hata ayıklama) geçmek istiyorsanız, doğru sembol dosyalarını almak için ek adımlar gereklidir.

![Modüller penceresinde sembol bilgilerini görüntüleme](../debugger/media/dbg-tips-modules-window.png "Viewsymbolınformation")

Sembol bilgilerini doğrudan **modüller** penceresinden, sağ tıklayıp **sembolleri yükle**' yi seçerek yükleyebilirsiniz.

Bazen, uygulama geliştiricileri, eşleşen sembol dosyaları olmadan (parmak izini azaltmak için) uygulamaları teslim eder, ancak daha sonra yayınlanan bir sürümün hatalarını ayıklayabilmeleri için eşleşen sembol dosyalarının bir kopyasını derleme için saklayın.

Hata ayıklayıcının kodu Kullanıcı kodu olarak sınıflandırdığı hakkında bilgi edinmek için bkz. [yalnızca kendi kodum](../debugger/just-my-code.md). sembol dosyaları hakkında daha fazla bilgi edinmek için bkz. [Visual Studio hata ayıklayıcı 'da sembol (. pdb) ve kaynak dosyaları belirtme](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Daha fazla bilgi edinin

Ek ipuçları ve püf noktaları ve daha ayrıntılı bilgi için şu blog gönderilerine bakın:

- [7 Visual Studio hata ayıklama için bilinen korsanlardan daha az](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio 'de 7 gizli Gems](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Ayrıca bkz.

[Klavye kısayolları](../ide/productivity-shortcuts.md)
