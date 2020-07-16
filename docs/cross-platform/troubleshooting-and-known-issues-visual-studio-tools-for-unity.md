---
title: Sorun giderme ve bilinen sorunlar (Unity için VS Araçları)
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 7858846585467de3b5b820902938d6019b0d09ff
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386270"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Sorun giderme ve bilinen sorunlar (Unity için Visual Studio Araçları)

Bu bölümde, Unity için Visual Studio Araçları, bilinen sorunların açıklamalarıyla ilgili sık karşılaşılan sorunlara çözümler bulacaksınız ve hataları bildirerek Unity için Visual Studio Araçları nasıl iyileştirebileceğinizi öğreneceksiniz.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Unity ve Visual Studio ile bağlantı sorunlarını giderme

### <a name="confirm-editor-attaching-is-enabled"></a>Düzenleyici Iliştirmenin etkin olduğunu onaylayın

Unity menüsünde **> Tercihleri Düzenle** ' yi seçin ve ardından **dış araçlar** sekmesini seçin. **Düzenleyici Iliştirme** onay kutusunun etkin olduğunu onaylayın. Daha fazla bilgi için [Unity tercihleri belgelerine](https://docs.unity3d.com/Manual/Preferences.html)bakın.

### <a name="unable-to-attach"></a>İliştirilemiyor

- Virüsten koruma için geçici olarak devre dışı bırakmayı veya hem VS hem de Unity için dışlama kuralları oluşturmayı deneyin.
- Güvenlik duvarınızı geçici olarak devre dışı bırakmayı deneyin veya VS ile Unity arasında TCP/UDP ağlarına izin vermek için kurallar oluşturun.
- Takım Görüntüleyicisi gibi bazı programlar, işlem algılamayı kesintiye uğratabilirler. Herhangi bir değişiklik olup olmadığını görmek için ek yazılımları geçici olarak durdurmayı deneyebilirsiniz.
- VSTU yalnızca "Unity.exe" süreçlerini izlerken ana Unity yürütülebilirini yeniden adlandırmayın.

## <a name="visual-studio-crashes"></a>Visual Studio çöküyor

Bu sorun, Visual Studio MEF önbelleğinin bozulması nedeniyle olabilir.

MEF önbelleğini sıfırlamak için aşağıdaki klasörü kaldırmayı deneyin (bunu yapmadan önce Visual Studio 'Yu kapatın):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Bu, sorununuzu çözmelidir. Sorunu yaşamaya devam etmeniz durumunda, Visual Studio için Geliştirici Komut İstemi yönetici olarak çalıştırın ve aşağıdaki komutu kullanın:

```batch
 devenv /setup
```

## <a name="visual-studio-stops-responding"></a>Visual Studio yanıt vermeyi durduruyor

Parse, FMOD, UMP (Evrensel Media Player), ZFBrowser veya katıştırılmış tarayıcı gibi çeşitli Unity eklentileri yerel iş parçacıklarını kullanıyor. Bir eklenti çalışma zamanına yerel bir iş parçacığı iliştirirken, daha sonra işletim sistemine çağrıları engelleyen bir sorundur. Bu, Unity 'nin hata ayıklayıcı (veya etki alanı yeniden yükleme) için bu iş parçacığını kesintiye uğramayacağı ve yanıt vermemesine

FMOD için, bir geçici çözüm vardır, `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` zaman uyumsuz işlemeyi devre dışı bırakmak ve ana iş parçacığında tüm işlemleri gerçekleştirmek için başlatma [bayrağını](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags) geçirebilirsiniz.

## <a name="incompatible-project-in-visual-studio"></a>Visual Studio 'da uyumsuz proje

İlk olarak, Visual Studio 'Nun Unity 'de dış betik düzenleyiciniz (düzenleme/Tercihler/dış araçlar) olarak ayarlandığından emin olun. Daha sonra Unity 'de Visual Studio eklentisinin yüklü olup olmadığını kontrol edin (yardım/Ilgili Microsoft Visual Studio, en altta Unity için araçları 'nın etkin olduğunu belirten bir ileti görüntülemelidir). Sonra uzantının Visual Studio 'da düzgün şekilde yüklenip yüklenmediğini kontrol edin (yardım/hakkında).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Ek yeniden yükler veya Visual Studio tüm açık pencereleri kaybetme

Proje dosyalarına hiçbir şekilde doğrudan bir varlık işlemcisinden veya başka bir araçla dokunduğunuzdan emin olun. Proje dosyasını gerçekten değiştirmeniz gerekiyorsa, bunun için bir API kullanıma sunuyoruz. Lütfen [derleme başvuru sorunları bölümüne](#assembly-reference-issues)bakın.

Ek yeniden yükleme deneyimliyorsanız veya Visual Studio yeniden yükleme sırasında tüm açık pencereleri kaybederiyorsa, doğru .NET hedefleme paketlerinin yüklü olduğundan emin olun. Daha fazla bilgi için aşağıdaki çerçeveler hakkında bölümüne bakın.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Hata ayıklayıcı özel durumlara uymuyor

Eski Unity çalışma zamanını (.NET 3,5 eşdeğerini) kullanırken hata ayıklayıcı her zaman bir özel durum işlenmemiş olduğunda (= try/catch bloğunun dışında) kesilir. Özel durum işlenirse, hata ayıklayıcı bir kesmenin gerekli olup olmadığını anlamak için özel durum ayarları penceresini kullanır.

Yeni çalışma zamanı (.NET 4,6 eşdeğeri) ile, Unity Kullanıcı özel durumlarını yönetmek için yeni bir yol getirdi ve sonuç olarak, bir try/catch bloğunun dışında olsalar bile tüm özel durumlar "Kullanıcı tarafından işlendi" olarak görülür. Bunun nedeni, hata ayıklayıcının kesilmesini istiyorsanız özel durum ayarları penceresinde açıkça bunları denetlemeniz gerekir.

Özel durum ayarları penceresinde (Hata Ayıkla > Windows > özel durum ayarları), bir özel durum kategorisi (örneğin, ortak dil çalışma zamanı özel durumları, yani .NET özel durumları) için düğümünü genişletin ve bu kategoride yakalamak istediğiniz özel durumun onay kutusunu seçin (örneğin, System. NullReferenceException). Tüm özel durumlar kategorisini de seçebilirsiniz.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Windows 'da, Visual Studio 'Nun Unity hedef çerçevesini indirmesini ister

Unity için Visual Studio Araçları, Windows 8 veya 10 ' da varsayılan olarak yüklü olmayan .NET Framework 3,5 gerektirir. Bu sorunu gidermek için, .NET Framework 3,5 'yi indirme ve yükleme yönergelerini izleyin.

Yeni Unity çalışma zamanını kullanırken .NET hedefleme paketleri sürüm 4,6 ve 4.7.1 de gereklidir. Onları hızlıca yüklemek için VS2017 yükleyicisini kullanabilirsiniz (VS2017 yüklemenizi, tek tek bileşenlerinizi, .NET kategorisini değiştirin, 4. x hedefleme paketini seçin).

## <a name="assembly-reference-issues"></a>Derleme başvurusu sorunları

Projeniz karmaşık başvuru temelinde veya bu oluşturma adımını daha iyi denetlemek isterseniz, oluşturulan projeyi veya çözüm içeriğini yönetmek için [API](../cross-platform/customize-project-files-created-by-vstu.md) 'imizi kullanabilirsiniz. Ayrıca, Unity projenizdeki [Yanıt dosyalarını](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) da kullanabilirsiniz.

## <a name="breakpoints-with-a-warning"></a>Uyarı içeren kesme noktaları

Visual Studio belirli bir kesme noktası için kaynak konumu bulamazsa, kesme noktası etrafında bir uyarı görürsünüz. Kullanmakta olduğunuz betiğin geçerli Unity sahnede düzgün bir şekilde yüklendiğini/kullanıldığını denetleyin.

## <a name="breakpoints-not-hit"></a>Kesme noktaları isabet etmez

Kullanmakta olduğunuz betiğin geçerli Unity sahnede düzgün bir şekilde yüklendiğini/kullanıldığını denetleyin. Hem Visual Studio hem de Unity 'den çıkıp tüm oluşturulan dosyaları ( \* . csproj, \* . sln) ve tüm kitaplık klasörünü silin.

## <a name="unable-to-debug-android-players"></a>Android oynatıcılarda hata ayıklaması yapılamıyor

Player algılaması için çok noktaya yayın kullanıyoruz (Unity tarafından kullanılan varsayılan mekanizma), ancak bundan sonra hata ayıklayıcıyı eklemek için normal bir TCP bağlantısı kullanıyoruz. Algılama aşaması, Android cihazlar için ana sorundur.

WiFi, gecikme nedeniyle USB ile karşılaştırıldığında çok yönlüdür ancak süper yavaştır. Bazı yönlendiriciler veya cihazlar için uygun çok noktaya yayın desteğinin eksik olduğunu gördük (Nexus serisi bunun için iyi bilinmektedir).

USB, hata ayıklama için süper hızlıdır ve Unity için Visual Studio Araçları artık USB cihazlarını algılayabilir ve hata ayıklama için bağlantı noktalarını doğru bir şekilde iletmek üzere ADB sunucusuyla iletişim kurabilir.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Visual Studio 2015, IntelliSense veya Code colorile ilgili sorunlar

Visual Studio 2015 ' i güncelleştirme 3 ' e yükseltmeyi deneyin.

## <a name="known-issues"></a>Bilinen sorunlar

 Unity için Visual Studio Araçları hata ayıklayıcının, C# derleyicisinin daha eski sürümü ile nasıl etkileşime gireceğini belirten bilinen sorunlar vardır. Bu sorunları gidermeye yardımcı olmak için çalışıyoruz, ancak bu sırada aşağıdaki sorunlarla karşılaşabilirsiniz:

- Hata ayıklarken Unity bazen kilitleniyor.

- Hata ayıklama sırasında Unity bazen donuyor.

- Yöntemlerin içine ve dışına adımla bazen, özellikle yineleyiciler içinde veya switch deyimlerinde yanlış bir şekilde davranır.

## <a name="report-errors"></a>Hataları raporla

 Kilitlenme, dondurur veya diğer hatalarla karşılaşdığınızda hata raporları göndererek Unity için Visual Studio Araçları kalitesini iyileştirmemize yardımcı olun. Bu, Unity için Visual Studio Araçları sorunları araştırmamıza ve gidermenize yardımcı olur. Teşekkür ederiz!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio donuyor olduğunda hata bildirme

 Unity için Visual Studio Araçları ile hata ayıklarken Visual Studio 'Nun bazen donmasına neden olan raporlar var, ancak bu sorunu anlamak için daha fazla veri gerekir. Aşağıdaki adımları izleyerek araştırmamıza yardımcı olabilirsiniz.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları hata ayıklarken Visual Studio 'Nun donuyor olduğunu bildirmek için

*Windows 'da:*

1. Visual Studio 'nun yeni bir örneğini açın.

1. Işleme Iliştir iletişim kutusunu açın. Visual Studio 'nun yeni örneğinde, ana menüdeki **Hata Ayıkla**, **İşleme İliştir**' i seçin.

1. Hata ayıklayıcıyı Visual Studio 'nun dondurulmuş örneğine iliştirin. **Işleme İliştir** iletişim kutusunda, **kullanılabilir Işlemler** tablosundan Visual Studio 'nun dondurulmuş örneğini seçin ve **Ekle** düğmesini seçin.

1. Hata ayıklayıcıyı duraklatın. Visual Studio 'nun yeni örneğinde, ana menüdeki **Hata Ayıkla**, **Tümünü kes**' i seçin veya **Ctrl + Alt + Break**tuşlarına basın.

1. İş parçacığı oluşturma-döküm. Komut penceresi, aşağıdaki komutu girin ve **ENTER**tuşuna basın:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Önce **komut** penceresini görünür yapmanız gerekebilir. Visual Studio 'da, ana menüden **Görünüm**, **diğer pencereler**, **komut penceresi**' ni seçin.

*Mac'te:*

1. Bir Terminal açın ve Mac için Visual Studio PID 'sini alın:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Lldb hata ayıklayıcısını başlatın:

    ```shell
    lldb
    ```

1. PID kullanarak Mac için Visual Studio örneğine iliştirin:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Tüm iş parçacıkları için StackTrace 'i alın:

    ```shell
    bt all
    ```

Son olarak, iş parçacığı dökümünü [vstusp@microsoft.com](mailto:vstusp@microsoft.com) , Visual Studio dondurulmuş hale geldiğinde ne yaptığınızın bir açıklamasıyla birlikte gönderin.
