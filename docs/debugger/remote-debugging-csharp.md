---
title: Uzaktan Hata Ayıklama c# veya VB projesi | Microsoft Dokümanlar
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f147acae956ad380c6e85984de29d5316394c0a
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302100"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Visual Studio'da C# veya Visual Basic projesinin Uzaktan Hata Ayıklanması
Farklı bir bilgisayarda dağıtılan bir Visual Studio uygulamasını hata ayıklamak için, uygulamanızı dağıttığınız bilgisayardaki uzak araçları yükleyin ve çalıştırın, Projenizi Visual Studio'dan uzak bilgisayara bağlanacak şekilde yapılandırın ve ardından uygulamanızı çalıştırın.

![Uzaktan hata ayıklama bileşenleri](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Evrensel Windows Uygulamaları 'nın (UWP) uzaktan hata ayıklama hakkında bilgi için [bkz.](debug-installed-app-package.md)

## <a name="requirements"></a>Gereksinimler

Uzaktan hata ayıklayıcı, Windows Server 2008 Service Pack 2 ile başlayan Windows 7 ve daha yeni (telefon değil) ve Windows Server sürümlerinde desteklenir. Gereksinimlerin tam listesi için [Gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon)bölümüne bakın.

> [!NOTE]
> Proxy üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmez. Çevirmeli Internet gibi yüksek gecikmeli veya düşük bant genişliği bağlantısı üzerinden veya ülkeler arasında Internet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya kabul edilemez derecede yavaş olabilir.

## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirin ve yükleyin

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Bazı senaryolarda, uzak hata ayıklama yı çalıştırmak için en verimli olabilir. Daha fazla bilgi için [bkz.](../debugger/remote-debugging.md#fileshare_msvsmon)

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>Uzaktan hata ayıklamayı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izin eklemeniz, kimlik doğrulama modunu veya uzak hata ayıklayıcının bağlantı noktası numarasını değiştirmeniz gerekiyorsa, [bkz.](../debugger/remote-debugging.md#configure_msvsmon)

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a>Projeyi uzaktan hata ayıklama
Hata ayıklayıcı Visual C# veya Visual Basic masaüstü uygulamalarını uzak bir makineye dağıtamaz, ancak bunları aşağıdaki gibi uzaktan hata ayıklamanıza devam edebilirsiniz. Aşağıdaki yordam, aşağıdaki resimde gösterildiği gibi, **MJO-DL**adlı bir bilgisayarda hata ayıklamak istediğinizi varsayar.

1. **MyWpf**adında bir WPF projesi oluşturun.

2. Kodda kolayca erişilebilen bir noktada bir kesme noktası ayarlayın.

    Örneğin, bir düğme işleyicisi bir kesme noktası ayarlayabilirsiniz. Bunu yapmak için MainWindow.xaml'ı açın ve Araç Kutusundan bir Düğme denetimi ekleyin, ardından işleyicisini açmak için düğmeyi çift tıklatın.

3. Çözüm Gezgini'nde projeyi sağ tıklatın ve **Özellikler'i**seçin.

4. **Özellikler** sayfasında **Hata Ayıklama** sekmesini seçin.

    ![Uzaktan Hata AyıklamaCSharp](../debugger/media/remotedebuggercsharp.png "Uzaktan Hata AyıklamaCSharp")

5. **Çalışma dizini** metin kutusunun boş olduğundan emin olun.

6. **Uzak makineyi kullan'ı**seçin ve metin kutusuna **makine adınızı yazın.** (Bağlantı noktası numarası uzak hata ayıklama penceresinde gösterilir. Port numarası Visual Studio'nun her sürümünde 2'yi arttırıyor).

    Bu örnekte, şu leri kullanın:
    ::: moniker range=">=vs-2019"
    Görsel Stüdyo 2019'da **MJO-DL:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Görsel Stüdyo 2017 hakkında **MJO-DL:4022**
    ::: moniker-end

7. **Yerel kod hata ayıklama etkinleştirin** seçili olmadığından emin olun.

8. Projeyi derleyin.

9. Uzak bilgisayarda Visual Studio bilgisayarınızdaki Hata **Ayıklama** klasörüyle aynı yol olan bir klasör oluşturun: ** \<kaynak yolu>\MyWPF\MyWPF\bin\Debug**.

10. Visual Studio bilgisayarınızdan yeni oluşturduğunuz yürütülebilir dosyayı uzak bilgisayarda yeni oluşturulan klasöre kopyalayın.

    > [!CAUTION]
    > Kodda değişiklik yapmayın veya yeniden oluşturmayın (veya bu adımı yinelemeniz gerekir). Uzak makineye kopyaladığınız çalıştırılabilir işlem, yerel kaynağınızla ve sembollerinizle tam olarak eşleşmelidir.

    Projeyi el ile kopyalayabilir, Xcopy, Robocopy, Powershell veya diğer seçenekleri kullanabilirsiniz.

11. Uzaktan hata ayıklamanın hedef makinede çalıştığını unutmayın (Değilse **Başlat** menüsünde **Uzaktan Hata Ayıklama'yı** arayın). Uzaktan hata ayıklama penceresi şuna benziyor.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. Visual Studio'da hata ayıklamaya başlayın (**Hata Ayıklama > Hata Ayıklama**başlatın veya **F5).**

13. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.

     Gerekli kimlik bilgileri ağınızın güvenlik yapılandırmasına bağlı olarak değişir. Örneğin, bir etki alanı bilgisayarında etki alanı adınızı ve parolanızı girebilirsiniz. Etki alanı olmayan bir makinede, doğru parolayla birlikte makine <strong>MJO-DL\name@something.com</strong>adını ve geçerli bir kullanıcı hesabı adı girebilirsiniz.

     WPF uygulamasının ana penceresinin uzak bilgisayarda açık olduğunu görmeniz gerekir.

14. Gerekirse, kesme noktasına vurmak için harekete geçin. Kesme noktasının etkin olduğunu görmelisiniz. Değilse, uygulama sembolleri yüklenmedi. Yeniden deneyin ve bu işe yaramazsa, sembolleri yükleme ve [bunları anlama sembol dosyaları ve Visual Studio'nun sembol ayarlarından](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)nasıl giderdiği hakkında bilgi alın.

15. Visual Studio makinesinde, yürütmenin kesme noktasında durduğunu görmelisiniz.

    Uygulama tarafından kullanılması gereken kod dışı dosyalarınız varsa, bunları Visual Studio projesine eklemeniz gerekir. Ek dosyalar için proje klasörü oluşturun **(Çözüm Gezgini'nde,** **Yeni Klasör > ekle'yi**tıklatın). Ardından dosyaları klasöre ekleyin **(Çözüm Gezgini'nde,** **Varolan Öğe> ekle'yi**tıklatın, ardından dosyaları seçin). Her dosyanın **Özellikleri** sayfasında, **Kopyala'yı Her** **Zaman Kopyalamak**için Çıktı Dizini'ne ayarlayın.

## <a name="set-up-debugging-with-remote-symbols"></a>Uzaktan Sembollerle Hata Ayıklama'yı Ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Uzaktan Hata Ayıklama için Windows Güvenlik Duvarını Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)