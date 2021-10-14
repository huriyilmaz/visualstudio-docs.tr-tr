---
title: C# veya VB projesinde uzaktan hata ayıklama | Microsoft Docs
description: bu adım adım yönergeleri izleyerek bir Visual Studio C# veya Visual Basic uygulamasında bir uzak bilgisayardan hata ayıklamayı öğrenin.
ms.custom:
- remotedebugging"=
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 3a4395e54b5bf9a1e10840266496922e432a0816
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970106"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Visual Studio bir C# veya Visual Basic projesi üzerinde uzaktan hata ayıklama
farklı bir bilgisayara dağıtılan Visual Studio bir uygulamada hata ayıklamak için, uygulamanızı dağıttığınız bilgisayara uzak araçları yükleyip çalıştırın, projenizi Visual Studio uzak bilgisayara bağlanacak şekilde yapılandırın ve ardından uygulamanızı çalıştırın.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

uzaktan hata ayıklama evrensel Windows uygulamaları (UWP) hakkında bilgi için bkz. [yüklü uygulama paketinde hata ayıklama](debug-installed-app-package.md).

## <a name="requirements"></a>Gereksinimler

uzaktan hata ayıklayıcı, Windows server 2008 Service Pack 2 ' den başlayarak Windows 7 ve daha yeni (telefon değil) ve Windows sunucusu sürümlerinde desteklenir. Gereksinimlerin tüm listesi için bkz. [gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmez. Yüksek gecikme veya düşük bant genişliğine sahip bir bağlantı (örneğin, Internet veya ülkeler arasında Internet üzerinden) için hata ayıklama önerilmez ve başarısız olabilir veya aşırı derecede yavaş olabilir.

## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Bazı senaryolarda, uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırmak en etkili olabilir. Daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırma](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izinler eklemeniz gerekiyorsa, kimlik doğrulama modunu veya uzaktan hata ayıklayıcı bağlantı noktası numarasını değiştirin, bkz. [Uzaktan hata ayıklayıcıyı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a> Projede uzaktan hata ayıkla
hata ayıklayıcı, Visual C# veya Visual Basic masaüstü uygulamalarını uzak bir makineye dağıtabamaz, ancak yine de aşağıdaki gibi uzaktan hata ayıklaması yapabilirsiniz. Aşağıdaki yordamda, aşağıdaki çizimde gösterildiği gibi **Mjo-DL** adlı bir bilgisayarda hata ayıklamak istediğinizi varsayılmaktadır.

1. **MyWpf** ADLı bir WPF projesi oluşturun.

2. Kodu kolayca erişilen kodda bir yere kesme noktası ayarlayın.

    Örneğin, bir düğme işleyicisinde bir kesme noktası ayarlayabilirsiniz. Bunu yapmak için, MainWindow. xaml ' yi açın ve araç kutusundan bir düğme denetimi ekleyin, ardından düğmeye çift tıklayarak işleyiciyi açın.

3. Çözüm Gezgini, projeye sağ tıklayın ve **Özellikler**' i seçin.

4. **Özellikler** sayfasında **Hata Ayıkla** sekmesini seçin.

    ![Visual Studio Çözüm Gezgini özelliklerindeki hata ayıklama sekmesinin ekran görüntüsü. Uzak makine Kullan özelliği ' MJO-DL: 4022 ' olarak ayarlandı.](../debugger/media/remotedebuggercsharp.png)

5. **Çalışma dizini** metin kutusunun boş olduğundan emin olun.

6. **Uzak makine kullan**' ı seçin ve metin kutusuna **yourmachinename: Port** yazın. (Bağlantı noktası numarası, uzaktan hata ayıklayıcı penceresinde gösterilir. Bağlantı noktası numarası her Visual Studio sürümünde 2 ' i artırır).

    Bu örnekte, şunu kullanın:
    ::: moniker range="vs-2022"
    **mjo-DL: 4026** on Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2019"
    **mjo-DL: 4024** on Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **mjo-DL: 4022** on Visual Studio 2017
    ::: moniker-end

7. **Yerel kod hata ayıklamasını etkinleştir** ' in seçili olmadığından emin olun.

8. Projeyi derleyin.

9. uzak bilgisayarda Visual Studio bilgisayarınızdaki **hata ayıklama** klasörüyle aynı yol olan bir klasör oluşturun: **\<source path> \mywpf\mywpf\bin\debug**.

10. Visual Studio bilgisayarınızdan oluşturduğunuz yürütülebilir dosyayı uzak bilgisayardaki yeni oluşturulan klasöre kopyalayın.

    > [!CAUTION]
    > Kodda değişiklik yapmayın veya yeniden derleyin (veya bu adımı tekrarlamanız gerekir). Uzak makineye kopyaladığınız yürütülebilir dosya yerel kaynak ve sembollerle tam olarak eşleşmelidir.

    Projeyi el ile kopyalayabilir, XCopy, Robocopy, PowerShell veya diğer seçenekleri kullanabilirsiniz.

11. Uzaktan hata ayıklayıcının hedef makinede çalıştığından emin olun (yoksa, **Başlat** menüsünde **Uzaktan hata ayıklayıcı** için arama yapın). Uzaktan hata ayıklayıcı penceresi şuna benzer.

     ![Visual Studio 2017 uzaktan hata ayıklayıcı penceresinin ekran görüntüsü. Hata ayıklayıcının hedef makinede çalıştığını gösteren bir eylem listelenir.](../debugger/media/remotedebuggerwindow.png)

12. Visual Studio, hata ayıklamayı başlatın (hata ayıklama **> hata ayıklamayı başlatın** veya **F5**).

13. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.

     Gerekli kimlik bilgileri ağınızın güvenlik yapılandırmasına bağlı olarak farklılık gösterir. Örneğin, bir etki alanı bilgisayarında etki alanı adınızı ve parolanızı girebilirsiniz. Etki alanı olmayan bir makinede makine adı ve doğru parolayla birlikte geçerli bir kullanıcı hesabı adı girebilirsiniz <strong>MJO-DL\name@something.com</strong> .

     Uzak bilgisayarda WPF uygulamasının ana penceresinin açık olduğunu görmeniz gerekir.

14. Gerekirse, kesme noktasına isabet eden işlem yapın. Kesme noktasının etkin olduğunu görmeniz gerekir. Değilse, uygulamanın sembolleri yüklenmez. yeniden deneyin ve bu işe yaramazsa sembolleri yükleme ve [sembol dosyalarını ve Visual Studio sembol ayarlarını anlama](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)hakkında bilgi alın.

15. Visual Studio makinede yürütme 'nin kesme noktasında durdurulduğunu görmeniz gerekir.

    uygulama tarafından kullanılması gereken kod olmayan dosyalarınız varsa, bunları Visual Studio projesine dahil etmeniz gerekir. Ek dosyalar için bir proje klasörü oluşturun ( **Çözüm Gezgini** **> yeni klasör ekle**' ye tıklayın). Ardından dosyaları klasöre ekleyin ( **Çözüm Gezgini**, **var olan > Ekle**' ye tıklayın ve ardından dosyaları seçin). Her bir dosyanın **Özellikler** sayfasında, her **zaman kopyalamak** için **Çıkış Dizinine Kopyala** ' yı ayarlayın.

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak simgelerle hata ayıklamayı ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
