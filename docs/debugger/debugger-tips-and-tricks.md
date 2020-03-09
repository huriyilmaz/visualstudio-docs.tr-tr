---
title: İpuçları ve püf noktaları hata ayıklayıcısı
description: Visual Studio hata ayıklayıcı tarafından desteklenen daha az bilinen özelliklerinden bazıları hakkında bilgi edinin
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409348"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Hata Ayıklayıcı'Visual Studio için üretkenlik ipuçları ve püf noktaları öğrenin

Visual Studio hata ayıklayıcı için birkaç üretkenlik ipuçları ve püf noktaları öğrenmek için bu konuyu okuyun. Hata ayıklayıcının temel özelliklerine bakmak için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md). Bu konu başlığında özellik turu dahil edilmeyen bazı alanlar biz karşılarız.

## <a name="pin-data-tips"></a>PIN veri ipuçları

Sık hata ayıklama sırasında veri ipuçları gelin, değişken kendiniz hızlı erişim vermek için veri ipucu sabitlemek isteyebilirsiniz. Değişkeni yeniden başlatıldıktan sonra bile sabitlenmiş kalır. Veri ipucu sabitlemek için üzerine gelindiğinde Raptiye simgesine tıklayın. Birden fazla değişken sabitleyebilirsiniz.

![Veri Ipucunu sabitleme](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Kodunuzu düzenleyin ve (C#, VB, C++) hata ayıklamaya devam et

Visual Studio tarafından desteklenen çoğu dillerde hata ayıklama oturumu ortasında kodunuzu düzenleyin ve hata ayıklamaya devam et. Bu özelliği kullanmak için, hata ayıklayıcıda duraklama, düzenleme yapın ve hata ayıklamaya devam etmek için **F5**, **F10**veya **F11** tuşuna basın.

![Düzenle ve hata ayıklamayı Sürdür](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Özelliği ve özellik sınırlamalarını kullanma hakkında daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>XAML kodunu Düzenle ve hata ayıklamaya devam et

Bir hata ayıklama oturumu sırasında XAML kodunu değiştirmek için bkz. xaml [üzerinde çalışan xaml kodunu yazma ve hata ayıklama xaml çalışırken yeniden yükleme](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Yeniden oluşturulması zor olan sorunlarında hata ayıklama

Zor veya uygulamanızda belirli bir durumu yeniden oluşturmak harcanan zamanı ortadan kaldırır, koşullu kesme noktası kullanımı yardımcı olup olmadığını düşünün. Uygulama istenen bir duruma girene kadar (örneğin, bir değişkenin hatalı verileri depolayan bir durum gibi) uygulama kodunuzun kesilmesini önlemek için [koşullu kesme noktaları](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) ve filtre kesme noktaları kullanabilirsiniz. İfadeler, filtreler, isabet sayılarını vb. kullanarak koşulları ayarlayabilirsiniz.

#### <a name="to-create-a-conditional-breakpoint"></a>Koşullu kesme noktası oluşturmak için

1. Kesme noktası simgesine (kırmızı top) sağ tıklayın ve **koşullar**' ı seçin.

2. **Kesme noktası ayarları** penceresinde bir ifade yazın.

    ![Koşullu kesme noktası](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Başka bir tür koşulla ilgileniyorsanız, **kesme noktası ayarları** Iletişim kutusunda **koşullu ifade** yerine **filtre** ' yi seçin ve ardından filtre ipuçlarını izleyin.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Hata ayıklayıcıda gösterilecek verileri yapılandırın

, C#Visual Basic ve C++ (C++yalnızca/CLI kodu) için, hata ayıklayıcısına [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) özniteliğini kullanarak hangi bilgilerin gösterileceğini söyleyebilirsiniz. Kod C++ Için, [Natvis görselleştirmelerini](create-custom-views-of-native-objects.md)kullanarak aynı yapabilirsiniz.

## <a name="change-the-execution-flow"></a>Yürütme akışı değiştirme

Hata ayıklayıcısı ile duraklatılmış bir kod satırının sol taraftaki sarı ok işaretçi almak için fareyi kullanın. Başka bir noktada kod yürütme yolunda sarı ok işaretçiyi taşıyın. Ardından uygulamayı çalıştırmaya devam etmek için F5'e ya da bir adımı komutunu kullanın.

![Yürütme Işaretçisini taşı](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Yürütme Işaretçisini taşı")

Yürütme akışı değiştirerek farklı kod yürütme yolları test veya hata ayıklayıcı yeniden başlatmadan kodu yeniden gibi işlemler yapabilirsiniz.

> [!WARNING]
> Genelde bu özellikle dikkat etmek gerekir ve araç ipucunda bir uyarı görürsünüz. Çok diğer uyarılar görebilirsiniz. İşaretçiyi taşıma uygulamanızı daha önceki bir uygulama durumuna geri alınamaz.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>İzleme kapsamını nesneyi (C#, Visual Basic)

**İzleme** penceresi gibi hata ayıklayıcı pencerelerini kullanarak değişkenleri görüntülemek kolaydır. Ancak, bir değişken **izleme** penceresindeki kapsam dışına geçtiğinde, gri olduğunu fark edebilirsiniz. Bazı uygulama senaryolarında, değişken kapsam dışında olsa bile değişkenin değeri değişebilir ve bunu yakından izlemek isteyebilirsiniz (örneğin, bir değişken atık olarak toplanarak). Bu değişkeni, **izleme** penceresinde BIR nesne kimliği oluşturarak izleyebilirsiniz.

#### <a name="to-create-an-object-id"></a>Bir nesne kimliği oluşturmak için

1. İzlemek istediğiniz değişken yakın bir kesme noktası ayarlayın.

2. Hata ayıklayıcıyı (**F5**) başlatın ve kesme noktasında durun.

3. **Yereller** penceresinde değişkeni bulun (**hata ayıklama > Windows > Yereller**), değişkenine sağ tıklayın ve **nesne kimliğini yap**' ı seçin.

    ![Nesne KIMLIĞI oluşturma](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. **Yereller** penceresinde bir **$** ve bir sayı görmeniz gerekir. Bu değişken nesne kimliğidir.

5. Nesne KIMLIĞI değişkenine sağ tıklayın ve **Gözcü Ekle**' yi seçin.

Daha fazla bilgi için bkz. [nesne kimliği oluşturma](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>İşlevlerine yönelik dönüş değerlerini görüntüleme

İşlevlerinizin dönüş değerlerini görüntülemek için, kodunuzla adımlarken, **oto** penceresinde görüntülenen işlevlere bakın. Bir işlevin dönüş değerini görmek için, ilgilendiğiniz işlevin zaten çalıştırılmış olduğundan emin olun (işlev çağrısında halen durduysanız **F10** tuşuna basın). Pencere kapalıysa, **hata ayıklama > Windows > oto** ' ı kullanarak **oto** penceresini açın.

![Oto penceresi](../debugger/media/dbg-tips-autos-window.png "Oto penceresi")

Ayrıca, dönüş değerlerini görüntülemek için **komut** penceresine işlevler girebilirsiniz. ( **Hata ayıklama > Windows > anında**kullanarak açın.)

![Komut Penceresi](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Ayrıca, **izleme** ve **anında** penceresinde, `$ReturnValue`gibi [sözde değişkenler](../debugger/pseudovariables.md) de kullanabilirsiniz.

## <a name="string_visualizer"></a>Görselleştirici içindeki dizeleri İnceleme

Dizeleri ile çalışırken, biçimlendirilmiş dizenin tamamını görüntülemek yararlı olabilir. Düz metin, XML, HTML veya JSON dizesini görüntülemek için, bir dize değeri içeren bir değişken üzerine gelindiğinde büyüteç simgesini ![Visualizersimgesine](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") tıklayın.

![Dize görselleştiricisi açın](../debugger/media/dbg-tips-string-visualizers.png "Openstringgörselleştiricisi")

Dize Görselleştirici bir dize dize türüne bağlı olarak biçimlendirilmiş olup bulmanıza yardımcı olabilir. Örneğin, boş bir **değer** alanı, dizenin Görselleştirici türü tarafından tanınmadığını gösterir. Daha fazla bilgi için bkz. [dize görselleştiricisi Iletişim kutusu](../debugger/string-visualizer-dialog-box.md).

![JSON dize görselleştiricisi](../debugger/media/dbg-tips-string-visualizer-json.png "Jsonstringgörselleştiricisi")

Hata ayıklayıcı penceresinde görünen veri kümesi ve DataTable nesneleri gibi diğer diğer türler için de bir yerleşik görselleştiricisi açabilirsiniz.

## <a name="break-into-code-on-handled-exceptions"></a>Koda işlenen özel durumlar üzerinde kesme

İşlenmeyen özel durumları hakkında kodunuza hata ayıklayıcı keser. Ancak, işlenen özel durumlar (bir `try/catch` bloğu içinde oluşan özel durumlar gibi) hata kaynağı olabilir ve ne zaman meydana geldiğinde araştırmak isteyebilirsiniz. Hata ayıklayıcıyı işlenmiş özel durumlar için koda bölmek ve **özel durum ayarları** iletişim kutusundaki seçenekleri yapılandırmak için yapılandırabilirsiniz. **Hata ayıkla > Windows > özel durum ayarları**' nı seçerek bu iletişim kutusunu açın.

**Özel durum ayarları** iletişim kutusu, hata ayıklayıcıya belirli özel durumlarda koda bölünmeyle karşılaşmalarını sağlar. Aşağıdaki çizimde, bir `System.NullReferenceException` her gerçekleştiğinde hata ayıklayıcı kodunuzda kesilir. Daha fazla bilgi için bkz. [özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md).

![Özel durum ayarları Iletişim kutusu](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Hata ayıklama Kilitlenmeler ve yarış durumları

Tür birden çok iş parçacıklı uygulamalar için ortak olan sorunları hata ayıklamak ihtiyacınız varsa, bunu genellikle hata ayıklama sırasında iş parçacığı konumunu görüntülemek için yardımcı olur. Bunu **kaynak Içinde Iş parçacıklarını göster** düğmesini kullanarak kolayca yapabilirsiniz.

#### <a name="to-show-threads-in-your-source-code"></a>İş parçacığı kaynak kodunuzu göstermek için

1. Hata ayıklama sırasında **hata ayıklama** araç ![çubuğunda kaynak bölümünde](../debugger/media/dbg-multithreaded-show-threads.png "Threadişaretleyici") iş parçacıklarını **göster** düğmesine tıklayın.

2. Pencerenin sol tarafındaki cilt payını bakın. Bu satırda, iki kumaş iş parçacığına benzer bir *iş parçacığı işaretleyici* simgesi ![iş parçacığı işaretçisi](../debugger/media/dbg-thread-marker.png "Threadişaretleyici") görürsünüz. İş parçacığı işaretçisi, bir iş parçacığı bu konuma durdurulduğunu gösterir.

    Bir iş parçacığı işaret kısmen bir kesme noktası tarafından altına gizlenmiş, dikkat edin.

3. İşaretçi iş parçacığı işaret gelin. Bir DataTip görünür. DataTip durdurulmuş her iş parçacığı için adı ve iş parçacığı kimlik numarasını belirtir.

    Ayrıca, iş parçacıklarının konumunu [Paralel Yığınlar penceresinde](../debugger/get-started-debugging-multithreaded-apps.md)görüntüleyebilirsiniz.

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Web hizmetleri ve ağ kaynaklarına (UWP) için yüklerini inceleyin

UWP uygulamalarında, `Windows.Web.Http` API kullanarak gerçekleştirilen ağ işlemlerini çözümleyebilirsiniz. Web hizmetleri ve ağ kaynaklarını hata ayıklama yardımcı olmak için bu aracı kullanabilirsiniz. Aracı kullanmak için **> performans profil oluşturucu hata ayıkla**' yı seçin. **Ağ**' ı seçin ve ardından **Başlat**' ı seçin. Uygulamanızda, `Windows.Web.Http`kullanan senaryoya gidin ve sonra raporu oluşturmak için **koleksiyonu durdur** ' u seçin.

![Ağ kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Bir işlem içinde Özet görünümünü için daha fazla ayrıntı'ı seçin.

![Ağ kullanımı aracında ayrıntılı bilgiler](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Daha fazla bilgi için bkz. [ağ kullanımı](../profiling/network-usage.md).
::: moniker-end

## <a name="modules_window"></a>Hata ayıklayıcının uygulamanıza nasıl ilişi hakkında daha fazla bilgi edinin (C#, C++, Visual Basic, F#)

Çalışan uygulamanıza eklemek için hata ayıklayıcının hata ayıklamaya çalıştığınız uygulama aynı tam derleme için oluşturulan sembol (.pdb) dosyalarını yükler. Sembol dosyalarının biraz bilgi bazı senaryolarda yararlı olabilir. Visual Studio 'Nun, **modüller** penceresini kullanarak sembol dosyalarını nasıl yüklediğini inceleyebilirsiniz.

Hata ayıklama **> Windows > modülleri**'Ni seçerek **modüller** penceresini açın. **Modüller** penceresi, hata ayıklayıcının Kullanıcı kodu veya [*kodum*](../debugger/just-my-code.md)olarak hangi modülleri olduğunu ve modülün sembol yükleme durumunu söyleyebilir. Çoğu senaryoda, hata ayıklayıcı Kullanıcı kodu için sembol dosyalarını otomatik olarak bulur, ancak .NET kodu, sistem kodu veya üçüncü taraf kitaplık kodu içine (veya hata ayıklama) geçmek istiyorsanız, doğru sembol dosyalarını almak için ek adımlar gereklidir.

![Modüller penceresinde sembol bilgilerini görüntüleme](../debugger/media/dbg-tips-modules-window.png "Viewsymbolınformation")

Sembol bilgilerini doğrudan **modüller** penceresinden, sağ tıklayıp **sembolleri yükle**' yi seçerek yükleyebilirsiniz.

Bazı durumlarda, uygulama geliştiricilerinin (ayak izini azaltmak için) eşleşen sembol dosyaları, yayımlanmış bir sürüm'e daha sonra debug derleme için bir kopyasını eşleşen sembol dosyalar tut ancak olmadan uygulamalar gönderin.

Hata ayıklayıcının kodu Kullanıcı kodu olarak sınıflandırdığı hakkında bilgi edinmek için bkz. [yalnızca kendi kodum](../debugger/just-my-code.md). Sembol dosyaları hakkında daha fazla bilgi edinmek için bkz. [Visual Studio hata ayıklayıcısında simge (. pdb) ve kaynak dosyaları belirtme](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Daha fazla bilgi edinin

Ek ipuçları ve püf noktaları ve daha ayrıntılı bilgi için şu blog postalarına bakın:

- [7 Visual Studio 'da hata ayıklama için bilinen korsanlardan daha az](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio 'da 7 gizli Gems](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Ayrıca bkz.

[Klavye Kısayolları](../ide/productivity-shortcuts.md)
