---
title: Sorun giderme ve bilinen sorunlar (Unity için VS Araçları)
description: Sorun giderme hakkında daha fazla bilgi Unity için Visual Studio Araçları. Bilinen sorunların açıklamalarını öğrenin ve bu sorunların çözümleri hakkında bilgi öğrenin.
ms.date: 04/15/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 196d4e8604e736440be365c9d10a4ce9f2701fba
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970925"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Sorun giderme ve bilinen sorunlar (Unity için Visual Studio Araçları)

Bu bölümde, Unity için Visual Studio Araçları ile ilgili yaygın sorunların çözümlerini, bilinen sorunların açıklamalarını ve hataları bildirerek sorunları Unity için Visual Studio Araçları nasıl yardımcı olamayabilirsiniz.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Unity ile Visual Studio arasındaki bağlantı sorunlarını giderme

### <a name="confirm-editor-attaching-is-enabled-or-code-optimization-on-startup-is-set-to-debug"></a>`Editor Attaching`Etkinleştirildiğinden veya olarak ayarlanmış olduğunu `Code Optimization On Startup` onaylayın`Debug`

Unity Menüsünde öğesini `Edit / Preferences` seçin.

Kullanılan Unity sürümüne bağlı olarak:
- 'nin `Code Optimization On Startup` olarak ayar olduğunu onaylayın. `Debug`
- Veya sekmesini `External Tools` seçin. Onay kutusunun `Editor Attaching` etkinleştirildiğinden onaylayın. 

Daha fazla bilgi için [Unity Tercihleri belgelerine bakın.](https://docs.unity3d.com/Manual/Preferences.html)

### <a name="unable-to-attach"></a>Eklenemiyor

- Virüsten koruma yazılımınızı geçici olarak devre dışı bırakmayı deneyin veya hem VS hem de Unity için dışlama kuralları oluşturun.
- GÜVENLIK duvarınızı geçici olarak devre dışı bırakmayı deneyin veya VS ile Unity arasında TCP/UDP aliğine izin veren kurallar oluşturun.
- Team Viewer gibi bazı programlar işlem algılamayı etkileyene kadar devam ediyor olabilir. Bir şeyi değiştirir mi diye görmek için ek yazılımları geçici olarak durdurmayı denemeniz gerekir.
- ANA Unity yürütülebilir dosyasını yeniden adlandırın, VSTU yalnızca "Unity.exe" işlemlerini izliyor.

## <a name="visual-studio-crashes"></a>Visual Studio kilitleniyor

Bu sorun MEF önbelleğinin Visual Studio nedeniyle olabilir.

MEF önbelleğini sıfırlamak için aşağıdaki klasörü kaldırmayı deneyin (Visual Studio önce kapatın):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Bu, sorunlarınızı çözecek. Sorun hala devam ediyorsa, Yönetici olarak Geliştirici Komut İstemi için Visual Studio bir komut çalıştırın ve aşağıdaki komutu kullanın:

```batch
 devenv /setup
```

## <a name="visual-studio-stops-responding"></a>Visual Studio yanıt vermiyor

Parse, FMOD, UMP (Universal Media Player), ZFBrowser veya Embedded Browser gibi çeşitli Unity eklentileri yerel iş parçacıklarını kullanıyor. Eklentinin çalışma zamanının yerel iş parçacığını eklemesi ve ardından işletim sistemi çağrılarını engellemesi sorunudur. Bu, Unity'nin hata ayıklayıcı (veya etki alanı yeniden yükleme) için bu iş parçacığını kesintiye uğratması ve yanıt vermeyemiyor olduğu anlamına gelir.

FMOD için geçici bir çözüm vardır; zaman uyumsuz işlemeyi devre dışı bırakmak ve ana iş parçacığında tüm işlemleri gerçekleştirmek için başlatma `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` bayrağını geçebilirsiniz. [](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags)

## <a name="incompatible-project-in-visual-studio"></a>Visual Studio'de uyumsuz proje

Burada önemli olan şey, Visual Studio ayarlarında "Uyumsuz" durumu kaydederek açıkça kullanana kadar projeyi yeniden yüklemenin denemeyecek `Reload Project` olduğudur. Bu nedenle, her sorun giderme adımından sonra çözümü yeniden açmayı denedikten ve uyumsuz tüm projelere sağ tıklar ve öğesini `Reload Project` seçin.

1. kullanarak Visual Studio Unity'de dış betik düzenleyiciniz olarak ayarlanacak şekilde `Edit / Preferences / External Tools` ayarlanacak.
2. Unity sürümünüze bağlı olarak:
   - Visual Studio eklentisinin Unity'de yüklü olup değildir. `Help / About`en altta Unity için Microsoft Visual Studio'nin etkinleştirilmesi gibi bir ileti görüntülemesi gerekir.
   - Unity 2020.x+: 'de en son Visual Studio Düzenleyicisi paketini kullanarak kontrol `Window / Package Manager` edin.
3. Projenizin tüm projelerini/çözüm dosyalarını `.vs` ve klasörünü silmeyi deneyin.
4. veya kullanarak projeleri/çözümü yeniden kullanmayı `Open C# Project` `Edit / Preferences / External tools / Regenerate Project files` deneyin.
5. Oyun/Unity iş yükünü Visual Studio.
6. MeF önbelleğini burada açıklanan şekilde temizlemeyi [deneyin.](#visual-studio-crashes)
7. Uygulama yüklemelerini yeniden Visual Studio deneyin (yalnızca başlamak için Game/Unity iş yükünü kullanarak).
8. içinde Unity uzantısına müdahale etmeleri durumunda üçüncü taraf uzantıları devre dışı bırakmayı `Tools / Extensions` deneyin.

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Ek yeniden yüklemeler veya Visual Studio açık pencerelerin kaybı

Proje dosyalarına hiçbir zaman doğrudan bir varlık işlemcisi veya başka bir araçtan dokunmayın. Proje dosyasını gerçekten işlemeniz gerekirse bunun için bir API'yi kullanırsınız. Lütfen Derleme [başvuruları sorunları bölümünü kontrol edin.](#assembly-reference-or-project-property-issues)

Ek yeniden yüklemelerle veya yeniden yükleme Visual Studio tüm açık Windows kaybıyla karşıdan yüklense, düzgün .NET hedefleme paketlerinin yüklü olduğundan emin olun. Daha fazla bilgi için çerçeveler hakkında aşağıdaki bölüme bakın.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Hata ayıklayıcısı özel durumlarda kesmez

Eski Unity çalışma zamanı (.NET 3.5 eşdeğeri) kullanılırken, bir özel durum işlenmiş (=try/catch bloğu dışında) olduğunda hata ayıklayıcı her zaman bozulur. Özel durum işlandı ise, hata ayıklayıcı bir kesme gerekli olup olmadığını belirlemek için Özel Durum Ayarlar Penceresi kullanır.

Yeni çalışma zamanı (.NET 4.6 eşdeğeri) ile Unity, kullanıcı özel durumlarını yönetmek için yeni bir yol başlattı ve sonuç olarak, bir try/catch bloğu dışında olsalar bile tüm özel durumlar "kullanıcı tarafından işlenmiş" olarak görülür. Bu nedenle, hata ayıklayıcının kesmesi için özel durum Ayarlar Penceresinde bunları açıkça denetlemenizi gerekir.

Özel Durum Ayarlar penceresinde (Hata Ayıklama > Windows > Özel Durum Ayarlar), bir özel durum kategorisinin düğümünü genişletin (örneğin, Ortak Dil Çalışma Zamanı Özel Durumları, yani .NET özel durumları) ve bu kategori içinde yakalamak istediğiniz özel durumun onay kutusunu seçin (örneğin System.NullReferenceException). Ayrıca bir özel durum kategorisinin tamamını da seçin.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Bu Windows, Visual Studio Unity hedef çerçevesini indirmeyi sorar

Eski Unity çalışma zamanı (.NET 3.5 eşdeğeri) kullanılırken, Unity için Visual Studio Araçları için .NET Framework 3.5 gerekir. Bu, Windows 8 veya 10'da varsayılan olarak yüklenmez. Bu sorunu düzeltmek için yönergeleri izleyerek .NET Framework 3.5'i indirin ve yükleyin.

Yeni Unity çalışma zamanı kullanılırken, Unity sürümüne bağlı olarak .NET hedefleme paketleri sürüm 4.6 veya 4.7.1 de gereklidir. Bunları hızlı bir şekilde yüklemek Visual Studio (yüklemenizi, tek tek bileşenlerinizi, .NET kategorisini değiştirmek, tüm 4.x hedefleme paketlerini seçmek) için Visual Studio yükleyicisini kullanabilirsiniz.

## <a name="assembly-reference-or-project-property-issues"></a>Derleme başvurusu veya proje özelliği sorunları

Projeniz karmaşık başvuru açısından ise veya bu oluşturma adımını daha iyi [](../extensibility/customize-project-files-created-by-vstu.md) kontrol etmek için API'mizi kullanarak oluşturulan proje veya çözüm içeriğini işebilirsiniz. Unity projenizin [yanıt dosyalarını](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) da kullanabilirsiniz, biz de bunları işleeceğiz.

Son Visual Studio unity sürümleriyle birlikte en iyi yaklaşım, oluşturulan projeleriniz ile birlikte özel `Directory.Build.props` bir dosya kullanmak gibi görünüyor. Ardından, oluşturma sürecine müdahale etmeden proje yapısına katkıda bulunabileceksiniz.

## <a name="breakpoints-with-a-warning"></a>Uyarı ile kesme noktaları

Belirli Visual Studio bir kesme noktası için kaynak konumu bulamazsanız kesme noktanız etrafında bir uyarıyla karşınıza gelir. Kullanmakta olduğu betiğin geçerli Unity sahnesinde düzgün şekilde yükleniyor/kullanılıyor olduğunu denetleyin.

## <a name="breakpoints-not-hit"></a>Kesme noktaları isabet değil

Kullanmakta olduğu betiğin geçerli Unity sahnesinde düzgün şekilde yükleniyor/kullanılıyor olduğunu denetleyin. Hem Visual Studio Unity'den çıkın, ardından oluşturulan tüm dosyaları ( \* .csproj, \* .sln), klasörü ve `.vs` Kitaplık klasörünün tamamını silin. Unity web sitesinde C# hata ayıklaması hakkında daha fazla bilgi [bulabilirsiniz.](https://docs.unity3d.com/Manual/ManagedCodeDebugging.html)

## <a name="unable-to-debug-android-players"></a>Android oyuncularda hata ayıklaması kurulamadı

Oynatıcı algılama için çok noktaya yayın (Unity tarafından kullanılan varsayılan mekanizmadır) kullanılır, ancak bundan sonra hata ayıklayıcıyı eklemek için normal bir TCP bağlantısı kullanıruz. Algılama aşaması, Android cihazlar için ana sorundur.

Wifi çok yönlüdür ancak gecikme süresi nedeniyle USB'ye kıyasla çok yavaştır. Bazı yönlendiriciler veya cihazlar için uygun çok noktaya yayın desteğinin eksik olduğunu gördük (Nexus serisi bunun için iyi bilinir).

USB hata ayıklama için süper hızlıdır ve Unity için Visual Studio Araçları artık USB cihazlarını algılanabilir ve hata ayıklama için bağlantı noktalarını düzgün bir şekilde iletmesi için adb sunucusuyla iletişimde bulunur.

## <a name="issues-with-intellisense-or-code-coloration"></a>IntelliSense veya kod renklendirme sorunları

Güncelleştirmenizi en Visual Studio sürümüne yükseltmeyi deneyin. Uyumsuz projeler için ile aynı sorun [giderme adımlarını deneyin.](#incompatible-project-in-visual-studio)

## <a name="known-issues"></a>Bilinen sorunlar

Hata ayıklayıcının Unity'nin Unity için Visual Studio Araçları C# derleyicisi sürümüyle etkileşim kurması sonucunda ortaya çıkan bilinen sorunlar vardır. Bu sorunları düzeltmeye yardımcı olmak için çalışıyoruz, ancak bu arada aşağıdaki sorunlarıyla da karşınıza olabilir:

- Hata ayıklama sırasında Unity bazen kilitleniyor.

- Hata ayıklama sırasında Unity bazen donuyor.

- Yöntemlerin içine veya dışından adımlama bazen, özellikle de iterators'da veya switch deyimlerinde yanlış davranır.

## <a name="report-errors"></a>Hataları bildirme

Kilitlenme, donma veya diğer Unity için Visual Studio Araçları hatalarla ilgili hata raporları göndererek bu hizmet kalitesini artırmamıza yardımcı olun. Bu, uygulamayla ilgili sorunları araştırmamıza ve düzeltmeme Unity için Visual Studio Araçları. Teşekkür ederiz!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Uygulama donuyorsa hata Visual Studio bildirme

Hata ayıklama sırasında Visual Studio bazen donan raporlar Unity için Visual Studio Araçları ama bu sorunu anlamak için daha fazla veriye ihtiyacımız var. Aşağıdaki adımları takip edin ve araştırmamıza yardımcı olabilir.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Hata ayıklama sırasında Visual Studio hata ayıklama sırasında bu hatanın donup Unity için Visual Studio Araçları

*Windows:*

1. Yeni bir örnek Visual Studio.

1. İşleme Ekle iletişim kutusunu açın. Uygulamanın yeni Visual Studio menüsünde Hata Ayıkla, İşleme **Ekle'yi seçin.** 

1. Hata ayıklayıcıyı uygulamanın donmuş örneğine Visual Studio. **işleme iliştir** iletişim kutusunda, **kullanılabilir işlemler** tablosundan Visual Studio dondurulmuş örneğini seçin, sonra **ekle** düğmesini seçin.

1. Hata ayıklayıcıyı duraklatın. yeni Visual Studio örneğinde, ana menüdeki **hata ayıkla**, **tümünü kes**' i seçin veya **Ctrl + Alt + Break** tuşlarına basın.

1. İş parçacığı oluşturma-döküm. Komut penceresi, aşağıdaki komutu girin ve **ENTER** tuşuna basın:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Önce **komut** penceresini görünür yapmanız gerekebilir. Visual Studio, ana menüden **görünüm**, **diğer Windows**, **komut penceresi**' ni seçin.

*Mac'te:*

1. bir terminal açın ve Mac için Visual Studio pıd 'sini alın:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Lldb hata ayıklayıcısını başlatın:

    ```shell
    lldb
    ```

1. pıd kullanarak Mac için Visual Studio örneğine iliştirin:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Tüm iş parçacıkları için StackTrace 'i alın:

    ```shell
    bt all
    ```

son olarak, [vstusp@microsoft.com](mailto:vstusp@microsoft.com) Visual Studio dondurulmuş hale geldiğinde ne yaptığınızın bir açıklamasıyla birlikte iş parçacığı dökümünü gönderin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
