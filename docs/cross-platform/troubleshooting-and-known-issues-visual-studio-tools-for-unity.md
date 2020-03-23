---
title: Sorun giderme ve bilinen sorunlar (VS Unity Araçları)
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d6856ff73f9aab2325a31e164e7983a919097d46
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "66261124"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Sorun giderme ve bilinen sorunlar (Visual Studio Tools for Unity)

Bu bölümde, Visual Studio Tools for Unity ile sık karşılaşılan sorunlara çözümler bulacak, bilinen sorunların açıklamalarını ve hataları bildirerek Visual Studio Tools for Unity'yi geliştirmenize nasıl yardımcı olabileceğinizi öğreneceksiniz.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Unity ve Visual Studio arasındaki bağlantıyı giderme

### <a name="confirm-editor-attaching-is-enabled"></a>Editör Ekleme'nin etkin olduğunu onaylayın

Birlik Menüsü'nde, **> Tercihleri Edet'i** ve ardından **Dış Araçlar** sekmesini seçin. Düzenleyici **Ekleme** onay kutusunun etkin olduğunu onaylayın. Daha fazla bilgi için [Birlik Tercihleri belgelerine](https://docs.unity3d.com/Manual/Preferences.html)bakın.

### <a name="unable-to-attach"></a>Eklenemiyor

- Virüsten koruma yazılımınızı geçici olarak devre dışı bırakıp hem VS hem de Unity için dışlama kuralları oluşturmaya çalışın.
- Güvenlik duvarınızı geçici olarak devre dışı bırakıp VS ve Unity arasında TCP/UDP ağına izin vermek için kurallar oluşturmaya çalışın.
- Team Viewer gibi bazı programlar işlem algılamayı etkileyebilir. Bir şeyi değiştirip değiştirmediğinizi görmek için herhangi bir ek yazılımı geçici olarak durdurmayı deneyebilirsiniz.
- VSTU yalnızca "Unity.exe" işlemlerini izlediği için ana Unity çalıştırılabilir adını yeniden adlandırmayın.

## <a name="visual-studio-crashes"></a>Visual Studio çöküyor

Bu sorun, Visual Studio MEF önbelleğinin bozulmasından kaynaklanabilir.

MEF önbelleğini sıfırlamak için aşağıdaki klasörü kaldırmayı deneyin (bunu yapmadan önce Visual Studio'yu kapatın):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Bu sorununuzu gidermek gerekir. Sorunu hala yaşıyorsanız, Visual Studio için Bir Geliştirici Komut İstemi'ni Yönetici olarak çalıştırın ve aşağıdaki komutu kullanın:

```batch
 devenv /setup
```

## <a name="visual-studio-hangs"></a>Visual Studio askıda

Parse, FMOD, UMP (Universal Media Player), ZFBrowser veya Embedded Browser gibi çeşitli Unity eklentileri yerel iş parçacığı kullanıyor. Bu, bir eklentinin çalışma süresine yerel bir iş parçacığı iliştirmesi ile ilgili bir sorundur ve bu da işletim sistemi aramalarını engeller. Bu, Unity'nin hata ayıklayıcı (veya etki alanı yeniden yüklemesi) için bu iş parçacığıkesintiyip asamayacağı anlamına gelir.

FMOD için bir geçici çözüm vardır, `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` asynchronous işlemedevre dışı bırakıp ana iş parçacığı üzerindeki tüm işlemleri gerçekleştirmek için başlatma [bayrağını](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags) geçirebilirsiniz.

## <a name="incompatible-project-in-visual-studio"></a>Visual Studio'da uyumsuz proje

İlk olarak, Visual Studio'nun Unity (Edit/Preferences/External Tools) dosyası dışında dış komut dosyası düzenleyiciniz olarak ayarlanabildiğinizden denetleyin. Ardından Visual Studio eklentisinin Unity'ye yüklü olup olmadığını kontrol edin (Yardım/Hakkında, microsoft visual studio tools for Unity gibi bir iletiyi görüntülemeli) en altta etkinleştirildi. Daha sonra uzantın Visual Studio'ya (Yardım/Hakkında) düzgün bir şekilde yüklendiğinden kontrol edin.

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Ekstra yeniden yüklemeveya Visual Studio tüm açık pencereleri kaybetme

Proje dosyalarına doğrudan bir varlık işlemcisinden veya başka bir araçtan dokunmadığından emin olun. Eğer gerçekten proje dosyasını manipüle etmek gerekiyorsa, bunun için bir API ortaya çıkar. Lütfen [Montaj referansları sorunları bölümünü](#assembly-reference-issues)kontrol edin.

Ekstra yeniden yüklemeler yaşıyorsanız veya Visual Studio yeniden yükleme de tüm açık Windows kaybediyorsa, uygun .NET hedefleme paketleri yüklü olduğundan emin olun. Daha fazla bilgi için çerçeveler hakkında aşağıdaki bölümü kontrol edin.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Hata ayıklama özel durumlar akırılmaz

Eski Unity çalışma zamanı (.NET 3.5 eşdeğeri) kullanırken, bir özel durum işlenmediğinde (=deneme/yakalama bloğu dışında) hata ayıklama her zaman kırılır. Özel durum işlenirse, hata ayıklayıcı bir kesme nin gerekli olup olmadığını belirlemek için Özel Durum Ayarları Penceresi'ni kullanır.

Yeni çalışma süresi (.NET 4.6 eşdeğeri) ile Unity, kullanıcı özel durumlarını yönetmek için yeni bir yol tanıttı ve sonuç olarak, tüm özel durumlar deneme/yakalama bloğu dışında olsalar bile "kullanıcı işledi" olarak görülüyor. Bu nedenle hata ayıklamanın kırılmasını istiyorsanız, bunları Özel Durum Ayarları Penceresinde açıkça denetlemeniz gerekir.

Özel Durum Ayarları penceresinde (Hata Ayıklama > Windows > Özel Durum Ayarları), özel durumlar kategorisi (örneğin, Ortak Dil Çalışma Zamanı Özel Durumlar, yani .NET özel durumlar) için düğümü genişletin ve bu kategoride yakalamak istediğiniz özel durum için onay kutusunu seçin (örneğin System.NullReferenceException). Ayrıca, özel durumların tüm kategorisini de seçebilirsiniz.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Windows'da Visual Studio, Unity hedef çerçevesini indirmek ister

Visual Studio Tools for Unity, Windows 8 veya 10'da varsayılan olarak yüklenmez .NET framework 3.5 gerektirir. Bu sorunu gidermek için ,.NET framework 3.5'i indirmek ve yüklemek için yönergeleri izleyin.

Yeni Unity çalışma süresini kullanırken,.NET hedefleme paketleri sürüm 4.6 ve 4.7.1 de gereklidir. Vs2017 yükleyicisini kullanarak hızlı bir şekilde yüklemeniz mümkündür (VS2017 kurulumunuzu, tek tek bileşenlerinizi, .NET kategorinizi değiştirin, tüm 4.x hedefleme paketlerini seçin).

## <a name="assembly-reference-issues"></a>Derleme başvuru sorunları

Projeniz karmaşık başvuru açısından kullanılıyorsa veya bu oluşturma adımını daha iyi denetlemek istiyorsanız, oluşturulan proje veya çözüm içeriğini işlemek için [API'mizi](../cross-platform/customize-project-files-created-by-vstu.md) kullanabilirsiniz. [Yanıt dosyalarını](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) Unity projenizde de kullanabilirsiniz ve bunları işleyebiliriz.

## <a name="breakpoints-with-a-warning"></a>Uyarı ile kesme noktaları

Visual Studio belirli bir kesme noktası için kaynak bir konum bulamazsa, kesme noktanızın etrafında bir uyarı görürsünüz. Kullandığınız komut dosyasının geçerli Unity sahnesinde düzgün şekilde yüklendiğinden/kullanıldığından denetleyin.

## <a name="breakpoints-not-hit"></a>Kesme noktaları isabet etmiyor

Kullandığınız komut dosyasının geçerli Unity sahnesinde düzgün şekilde yüklendiğinden/kullanıldığından denetleyin. Hem Visual Studio'yu hem de\*Unity'yi bırakın \*ve oluşturulan tüm dosyaları (.csproj, .sln) ve tüm Kitaplık klasörünü silin.

## <a name="unable-to-debug-android-players"></a>Android oyuncularını hata ayıklayamıyor

Oyuncu algılamaiçin çoklu yayın kullanıyoruz (Unity tarafından kullanılan varsayılan mekanizmadır), ancak bundan sonra hata ayıklamayı takmak için düzenli bir TCP bağlantısı kullanırız. Algılama aşaması Android cihazlar için ana konudur.

Wifi gecikme nedeniyle USB ile karşılaştırıldığında çok yönlü ama süper yavaş. Biz bazı yönlendiriciler veya cihazlar için uygun multicast destek eksikliği gördüm (Nexus serisi de bunun için bilinir).

USB hata ayıklama için süper hızlıdır ve Visual Studio Tools for Unity artık USB aygıtlarını algılayabiliyor ve hata ayıklama için bağlantı noktalarını düzgün bir şekilde iletmek için adb sunucusuyla konuşabiliyor.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Visual Studio 2015 ve IntelliSense veya kod renklendirme saklı

Visual Studio 2015'inizi güncellemek için yükseltmeyi deneyin 3.

## <a name="known-issues"></a>Bilinen sorunlar

 Visual Studio Tools for Unity'de hata ayıklayıcının Unity'nin c# derleyicisinin eski sürümüyle nasıl etkileşimde olduğunu gösteren bilinen sorunlar vardır. Bu sorunların giderilen sorunlara yardımcı olmak için çalışıyoruz, ancak bu arada aşağıdaki sorunları karşılaşabilirsiniz:

- Hata ayıklama, Birlik bazen çöker.

- Hata ayıklama, Birlik bazen donuyor.

- Yöntemlere girip çıkmak bazen, özellikle yineleyicilerde veya anahtar ifadelerinde yanlış şekilde işler.

## <a name="report-errors"></a>Hataları bildirme

 Lütfen çökme, donma veya diğer hatalarla karşılaştığında hata raporları göndererek Visual Studio Tools for Unity kalitesini artırmamıza yardımcı olun. Bu, Visual Studio Tools for Unity'deki sorunları araştırmamıza ve düzeltmemize yardımcı olur. Teşekkür ederiz!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio donduğunda hata bildirme

 Visual Studio'nun Visual Studio Tools for Unity ile hata ayıklarken bazen donduğuna dair raporlar vardır, ancak bu sorunu anlamak için daha fazla veriye ihtiyacımız vardır. Aşağıdaki adımları izleyerek araştırmamıza yardımcı olabilirsiniz.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Visual Studio'nun Unity için Visual Studio Tools ile hata ayıklama sırasında donduğuna dair bildirmek için

*Windows'da:*

1. Visual Studio'nun yeni bir örneğini açın.

1. İşleme Ekle iletişim kutusunu açın. Visual Studio'nun yeni örneğinde, ana menüde **Hata Ayıklama'yı**seçin, **İşleme Ekle'yi**seçin.

1. Hata ayıklamayı Visual Studio'nun dondurulmuş örneğine takın. **İşleme Ekle** iletişim kutusunda, **Kullanılabilir İşlemler** tablosundan Visual Studio'nun dondurulmuş örneğini seçin ve ardından **Ekle** düğmesini seçin.

1. Hata Ayıklama'yı duraklatın. Visual Studio'nun yeni örneğinde, ana menüde **Hata Ayıklama**, **Tümleri Kır'ı**seçin veya **Ctrl+Alt+Break**tuşuna basın.

1. Bir iş parçacığı dökümü oluşturun. Komut penceresinde aşağıdaki komutu girin ve **Enter**tuşuna basın:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Önce **Komut** penceresini görünür hale getirmeniz gerekebilir. Visual Studio'da, ana menüde **Görünüm,** **Diğer Windows**, **Komut Penceresi'ni**seçin.

*Mac'te:*

1. Bir terminal açın ve Mac için Visual Studio'nun PID'sini alın:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. lldb hata ayıklama başlatın:

    ```shell
    lldb
    ```

1. PID'yi kullanarak Mac örneğini Görsel Stüdyo'ya takın:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Tüm iş parçacıkları için yığın izini alın:

    ```shell
    bt all
    ```

Son olarak, Visual Studio [vstusp@microsoft.com](mailto:vstusp@microsoft.com)dondurulduğunda ne yaptığınızın bir açıklamasıyla birlikte iş parçacığı dökümüne gönderin.
