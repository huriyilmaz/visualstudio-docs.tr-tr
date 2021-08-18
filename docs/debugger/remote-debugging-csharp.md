---
title: C# veya VB projesinde Uzaktan Hata Ayıklama | Microsoft Docs
description: Bu adım adım yönergeleri izleyerek Visual Studio bir C# Visual Basic uygulamanın hata ayıklaması yapmayı öğrenin.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 4d650fe2f99dcbaa58e0d786e9981ca35ef1a265
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112573"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Bir C# veya Visual Basic projesinde Uzaktan Hata Ayıklama Visual Studio
Farklı bir bilgisayarda dağıtılan bir Visual Studio uygulamasında hata ayıklamak için, uygulamayı dağıtmış olduğunuz bilgisayarda uzak araçları yükleyin ve çalıştırın, projenizi Visual Studio'den uzak bilgisayara bağlanacak şekilde yapılandırarak ve ardından uygulamanızı çalıştırın.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Universal Windows Apps 'de (UWP) uzaktan hata ayıklama hakkında bilgi için bkz. Yüklü [Uygulama Paketinde Hata Ayıklama.](debug-installed-app-package.md)

## <a name="requirements"></a>Gereksinimler

Uzaktan hata ayıklayıcısı Windows Server 2008 Service Pack 2 ile başlayan Windows Windows Server 7 ve daha yeni sürümlerde (telefon değil) ve sürümlerinde de desteklemektedir. Gereksinimlerin tam listesi için bkz. [Gereksinimler.](../debugger/remote-debugging.md#requirements_msvsmon)

> [!NOTE]
> Ara sunucu üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmiyor. Çevirmeli İnternet gibi yüksek gecikme süresi veya düşük bant genişliği bağlantısı üzerinden veya ülkeler arasında İnternet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya kabul edilemez düzeyde yavaş olabilir.

## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Bazı senaryolarda, uzak hata ayıklayıcısını bir dosya paylaşımından çalıştırmak en verimli olabilir. Daha fazla bilgi için [bkz. Bir dosya paylaşımından uzaktan hata ayıklayıcıyı çalıştırma.](../debugger/remote-debugging.md#fileshare_msvsmon)

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izin eklemeniz, uzak hata ayıklayıcı için kimlik doğrulama modunu veya bağlantı noktası numarasını değiştirmenizi gerekirse, bkz. Uzaktan hata [ayıklayıcıyı yapılandırma.](../debugger/remote-debugging.md#configure_msvsmon)

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a> Projede uzaktan hata ayıklama
Hata ayıklayıcı Visual C# veya Visual Basic masaüstü uygulamalarını uzak bir makineye dağıtamaz, ancak yine de aşağıdaki gibi uzaktan hata ayıklama yapabilirsiniz. Aşağıdaki yordamda, aşağıdaki çizimde gösterildiği gibi **MJO-DL** adlı bir bilgisayarda hata ayıklamak istediğiniz varsaylanmıştır.

1. **MyWpf** adlı bir WPF projesi oluşturun.

2. Kodun içinde kolayca erişen bir kesme noktası ayarlayın.

    Örneğin, bir düğme işleyicisinde kesme noktası ayarlayabilirsiniz. Bunu yapmak için MainWindow.xaml'i açın ve Araç Kutusundan bir Düğme denetimi ekleyin, ardından düğmeye çift tıklayarak işleyicisini açın.

3. Bu Çözüm Gezgini projeye sağ tıklayın ve Özellikler'i **seçin.**

4. Özellikler **sayfasında** Hata Ayıkla **sekmesini** seçin.

    ![Visual Studio Çözüm Gezgini Özellikler'de Hata Ayıkla sekmesinin ekran görüntüsü. Uzak makine kullan özelliği 'MJO-DL:4022' olarak ayarlanır.](../debugger/media/remotedebuggercsharp.png)

5. Çalışma dizini **metin kutusunun boş** olduğundan emin olun.

6. Uzak **makine kullan'ı** seçin ve metin kutusuna **yourmachinename:port** yazın. (Bağlantı noktası numarası, uzak hata ayıklayıcı penceresinde gösterilir. Bağlantı noktası numarası, her bir sürümde 2'Visual Studio).

    Bu örnekte şunları kullanın:
    ::: moniker range=">=vs-2019"
    **Visual Studio 2019'da MJO-DL:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    **Visual Studio 2017'de MJO-DL:4022**
    ::: moniker-end

7. Yerel kodda **hata ayıklamayı etkinleştir'in seçili** olduğundan emin olun.

8. Projeyi derleyin.

9. Uzak bilgisayarda, Visual Studio bilgisayarınızda Hata Ayıklama  klasörüyle aynı yol olan bir klasör oluşturun: **\<source path> \MyWPF\MyWPF\bin\Debug**.

10. Yeni oluşturduğunuz yürütülebilir dosyayı Visual Studio uzak bilgisayarda yeni oluşturulan klasöre kopyalayın.

    > [!CAUTION]
    > Kodda değişiklik yapma veya yeniden oluşturma (veya bu adımı yinelemeniz gerekir). Uzak makineye kopyalanmış yürütülebilir dosya, yerel kaynağınız ve sembolleriniz ile tam olarak eşleşmeli.

    Projeyi el ile kopyalayıp XCopy, Robocopy, PowerShell veya diğer seçenekleri kullanabilirsiniz.

11. Hedef makinede uzaktan hata ayıklayıcının çalıştırıldıklarına emin olun (Çalışmıyorsa Başlat menüsünde **Uzaktan** Hata **Ayıklayıcı'ya gidin).** Uzaktan hata ayıklayıcısı penceresi aşağıdaki gibi görünür.

     ![Visual Studio 2017 Uzaktan Hata Ayıklayıcısı penceresinin ekran görüntüsü. Hedef makinede hata ayıklayıcının çalıştır olduğunu gösteren bir eylem listelenir.](../debugger/media/remotedebuggerwindow.png)

12. Bu Visual Studio hata ayıklamayı başlat (**Hata Ayıklamayı Başlat >** veya **F5 ).**

13. İstendiğinde, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.

     Gerekli kimlik bilgileri ağ güvenlik yapılandırmasına bağlı olarak değişir. Örneğin, bir etki alanı bilgisayarına etki alanı adınızı ve parolanızı girebilirsiniz. Etki alanı olmayan bir makinede, makine adını ve gibi geçerli bir kullanıcı hesabı adını ve <strong>MJO-DL\name@something.com</strong> doğru parolayı girebilirsiniz.

     WPF uygulamasının ana penceresinin uzak bilgisayarda açık olduğunu görüyor olun.

14. Gerekirse kesme noktasıyla ilgili eyleme geçin. Kesme noktası'nın etkin olduğunu görüyor olun. Değilse, uygulamanın sembolleri yüklenmez. Yeniden deneyin ve işe işelenmiyorsa sembolleri yükleme ve sembol dosyalarını anlama ve sembol ayarlarını Visual Studio giderme konusunda [bilgi edinebilirsiniz.](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

15. Sanal Visual Studio kesme noktası üzerinde yürütmenin durdurulmuş olduğunu görüyoruz.

    Uygulama tarafından kullanılacak kod olmayan dosyalarınız varsa, bunları uygulama projesine Visual Studio gerekir. Ek dosyalar için bir proje klasörü oluşturun (dosyanın Çözüm Gezgini Yeni **Klasör** **ekle'> tıklayın).** Ardından dosyaları klasöre ekleyin (dosyanın **Çözüm Gezgini, Var** Olan **Öğe > Ekle'ye tıklayın** ve ardından dosyaları seçin). Her **dosyanın Özellikler** sayfasında Çıkış Dizinine **Kopyala'ya her zaman kopyala** olarak **ayarlayın.**

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak Sembollerle Hata Ayıklamayı Ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Uzaktan Hata Windows Güvenlik Duvarı'nı yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)