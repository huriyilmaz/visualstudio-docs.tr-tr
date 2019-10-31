---
title: Hata Ayıklayıcıdaki ipuçları ve püf noktaları
description: Visual Studio hata ayıklayıcısı tarafından desteklenen daha az bilinen özelliklerden bazıları hakkında bilgi edinin
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
ms.openlocfilehash: 70276b8ba4efb08b0a6a57dc48716bd608f0429a
ms.sourcegitcommit: bdccab4c2dbd50ea8adaaf88c69c9ca32db88099
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144750"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Visual Studio 'da hata ayıklayıcı için üretkenlik Ipuçları ve püf noktaları öğrenin

Visual Studio hata ayıklayıcısı için birkaç üretkenlik ipucu ve püf noktası öğrenmek için bu konuyu okuyun. Hata ayıklayıcının temel özelliklerine bakmak için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md). Bu konu başlığında, Özellik turuna dahil olmayan bazı bölümler ele alınmaktadır.

## <a name="pin-data-tips"></a>Veri sabitleme ipuçları

Hata ayıklama sırasında sıklıkla veri ipuçları üzerine geldiğinizde, hızlı erişim sağlamak için değişkenin veri ipucunu sabitlemek isteyebilirsiniz. Yeniden başlatıldıktan sonra bile değişken sabitlenmiş kalır. Veri ipucunu sabitlemek için, üzerine gelindiğinde sabitleme simgesine tıklayın. Birden çok değişkeni sabitleyebilir.

![Veri Ipucunu sabitleme](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Kodunuzu düzenleyin ve hata ayıklamaya devam edinC#(, vb C++,)

Visual Studio 'nun desteklediği çoğu dilde kodunuzu bir hata ayıklama oturumunun ortasında düzenleyebilir ve hata ayıklamaya devam edebilirsiniz. Bu özelliği kullanmak için, hata ayıklayıcıda duraklama, düzenleme yapın ve hata ayıklamaya devam etmek için **F5**, **F10**veya **F11** tuşuna basın.

![Düzenle ve hata ayıklamayı Sürdür](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Özelliği ve özellik sınırlamalarını kullanma hakkında daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>XAML kodunu Düzenle ve hata ayıklamaya devam et

Bir hata ayıklama oturumu sırasında XAML kodunu değiştirmek için bkz. xaml [üzerinde çalışan xaml kodunu yazma ve hata ayıklama xaml çalışırken yeniden yükleme](xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Yeniden oluşturulması zor olan sorunları ayıklayın

Uygulamanızda belirli bir durumu yeniden oluşturmak zor veya zaman alıyorsa, koşullu kesme noktası kullanmanın yardımcı olup olmadığını göz önünde bulundurun. Uygulama istenen bir duruma girene kadar (örneğin, bir değişkenin hatalı verileri depolayan bir durum gibi) uygulama kodunuzun kesilmesini önlemek için [koşullu kesme noktaları](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) ve filtre kesme noktaları kullanabilirsiniz. İfadeleri ifade, filtre, isabet sayısı vb. kullanarak belirleyebilirsiniz.

#### <a name="to-create-a-conditional-breakpoint"></a>Koşullu kesme noktası oluşturmak için

1. Kesme noktası simgesine (kırmızı top) sağ tıklayın ve **koşullar**' ı seçin.

2. **Kesme noktası ayarları** penceresinde bir ifade yazın.

    ![Koşullu kesme noktası](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Başka bir tür koşulla ilgileniyorsanız, **kesme noktası ayarları** Iletişim kutusunda **koşullu ifade** yerine **filtre** ' yi seçin ve ardından filtre ipuçlarını izleyin.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Hata ayıklayıcıda gösterilecek verileri yapılandırın

, C#Visual Basic ve C++ (C++yalnızca/CLI kodu) için, hata ayıklayıcısına [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) özniteliğini kullanarak hangi bilgilerin gösterileceğini söyleyebilirsiniz. Kod C++ Için, [Natvis görselleştirmelerini](create-custom-views-of-native-objects.md)kullanarak aynı yapabilirsiniz.

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

Kod satırında hata ayıklayıcı duraklatıldığında, sol taraftaki sarı ok işaretçisini almak için fareyi kullanın. Sarı ok işaretçisini kod yürütme yolundaki farklı bir noktaya taşıyın. Ardından, uygulamayı çalıştırmaya devam etmek için F5 veya Step komutunu kullanın.

![Yürütme Işaretçisini taşı](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Yürütme Işaretçisini taşı")

Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etme veya hata ayıklayıcıyı yeniden başlatmanıza gerek kalmadan kodu yeniden çalıştırma gibi işlemleri yapabilirsiniz.

> [!WARNING]
> Genellikle bu özellikle dikkatli olmanız ve araç ipucunda bir uyarı görmeniz gerekir. Diğer uyarıları da görebilirsiniz. İşaretçinin taşınması uygulamanızı önceki bir uygulama durumuna döndüremezsiniz.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Kapsam dışı bir nesneyi izleme (C#, Visual Basic)

**İzleme** penceresi gibi hata ayıklayıcı pencerelerini kullanarak değişkenleri görüntülemek kolaydır. Ancak, bir değişken **izleme** penceresindeki kapsam dışına geçtiğinde, gri olduğunu fark edebilirsiniz. Bazı uygulama senaryolarında, değişken kapsam dışında olsa bile değişkenin değeri değişebilir ve bunu yakından izlemek isteyebilirsiniz (örneğin, bir değişken atık olarak toplanarak). Bu değişkeni, **izleme** penceresinde BIR nesne kimliği oluşturarak izleyebilirsiniz.

#### <a name="to-create-an-object-id"></a>Bir nesne KIMLIĞI oluşturmak için

1. İzlemek istediğiniz bir değişkenin yakınında bir kesme noktası ayarlayın.

2. Hata ayıklayıcıyı (**F5**) başlatın ve kesme noktasında durun.

3. **Yereller** penceresinde değişkeni bulun (**hata ayıklama > Windows > Yereller**), değişkenine sağ tıklayın ve **nesne kimliğini yap**' ı seçin.

    ![Nesne KIMLIĞI oluşturma](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. **Yereller** penceresinde bir **$** ve bir sayı görmeniz gerekir. Bu değişken, nesne KIMLIĞIDIR.

5. Nesne KIMLIĞI değişkenine sağ tıklayın ve **Gözcü Ekle**' yi seçin.

Daha fazla bilgi için bkz. [nesne kimliği oluşturma](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>İşlevler için dönüş değerlerini görüntüle

İşlevlerinizin dönüş değerlerini görüntülemek için, kodunuzla adımlarken, **oto** penceresinde görüntülenen işlevlere bakın. Bir işlevin dönüş değerini görmek için, ilgilendiğiniz işlevin zaten çalıştırılmış olduğundan emin olun (işlev çağrısında halen durduysanız **F10** tuşuna basın). Pencere kapalıysa, **hata ayıklama > Windows > oto** ' ı kullanarak **oto** penceresini açın.

![Oto penceresi](../debugger/media/dbg-tips-autos-window.png "Oto penceresi")

Ayrıca, dönüş değerlerini görüntülemek için **komut** penceresine işlevler girebilirsiniz. ( **Hata ayıklama > Windows > anında**kullanarak açın.)

![Komut Penceresi](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Ayrıca, **izleme** ve **anında** penceresinde, `$ReturnValue` gibi [sözde değişkenler](../debugger/pseudovariables.md) de kullanabilirsiniz.

## <a name="string_visualizer"></a>Görselleştirici içindeki dizeleri İnceleme

Dizelerle çalışırken, tüm biçimli dizeyi görüntülemek yararlı olabilir. Düz metin, XML, HTML veya JSON dizesini görüntülemek için, bir dize değeri içeren bir değişken üzerine gelindiğinde büyüteç simgesini ![Visualizersimgesine](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") tıklayın.

![Dize görselleştiricisi açın](../debugger/media/dbg-tips-string-visualizers.png "Openstringgörselleştiricisi")

Dize görselleştiricisi dize türüne bağlı olarak bir dizenin hatalı biçimlendirilmiş olup olmadığını bulmanıza yardımcı olabilir. Örneğin, boş bir **değer** alanı, dizenin Görselleştirici türü tarafından tanınmadığını gösterir. Daha fazla bilgi için bkz. [dize görselleştiricisi Iletişim kutusu](../debugger/string-visualizer-dialog-box.md).

![JSON dize görselleştiricisi](../debugger/media/dbg-tips-string-visualizer-json.png "Jsonstringgörselleştiricisi")

Hata ayıklayıcı penceresinde görünen veri kümesi ve DataTable nesneleri gibi diğer diğer türler için de bir yerleşik görselleştiricisi açabilirsiniz.

## <a name="break-into-code-on-handled-exceptions"></a>İşlenmiş özel durumlarla ilgili koda Böl

Hata ayıklayıcı, işlenmeyen özel durumlarla kodunuzda sizi sonlandırır. Ancak, işlenen özel durumlar (bir `try/catch` bloğu içinde oluşan özel durumlar gibi) hata kaynağı olabilir ve ne zaman meydana geldiğinde araştırmak isteyebilirsiniz. Hata ayıklayıcıyı işlenmiş özel durumlar için koda bölmek ve **özel durum ayarları** iletişim kutusundaki seçenekleri yapılandırmak için yapılandırabilirsiniz. **Hata ayıkla > Windows > özel durum ayarları**' nı seçerek bu iletişim kutusunu açın.

**Özel durum ayarları** iletişim kutusu, hata ayıklayıcıya belirli özel durumlarda koda bölünmeyle karşılaşmalarını sağlar. Aşağıdaki çizimde, bir `System.NullReferenceException` her gerçekleştiğinde hata ayıklayıcı kodunuzda kesilir. Daha fazla bilgi için bkz. [özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md).

![Özel durum ayarları Iletişim kutusu](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Hata ayıklama kilitlenmeleri ve yarış koşulları

Çok iş parçacıklı uygulamalarda ortak olan sorun türlerinde hata ayıklaması yapmanız gerekiyorsa, genellikle hata ayıklama sırasında iş parçacıklarının konumunu görüntülemeye yardımcı olur. Bunu **kaynak Içinde Iş parçacıklarını göster** düğmesini kullanarak kolayca yapabilirsiniz.

#### <a name="to-show-threads-in-your-source-code"></a>Kaynak kodunuzda iş parçacıklarını göstermek için

1. Hata ayıklama sırasında **hata ayıklama** araç ![çubuğunda kaynak bölümünde](../debugger/media/dbg-multithreaded-show-threads.png "Threadişaretleyici") iş parçacıklarını **göster** düğmesine tıklayın.

2. Pencerenin sol tarafındaki cilt paya bakın. Bu satırda, iki kumaş iş parçacığına benzer bir *iş parçacığı işaretleyici* simgesi ![iş parçacığı işaretçisi](../debugger/media/dbg-thread-marker.png "Threadişaretleyici") görürsünüz. İş parçacığı işaretçisi, bu konumda bir iş parçacığının durdurulduğunu gösterir.

    Bir iş parçacığı işaretleyicisinin bir kesme noktası tarafından kısmen eklenebilir olabileceğini unutmayın.

3. İşaretçiyi iş parçacığı işaretçisinin üzerine getirin. Bir veri Ipucu görünür. Veri Ipucu, her durdurulan iş parçacığı için ad ve iş parçacığı KIMLIĞI numarası size bildirir.

    Ayrıca, iş parçacıklarının konumunu [Paralel Yığınlar penceresinde](../debugger/get-started-debugging-multithreaded-apps.md)görüntüleyebilirsiniz.

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Web Hizmetleri ve ağ kaynakları için yükleri İnceleme (UWP)

UWP uygulamalarında, `Windows.Web.Http` API kullanarak gerçekleştirilen ağ işlemlerini çözümleyebilirsiniz. Bu aracı, Web Hizmetleri ve ağ kaynaklarında hata ayıklamanıza yardımcı olması için kullanabilirsiniz. Aracı kullanmak için **> performans profil oluşturucu hata ayıkla**' yı seçin. **Ağ**' ı seçin ve ardından **Başlat**' ı seçin. Uygulamanızda, `Windows.Web.Http` kullanan senaryoya gidin ve sonra raporu oluşturmak için **koleksiyonu durdur** ' u seçin.

![Ağ kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Daha fazla ayrıntı görüntülemek için Özet görünümünde bir işlem seçin.

![Ağ kullanımı aracında ayrıntılı bilgiler](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Daha fazla bilgi için bkz. [ağ kullanımı](../profiling/network-usage.md).
::: moniker-end

## <a name="modules_window"></a>Hata ayıklayıcının uygulamanıza nasıl ilişi hakkında daha fazla bilgi edinin (C#, C++, Visual Basic, F#)

Çalışan uygulamanıza iliştirmek için hata ayıklayıcı, hata ayıklamaya çalıştığınız uygulamanın tam olarak aynı derlemesi için oluşturulan sembol (. pdb) dosyalarını yükler. Bazı senaryolarda sembol dosyalarının küçük bir bilgisi yararlı olabilir. Visual Studio 'Nun, **modüller** penceresini kullanarak sembol dosyalarını nasıl yüklediğini inceleyebilirsiniz.

Hata ayıklama **> Windows > modülleri**'Ni seçerek **modüller** penceresini açın. **Modüller** penceresi, hata ayıklayıcının Kullanıcı kodu veya [*kodum*](../debugger/just-my-code.md)olarak hangi modülleri olduğunu ve modülün sembol yükleme durumunu söyleyebilir. Çoğu senaryoda, hata ayıklayıcı Kullanıcı kodu için sembol dosyalarını otomatik olarak bulur, ancak .NET kodu, sistem kodu veya üçüncü taraf kitaplık kodu içine (veya hata ayıklama) geçmek istiyorsanız, doğru sembol dosyalarını almak için ek adımlar gereklidir.

![Modüller penceresinde sembol bilgilerini görüntüleme](../debugger/media/dbg-tips-modules-window.png "Viewsymbolınformation")

Sembol bilgilerini doğrudan **modüller** penceresinden, sağ tıklayıp **sembolleri yükle**' yi seçerek yükleyebilirsiniz.

Bazen, uygulama geliştiricileri, eşleşen sembol dosyaları olmadan (parmak izini azaltmak için) uygulamaları teslim eder, ancak daha sonra yayınlanan bir sürümün hatalarını ayıklayabilmeleri için eşleşen sembol dosyalarının bir kopyasını derleme için saklayın.

Hata ayıklayıcının kodu Kullanıcı kodu olarak sınıflandırdığı hakkında bilgi edinmek için bkz. [yalnızca kendi kodum](../debugger/just-my-code.md). Sembol dosyaları hakkında daha fazla bilgi edinmek için bkz. [Visual Studio hata ayıklayıcısında simge (. pdb) ve kaynak dosyaları belirtme](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Daha fazla bilgi edinin

Ek ipuçları ve püf noktaları ve daha ayrıntılı bilgi için şu blog gönderilerine bakın:

- [7 Visual Studio 'da hata ayıklama için bilinen korsanlardan daha az](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio 'da 7 gizli Gems](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Ayrıca bkz.

[Klavye Kısayolları](../ide/productivity-shortcuts.md)
