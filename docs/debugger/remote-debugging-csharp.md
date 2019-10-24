---
title: A C# veya vb projesinde uzaktan hata ayıklama | Microsoft Docs
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
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730252"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Visual Studio 'da C# veya Visual Basic bir projede uzaktan hata ayıklama
Farklı bir bilgisayara dağıtılan bir Visual Studio uygulamasında hata ayıklamak için, uygulamanızı dağıttığınız bilgisayara Uzak araçları yükleyip çalıştırın, projenizi Visual Studio 'dan uzak bilgisayara bağlanacak şekilde yapılandırın ve ardından uygulamanızı çalıştırın.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Evrensel Windows uygulamaları (UWP) ile ilgili uzaktan hata ayıklama hakkında bilgi için bkz. [yüklü uygulama paketinin hatalarını ayıklama](debug-installed-app-package.md).

## <a name="requirements"></a>Gereksinimler

Uzaktan hata ayıklayıcı, Windows 7 ve Windows Server 2008 Service Pack 2 ' den başlayarak daha yeni (telefon değil) ve Windows Server sürümlerinde desteklenir. Gereksinimlerin tüm listesi için bkz. [gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmez. Yüksek gecikme veya düşük bant genişliğine sahip bir bağlantı (örneğin, Internet veya ülkeler arasında Internet üzerinden) için hata ayıklama önerilmez ve başarısız olabilir veya aşırı derecede yavaş olabilir.

## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Bazı senaryolarda, uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırmak en etkili olabilir. Daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırma](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="BKMK_setup"></a>Uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izinler eklemeniz gerekiyorsa, kimlik doğrulama modunu veya uzaktan hata ayıklayıcı bağlantı noktası numarasını değiştirin, bkz. [Uzaktan hata ayıklayıcıyı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_csharp"></a>Projede uzaktan hata ayıkla
Hata ayıklayıcı, uzak bir C# makineye görsel veya Visual Basic masaüstü uygulamaları dağıtabamaz, ancak yine de aşağıdaki gibi uzaktan hata ayıklaması yapabilirsiniz. Aşağıdaki yordamda, aşağıdaki çizimde gösterildiği gibi **Mjo-DL**adlı bir bilgisayarda hata ayıklamak istediğinizi varsayılmaktadır.

1. **MyWpf**ADLı bir WPF projesi oluşturun.

2. Kodu kolayca erişilen kodda bir yere kesme noktası ayarlayın.

    Örneğin, bir düğme işleyicisinde bir kesme noktası ayarlayabilirsiniz. Bunu yapmak için, MainWindow. xaml ' yi açın ve araç kutusundan bir düğme denetimi ekleyin, ardından düğmeye çift tıklayarak işleyiciyi açın.

3. Çözüm Gezgini, projeye sağ tıklayın ve **Özellikler**' i seçin.

4. **Özellikler** sayfasında **Hata Ayıkla** sekmesini seçin.

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. **Çalışma dizini** metin kutusunun boş olduğundan emin olun.

6. **Uzak makine kullan**' ı seçin ve metin kutusuna **yourmachinename: Port** yazın. (Bağlantı noktası numarası, uzaktan hata ayıklayıcı penceresinde gösterilir. Bağlantı noktası numarası her Visual Studio sürümünde 2 ' i artırır).

    Bu örnekte, şunu kullanın:
    ::: moniker range=">=vs-2019"
    **Mjo-DL: 4024** on Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **Mjo-DL: 4022** on Visual Studio 2017
    ::: moniker-end

7. **Yerel kod hata ayıklamasını etkinleştir** ' in seçili olmadığından emin olun.

8. Projeyi oluşturun.

9. Uzak bilgisayarda, Visual Studio bilgisayarınızdaki **hata ayıklama** klasörüyle aynı yol olan bir klasör oluşturun: **\<source yol > \MyWPF\MyWPF\bin\Debug**.

10. Visual Studio bilgisayarınızdan oluşturduğunuz yürütülebilir dosyayı uzak bilgisayardaki yeni oluşturulan klasöre kopyalayın.

    > [!CAUTION]
    > Kodda değişiklik yapmayın veya yeniden derleyin (veya bu adımı tekrarlamanız gerekir). Uzak makineye kopyaladığınız yürütülebilir dosya yerel kaynak ve sembollerle tam olarak eşleşmelidir.

    Projeyi el ile kopyalayabilir, xcopy, Robocopy, PowerShell veya diğer seçenekleri kullanabilirsiniz.

11. Uzaktan hata ayıklayıcının hedef makinede çalıştığından emin olun (yoksa, **Başlat** menüsünde **Uzaktan hata ayıklayıcı** için arama yapın). Uzaktan hata ayıklayıcı penceresi şuna benzer.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. Visual Studio 'da hata ayıklamayı başlatın (hata ayıklama **> başlatın**veya **F5**).

13. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.

     Gerekli kimlik bilgileri ağınızın güvenlik yapılandırmasına bağlı olarak farklılık gösterir. Örneğin, bir etki alanı bilgisayarında etki alanı adınızı ve parolanızı girebilirsiniz. Etki alanı olmayan bir makinede, makine adı ve <strong>MJO-DL\name@something.com</strong>gibi geçerli bir kullanıcı hesabı adı doğru parolayla birlikte girebilirsiniz.

     Uzak bilgisayarda WPF uygulamasının ana penceresinin açık olduğunu görmeniz gerekir.

14. Gerekirse, kesme noktasına isabet eden işlem yapın. Kesme noktasının etkin olduğunu görmeniz gerekir. Değilse, uygulamanın sembolleri yüklenmez. Yeniden deneyin ve bu işe yaramazsa sembolleri yükleme ve [sembol dosyalarını ve Visual Studio 'nun sembol ayarlarını anlama](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)hakkında bilgi alın.

15. Visual Studio makinesinde yürütmenin kesme noktasında durdurulduğunu görmeniz gerekir.

    Uygulama tarafından kullanılması gereken kod olmayan dosyalarınız varsa, bunları Visual Studio projesine dahil etmeniz gerekir. Ek dosyalar için bir proje klasörü oluşturun ( **Çözüm Gezgini** **> yeni klasör ekle**' ye tıklayın). Ardından dosyaları klasöre ekleyin ( **Çözüm Gezgini**, **var olan > Ekle**' ye tıklayın ve ardından dosyaları seçin). Her bir dosyanın **Özellikler** sayfasında, her **zaman kopyalamak**için **Çıkış Dizinine Kopyala** ' yı ayarlayın.

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak simgelerle hata ayıklamayı ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Windows Güvenlik Duvarı’nı Uzaktan Hata Ayıklama İçin Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)