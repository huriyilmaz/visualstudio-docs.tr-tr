---
title: Sorun giderme ve bilinen sorunlar (Unity için VS Araçları)
description: Unity için Visual Studio Araçları sorun giderme hakkında bilgi edinin. Bilinen sorunların açıklamalarını inceleyin ve bu sorunların çözümleri hakkında bilgi edinin.
ms.custom: ''
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
ms.openlocfilehash: a824c945bfc32e4d00b3573e3284a759b7797dcc53552dd99ae6bd276310f572
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121313776"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>sorun giderme ve bilinen sorunlar (Unity için Visual Studio Araçları)

bu bölümde, Unity için Visual Studio Araçları, bilinen sorunların açıklamalarıyla ilgili sık karşılaşılan sorunlara çözümler bulacaksınız ve hataları bildirerek Unity için Visual Studio Araçları nasıl iyileştirebileceğinizi öğreneceksiniz.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Unity ve Visual Studio arasında bağlantı sorunlarını giderme

### <a name="confirm-editor-attaching-is-enabled-or-code-optimization-on-startup-is-set-to-debug"></a>Onaylama `Editor Attaching` etkin veya `Code Optimization On Startup` olarak ayarlandı `Debug`

Unity menüsünde, öğesini seçin `Edit / Preferences` .

Kullanılan Unity sürümüne bağlı olarak:
- ' `Code Optimization On Startup` Nin olarak ayarlandığını doğrulayın `Debug` .
- Veya sekmeyi seçin `External Tools` . `Editor Attaching` onay kutusunun etkin olduğunu onaylayın. 

Daha fazla bilgi için [Unity tercihleri belgelerine](https://docs.unity3d.com/Manual/Preferences.html)bakın.

### <a name="unable-to-attach"></a>İliştirilemiyor

- Virüsten koruma için geçici olarak devre dışı bırakmayı veya hem VS hem de Unity için dışlama kuralları oluşturmayı deneyin.
- Güvenlik duvarınızı geçici olarak devre dışı bırakmayı deneyin veya VS ile Unity arasında TCP/UDP ağlarına izin vermek için kurallar oluşturun.
- Takım Görüntüleyicisi gibi bazı programlar, işlem algılamayı kesintiye uğratabilirler. Herhangi bir değişiklik olup olmadığını görmek için ek yazılımları geçici olarak durdurmayı deneyebilirsiniz.
- VSTU yalnızca "Unity.exe" süreçlerini izlerken ana Unity yürütülebilirini yeniden adlandırmayın.

## <a name="visual-studio-crashes"></a>Visual Studio kilitleniyor

bu sorunun nedeni Visual Studio MEF önbelleğinin bozulması olabilir.

MEF önbelleğini sıfırlamak için aşağıdaki klasörü kaldırmayı deneyin (bunu yapmadan önce Visual Studio kapatın):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Bu, sorununuzu çözmelidir. sorunu yaşamaya devam ederseniz, yönetici olarak bir Visual Studio Geliştirici Komut İstemi çalıştırın ve aşağıdaki komutu kullanın:

```batch
 devenv /setup
```

## <a name="visual-studio-stops-responding"></a>Visual Studio yanıt vermeyi durduruyor

Parse, FMOD, UMP (Evrensel Media Player), ZFBrowser veya katıştırılmış tarayıcı gibi çeşitli Unity eklentileri yerel iş parçacıklarını kullanıyor. Bir eklenti çalışma zamanına yerel bir iş parçacığı iliştirirken, daha sonra işletim sistemine çağrıları engelleyen bir sorundur. Bu, Unity 'nin hata ayıklayıcı (veya etki alanı yeniden yükleme) için bu iş parçacığını kesintiye uğramayacağı ve yanıt vermemesine

FMOD için, bir geçici çözüm vardır, `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` zaman uyumsuz işlemeyi devre dışı bırakmak ve ana iş parçacığında tüm işlemleri gerçekleştirmek için başlatma [bayrağını](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags) geçirebilirsiniz.

## <a name="incompatible-project-in-visual-studio"></a>Visual Studio uyumsuz proje

bilmeniz gereken çok önemli şey, Visual Studio, proje ayarlarında "uyumsuz" durumunun kaydedilemediğinden ve açık bir şekilde kullanana kadar bir projeyi yeniden yüklemeyi denemez `Reload Project` . Bu nedenle, her bir sorun giderme adımından sonra çözümü yeniden açmayı denediğinizden emin olun ve tüm uyumsuz projelere sağ tıklayıp öğesini seçin `Reload Project` .

1. Visual Studio, kullanarak Unity 'de dış betik düzenleyiciniz olarak ayarlandığından emin olun `Edit / Preferences / External Tools` .
2. Unity sürümünüze bağlı olarak:
   - Visual Studio eklentisinin Unity 'de yüklü olduğundan emin olun. `Help / About`en altta Unity için Microsoft Visual Studio araçları 'nın etkin olduğu gibi bir ileti görüntülenmelidir.
   - Unity 2020. x +: ' de en son Visual Studio düzenleyici paketini kullandığınızı denetleyin `Window / Package Manager` .
3. Tüm projeleri/çözüm dosyalarını ve `.vs` projenizdeki klasörü silmeyi deneyin.
4. Veya kullanarak projeleri/çözümü yeniden oluşturmayı deneyin `Open C# Project` `Edit / Preferences / External tools / Regenerate Project files` .
5. Visual Studio oyun/Unity iş yükünü yüklediğinizden emin olun.
6. [Burada](#visual-studio-crashes)AÇıKLANDıĞı gibi MEF önbelleğini temizlemeyi deneyin.
7. Visual Studio yeniden yüklemeyi deneyin (oyun/Unity iş yükünü yalnızca başlangıç için kullanarak).
8. İçinde Unity uzantısını kesintiye uğratabilmeleri durumunda üçüncü taraf uzantılarını devre dışı bırakmayı deneyin `Tools / Extensions` .

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>ek yeniden yükler veya Visual Studio tüm açık pencereleri kaybetme

Proje dosyalarına hiçbir şekilde doğrudan bir varlık işlemcisinden veya başka bir araçla dokunduğunuzdan emin olun. Proje dosyasını gerçekten değiştirmeniz gerekiyorsa, bunun için bir API kullanıma sunuyoruz. Lütfen [derleme başvuru sorunları bölümüne](#assembly-reference-or-project-property-issues)bakın.

ek yeniden yükleme deneyimliyorsanız veya Visual Studio, tüm açık Windows geri yükleme sırasında kaybediliyorsa, doğru .net hedefleme paketlerinin yüklü olduğundan emin olun. Daha fazla bilgi için aşağıdaki çerçeveler hakkında bölümüne bakın.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Hata ayıklayıcı özel durumlara uymuyor

Eski Unity çalışma zamanını (.NET 3,5 eşdeğerini) kullanırken hata ayıklayıcı her zaman bir özel durum işlenmemiş olduğunda (= try/catch bloğunun dışında) kesilir. özel durum işlenirse, hata ayıklayıcı bir kesme gerekip gerekmediğini öğrenmek için özel durum Ayarlar penceresini kullanır.

Yeni çalışma zamanı (.NET 4,6 eşdeğeri) ile, Unity Kullanıcı özel durumlarını yönetmek için yeni bir yol getirdi ve sonuç olarak, bir try/catch bloğunun dışında olsalar bile tüm özel durumlar "Kullanıcı tarafından işlendi" olarak görülür. bunun nedeni, hata ayıklayıcının kesilmesini istiyorsanız özel durum Ayarlar penceresinde açıkça bunları denetlemeniz gerekir.

özel durum Ayarlar penceresinde (hata ayıkla > Windows > özel durum Ayarlar), bir özel durum kategorisi (örneğin, ortak dil çalışma zamanı özel durumları, yani .net özel durumları) için düğümünü genişletin ve bu kategoride yakalamak istediğiniz özel durumun onay kutusunu seçin (örneğin, System. NullReferenceException). Tüm özel durumlar kategorisini de seçebilirsiniz.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Windows, Visual Studio Unity hedef çerçevesini indirmeyi ister

eski Unity çalışma zamanı (.net 3,5 eşdeğeri) kullanılırken, Unity için Visual Studio Araçları Windows 8 veya 10 ' da varsayılan olarak yüklü olmayan .net framework 3,5 gerektirir. Bu sorunu gidermek için, .NET Framework 3,5 'yi indirme ve yükleme yönergelerini izleyin.

Yeni Unity çalışma zamanını kullanırken, Unity sürümüne bağlı olarak .NET hedefleme paketleri sürüm 4,6 veya 4.7.1 de gereklidir. Visual Studio yükleyicisini kullanarak bunları hızlıca yüklersiniz (yüklemenizi, tek tek bileşenlerinizi, .net kategorisini değiştirin, tüm 4. x hedefleme paketlerini seçin).

## <a name="assembly-reference-or-project-property-issues"></a>Derleme başvurusu veya proje özelliği sorunları

Projeniz karmaşık başvuru temelinde veya bu oluşturma adımını daha iyi denetlemek isterseniz, oluşturulan projeyi veya çözüm içeriğini yönetmek için [API](../extensibility/customize-project-files-created-by-vstu.md) 'imizi kullanabilirsiniz. Ayrıca, Unity projenizdeki [Yanıt dosyalarını](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) da kullanabilirsiniz.

son Visual Studio ve Unity sürümlerinde, en iyi yaklaşım, `Directory.Build.props` oluşturulan projelerinizle birlikte özel bir dosya kullanma gibi görünür. Daha sonra, oluşturma süreciyle kesintiye uğramadan proje yapısına katkıda bulunabileceksiniz. [Burada](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build#directorybuildprops-and-directorybuildtargets) daha fazla bilgi bulabilirsiniz.

## <a name="breakpoints-with-a-warning"></a>Uyarı içeren kesme noktaları

Visual Studio belirli bir kesme noktası için kaynak konumu bulamazsa, kesme noktası etrafında bir uyarı görürsünüz. Kullanmakta olduğunuz betiğin geçerli Unity sahnede düzgün bir şekilde yüklendiğini/kullanıldığını denetleyin.

## <a name="breakpoints-not-hit"></a>Kesme noktaları isabet etmez

Kullanmakta olduğunuz betiğin geçerli Unity sahnede düzgün bir şekilde yüklendiğini/kullanıldığını denetleyin. hem Visual Studio hem de Unity 'den çıkıp tüm oluşturulan dosyaları ( \* . csproj, \* . sln), `.vs` klasörü ve tüm kitaplık klasörünü silin. Unity [Web sitesinde](https://docs.unity3d.com/Manual/ManagedCodeDebugging.html)C# hata ayıklaması hakkında daha fazla bilgi edinebilirsiniz.

## <a name="unable-to-debug-android-players"></a>Android oynatıcılarda hata ayıklaması yapılamıyor

Player algılaması için çok noktaya yayın kullanıyoruz (Unity tarafından kullanılan varsayılan mekanizma), ancak bundan sonra hata ayıklayıcıyı eklemek için normal bir TCP bağlantısı kullanıyoruz. Algılama aşaması, Android cihazlar için ana sorundur.

WiFi, gecikme nedeniyle USB ile karşılaştırıldığında çok yönlüdür ancak süper yavaştır. Bazı yönlendiriciler veya cihazlar için uygun çok noktaya yayın desteğinin eksik olduğunu gördük (Nexus serisi bunun için iyi bilinmektedir).

usb, hata ayıklama için süper hızlıdır ve Unity için Visual Studio Araçları artık usb cihazlarını algılayabilir ve hata ayıklama için bağlantı noktalarını doğru bir şekilde iletmek üzere adb sunucusuyla iletişim kurabilir.

## <a name="issues-with-intellisense-or-code-coloration"></a>IntelliSense veya kod renklendirme sorunları

Visual Studio en son sürüme yükseltmeyi deneyin. [Uyumsuz projeler](#incompatible-project-in-visual-studio)için aynı sorun giderme adımlarını deneyin.

## <a name="known-issues"></a>Bilinen sorunlar

Unity için Visual Studio Araçları hata ayıklayıcının, C# derleyicisinin daha eski sürümü ile nasıl etkileşime gireceğini belirten bilinen sorunlar vardır. Bu sorunları gidermeye yardımcı olmak için çalışıyoruz, ancak bu sırada aşağıdaki sorunlarla karşılaşabilirsiniz:

- Hata ayıklarken Unity bazen kilitleniyor.

- Hata ayıklama sırasında Unity bazen donuyor.

- Yöntemlerin içine ve dışına adımla bazen, özellikle yineleyiciler içinde veya switch deyimlerinde yanlış bir şekilde davranır.

## <a name="report-errors"></a>Hataları raporla

kilitlenme, dondurur veya diğer hatalarla karşılaşdığınızda hata raporları göndererek Unity için Visual Studio Araçları kalitesini iyileştirmemize yardımcı olun. bu, Unity için Visual Studio Araçları sorunları araştırmamıza ve gidermenize yardımcı olur. Teşekkür ederiz!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio donuyor olduğunda hata bildirme

Unity için Visual Studio Araçları ile hata ayıklarken Visual Studio bazen donuyor olan raporlar var, ancak bu sorunu anlamak için daha fazla veri gerekir. Aşağıdaki adımları izleyerek araştırmamıza yardımcı olabilirsiniz.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları ile hata ayıklarken Visual Studio donuyor olarak bildirmek için

*Windows:*

1. Visual Studio yeni bir örneğini açın.

1. Işleme Iliştir iletişim kutusunu açın. yeni Visual Studio örneğinde, ana menüdeki **hata ayıkla**, **işleme iliştir**' i seçin.

1. Hata ayıklayıcıyı dondurulmuş Visual Studio örneğine iliştirin. **işleme iliştir** iletişim kutusunda, **kullanılabilir işlemler** tablosundan Visual Studio dondurulmuş örneğini seçin, sonra **ekle** düğmesini seçin.

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
