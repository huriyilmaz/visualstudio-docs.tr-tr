---
title: Hata ayıklamadaki ipuçları ve püf noktaları
description: Visual Studio hata ayıklayıcıtarafından desteklenen daha az bilinen özelliklerden bazıları hakkında bilgi edinin
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302219"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Visual Studio'da Debugger için Üretkenlik İpuçları ve Püf Noktaları öğrenin

Visual Studio hata ayıklama için birkaç üretkenlik ipucu ve püf noktasını öğrenmek için bu konuyu okuyun. Hata ayıklamanın temel özelliklerine bakmak için [hata ayıklama yada ilk bakışta](../debugger/debugger-feature-tour.md)bkz. Bu konu, biz özellik turu dahil olmayan bazı alanları kapsamaktadır.

## <a name="pin-data-tips"></a>Veri ipuçlarını sabitleme

Hata ayıklama sırasında sık sık veri ipuçlarıüzerinde gezinirseniz, kendinize hızlı erişim sağlamak için değişkenin veri ucunu sabitlemek isteyebilirsiniz. Değişken yeniden başladıktan sonra bile sabit kalır. Veri ipucunu sabitlemek için, üzerinde gezinirken pin simgesini tıklatın. Birden çok değişkeni sabitleyebilirsiniz.

![Veri İpucu Sabitleme](../debugger/media/dbg-tips-data-tips-pinned.png "SabitlemeDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Kodunuzu edin ve hata ayıklama devam (C#, VB, C++)

Visual Studio tarafından desteklenen çoğu dilde, hata ayıklama oturumunun ortasında kodunuzu düzenleme yapabilir ve hata ayıklama devam edebilirsiniz. Bu özelliği kullanmak için hata ayıklayıcıda duraklarken imlecinizle kodunuzu tıklatın, düzeltmeler yapın ve hata ayıklama devam etmek için **F5**, **F10**veya **F11** tuşuna basın.

![Hata ayıklamayı ve hata ayıklamayı yapmaya devam etme](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Özelliği kullanma ve özellik sınırlamaları hakkında daha fazla bilgi için [bkz.](../debugger/edit-and-continue.md)

## <a name="edit-xaml-code-and-continue-debugging"></a>XAML kodunu edin ve hata ayıklama devam edin

Hata ayıklama oturumu sırasında XAML kodunu değiştirmek için [bkz.](../xaml-tools/xaml-hot-reload.md)

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Yeniden oluşturulması zor hata ayıklama sorunları

Uygulamanızda belirli bir durumu yeniden oluşturmak zor veya zaman alıyorsa, koşullu bir kesme noktasının kullanılmasının yardımcı olup olmadığını düşünün. [Koşullu kesme noktaları](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) ve uygulama istenilen duruma girene kadar (değişkenin hatalı veri depoladığı durum gibi) uygulama kodunuzu girmemek için kesme noktalarını filtreleyebilirsiniz. İfadeleri, filtreleri, isabet sayılarını ve benzeri bilgileri kullanarak koşulları ayarlayabilirsiniz.

#### <a name="to-create-a-conditional-breakpoint"></a>Koşullu bir kesme noktası oluşturmak için

1. Bir kesme noktası simgesine (kırmızı top) sağ tıklayın ve **Koşullar'ı**seçin.

2. Kesme **Noktası Ayarları** penceresinde bir ifade yazın.

    ![Koşullu Kesme Noktası](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "KoşulluBreakpoint")

3. Başka bir koşul türüyle ilgileniyorsanız, **Kesme Noktası Ayarları** iletişim kutusunda **Koşullu ifade** yerine **Filtre'yi** seçin ve ardından filtre ipuçlarını izleyin.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Verileri hata ayıklamada gösterecek şekilde yapılandırın

C#, Visual Basic ve C++ (yalnızca C++/CLI kodu) için hata ayıklayıcıya [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) özniteliğini kullanarak hangi bilgilerin gösterilen bilgileri söyleyebilirsiniz. C++ kodu için aynı şeyi [Natvis görselleştirmelerini](create-custom-views-of-native-objects.md)kullanarak da yapabilirsiniz.

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

Hata ayıklayıcı bir kod satırında duraklatılmışken, soldaki sarı ok işaretçisini kapmak için fareyi kullanın. Sarı ok işaretçisini kod yürütme yolunda farklı bir noktaya taşıyın. Ardından uygulamayı çalıştırmaya devam etmek için F5 veya bir adım komutu kullanırsınız.

![Yürütme İşaretçisini Taşıma](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Yürütme İşaretçisini Taşıma")

Yürütme akışını değiştirerek, hata ayıklayıcıyı yeniden başlatmadan farklı kod yürütme yollarını sınamak veya kodu yeniden çalıştırmak gibi şeyler yapabilirsiniz.

> [!WARNING]
> Genellikle bu özellik ile dikkatli olmak gerekir ve araç ucunda bir uyarı bakın. Başka uyarılar da görebilirsiniz. İşaretçiyi taşımak, uygulamanızı daha önceki bir uygulama durumuna geri çeviremez.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Kapsam dışı nesneyi izleme (C#, Visual Basic)

**Watch** penceresi gibi hata ayıklama pencerelerini kullanarak değişkenleri görüntülemek kolaydır. Ancak, Bir değişken **İzleme Penceresinde** kapsam dışına çıktığında, gri renkte olduğunu fark edebilirsiniz. Bazı uygulama senaryolarında, değişken kapsam dışında olsa bile bir değişkenin değeri değişebilir ve bunu yakından izlemek isteyebilirsiniz (örneğin, bir değişken çöp toplanabilir). **Saati** penceresinde bunun için bir Nesne Kimliği oluşturarak değişkeni izleyebilirsiniz.

#### <a name="to-create-an-object-id"></a>Nesne kimliği oluşturmak için

1. İzlemek istediğiniz bir değişkenin yakınına bir kesme noktası ayarlayın.

2. Hata ayıklama **(F5)** başlatın ve kesme noktasında durun.

3. **Yereller** penceresinde **(Hata Ayıklama > Windows > Locals)** değişkeni bulun), değişkene sağ tıklayın ve **Nesne Kimliği Yap'ı**seçin.

    ![Nesne Kimliği Oluşturma](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. **Yerel ler** **$** penceresinde artı bir sayı görmelisiniz. Bu değişken nesne kimliğidir.

5. Nesne kimliği değişkenine sağ tıklayın ve **İzle ekle'yi**seçin.

Daha fazla bilgi için [bkz.](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)

## <a name="view-return-values-for-functions"></a>Fonksiyonlar için dönüş değerlerini görüntüleme

İşlevlerinizin iade değerlerini görüntülemek için, kodunuzda adım atarken Otomatik Ler penceresinde görünen **işlevlere** bakın. Bir işlevin geri dönüş değerini görmek için, ilgilendiğiniz işlevin zaten yürütüldüğünden emin olun (şu anda işlev çağrısında durdurulduysanız bir kez **F10** tuşuna basın). Pencere kapalıysa, **Otomatik Ler** penceresini açmak için Windows **> Otomatikler > Hata** Ayıklama'yı kullanın.

![Otomatik Pencere](../debugger/media/dbg-tips-autos-window.png "Otomatik Pencere")

Ayrıca, iade değerlerini görüntülemek için **Hemen** penceresine işlevleri girebilirsiniz. (Hata **Ayıklama > Windows > Immediate**kullanarak açın.)

![Komut Penceresi](../debugger/media/dbg-tips-immediate-window.png "Hemen Pencere")

**Watch** ve **Immediate** penceresinde de sözde `$ReturnValue` [değişkenler](../debugger/pseudovariables.md) kullanabilirsiniz.

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Dizeleri görselleştiricide inceleyin

Dizeleri ile çalışırken, biçimlendirilmiş dize tamamını görüntülemek yararlı olabilir. Düz bir metin, XML, HTML veya JSON dizesini görüntülemek için, dize değeri içeren bir değişkenin üzerinde gezinirken büyüteç simgesi ![VisualizerIcon'u](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") tıklatın.

![String Visualizer aç](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Bir dize görselleştiricisi, dize türüne bağlı olarak bir dizenin biçimsiz kalıp koluştuğunu bulmanıza yardımcı olabilir. Örneğin, boş bir **Değer** alanı dize görselleştirici türü tarafından tanınmadığını gösterir. Daha fazla bilgi için [String Visualizer İletişim Kutusu'na](../debugger/string-visualizer-dialog-box.md)bakın.

![JSON String Görselleştirici](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Hata ayıklama pencerelerinde görünen DataSet ve DataTable nesneleri gibi birkaç başka tür için yerleşik bir görselleştirici de açabilirsiniz.

## <a name="break-into-code-on-handled-exceptions"></a>İşlenen özel durumlar için kod alagirme

Hata ayıklayıcı işlenmemiş özel durumlar üzerinde kodunuza girer. Ancak, işlenen özel durumlar `try/catch` (blok içinde oluşan özel durumlar gibi) da hataların kaynağı olabilir ve bunlar oluştuğunda araştırmak isteyebilirsiniz. **Özel Durum Ayarları** iletişim kutusundaki seçenekleri yapılandırarak hata ayıklayıcıyı işlenen özel durumlar için koda girecek şekilde yapılandırabilirsiniz. **Hata Ayıklama > Windows > Özel Durum Ayarları'nı**seçerek bu iletişim kutusunu açın.

**Özel Durum Ayarları** iletişim kutusu, hata ayıklayıcıya belirli özel durumlar üzerinde kod alamasını söylemenizi sağlar. Aşağıdaki resimde, hata ayıklayıcı her `System.NullReferenceException` meydana geldiğinde kodunuzu ayırır. Daha fazla bilgi için [bkz.](../debugger/managing-exceptions-with-the-debugger.md)

![Özel Durum Ayarları İletişim Kutusu](../debugger/media/dbg-tips-exception-settings.png "Özel DurumAyarlarıDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Hata hata kilitlenmeleri ve yarış koşulları

Çok iş parçacığı olan uygulamalarda yaygın olan türde sorunları hata ayıklamanız gerekiyorsa, hata ayıklama sırasında iş parçacıklarının konumunu görüntülemek genellikle yardımcı olur. Bunu **Kaynak'taki İş Parçacıklarını Göster** düğmesini kullanarak kolayca yapabilirsiniz.

#### <a name="to-show-threads-in-your-source-code"></a>Kaynak kodunuzdaki iş parçacıklarını göstermek için

1. Hata ayıklama sırasında, **Hata Ayıklama** araç **çubuğunda Kaynak'ta** İş ![Parçacıklarını Göster](../debugger/media/dbg-multithreaded-show-threads.png "İş Parçacığı İşaretleyicisi") düğmesini tıklatın.

2. Pencerenin sol tarafındaki oluka bak. Bu satırda, iki bez iş parçacığına benzeyen bir *iş parçacığı* simgesi İş ![Parçacığı İşaretçisi](../debugger/media/dbg-thread-marker.png "İş Parçacığı İşaretleyicisi") görürsünüz. İş parçacığı işaretçisi, bu konumda bir iş parçacığının durdurulduğunu gösterir.

    Bir iş parçacığı işaretçisinin bir kesme noktası tarafından kısmen gizlenebileceğine dikkat edin.

3. İşaretçiyi iş parçacığı işaretçisinin üzerine tover. Bir DataTip görüntülenir. DataTip, durdurulan her iş parçacığı için ad ve iş parçacığı kimliği numarasını söyler.

    [Paralel Yığınlar penceresinde](../debugger/get-started-debugging-multithreaded-apps.md)iş parçacıklarının konumunu da görüntüleyebilirsiniz.

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Web hizmetleri ve ağ kaynakları (UWP) için taşıma yüklerini inceleyin

UWP uygulamalarında, `Windows.Web.Http` API kullanılarak gerçekleştirilen ağ işlemlerini çözümleyebilirsiniz. Bu aracı, web hizmetlerini ve ağ kaynaklarını hata ayıklamaya yardımcı olmak için kullanabilirsiniz. Aracı kullanmak için **Hata Ayıklama > Performans Profilleyicisi'ni**seçin. **Ağ'ı**seçin ve ardından **Başlat'ı**seçin. Uygulamanızda, raporu kullanan `Windows.Web.Http`senaryoyu gözden geçirin ve ardından raporu oluşturmak için Koleksiyonu **Durdur'u** seçin.

![Ağ Kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "AğKullanımıProfTool")

Daha fazla ayrıntı görüntülemek için özet görünümünde bir işlem seçin.

![Ağ Kullanımı aracında ayrıntılı bilgi](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Daha fazla bilgi için [Ağ Kullanımı'na](../profiling/network-usage.md)bakın.
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Hata ayıklamanın uygulamanıza nasıl ekolduğunu daha iyi öğrenin (C#, C++, Visual Basic, F#)

Çalışan uygulamanıza eklemek için hata ayıklama simgesi (.pdb) dosyaları, hata ayıklamaya çalıştığınız uygulamanın tam olarak aynı yapısı için oluşturulur. Bazı senaryolarda, sembol dosyaları hakkında biraz bilgi yararlı olabilir. Visual Studio'nun **Modüller** penceresini kullanarak sembol dosyalarını nasıl yüklediği incelenebilirsiniz.

**Hata ayıklama > Windows > Modülleri**seçerek hata ayıklama sırasında **Modüller** penceresini açın. **Modüller** penceresi, hata ayıklayıcının kullanıcı kodu veya [*Kodum*](../debugger/just-my-code.md)olarak hangi modülleri tedavi ettiğini ve modülün sembol yükleme durumunu size söyleyebilir. Çoğu senaryoda hata ayıklayıcı kullanıcı kodu için simge dosyaları otomatik olarak bulur, ancak .NET koduna, sistem koduna veya üçüncü taraf kitaplık koduna adım atmak (veya hata ayıklamak) istiyorsanız, doğru sembol dosyalarını almak için ek adımlar gerekir.

![Modüller penceresinde sembol bilgilerini görüntüleme](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Sembol bilgilerini doğrudan **Modüller** penceresinden yükleyerek sağ tıklayıp **Yük Sembolleri'ni**seçebilirsiniz.

Bazen, uygulama geliştiricileri uygulamaları eşleşen sembol dosyaları olmadan (ayak izini azaltmak için) göndermez, ancak daha sonra yayımlanan bir sürümü hata ayıklamak için yapı için eşleşen sembol dosyalarının bir kopyasını saklar.

Hata ayıklayıcının kodu kullanıcı kodu olarak nasıl sınıflandırdığını öğrenmek için [Yalnızca Kodum'a](../debugger/just-my-code.md)bakın. Sembol dosyaları hakkında daha fazla bilgi edinmek için [Visual Studio hata ayıkcısındaki simge (.pdb) ve kaynak dosyaları belirt'e](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)bakın.

## <a name="learn-more"></a>Daha fazla bilgi edinin

Ek ipuçları ve püf noktaları ve daha ayrıntılı bilgi için şu blog gönderilerine bakın:

- [Visual Studio hata ayıklama için 7 daha az bilinen kesmek](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio'da 7 gizli mücevher](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Ayrıca bkz.

[Klavye Kısayolları](../ide/productivity-shortcuts.md)
