---
title: Uzaktan Hata Ayıklama C++ Projesi | Microsoft Dokümanlar
ms.custom: remotedebugging
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
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302114"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Visual Studio'da C++ Projesinin Uzaktan Hata Ayıklanması
Farklı bir bilgisayarda bir Visual Studio uygulamasını hata ayıklamak için, uygulamanızı dağıtacağınız bilgisayardaki uzak araçları yükleyin ve çalıştırın, Projenizi Visual Studio'dan uzak bilgisayara bağlanacak şekilde yapılandırın ve ardından uygulamanızı dağıtın ve çalıştırın.

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

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a>Uzaktan hata ayıklama c++ projesi
 Aşağıdaki yordamda, projenin adı ve yolu C:\remotetemp\MyMfc ve uzak bilgisayarın adı **MJO-DL'dir.**

1. **mymfc** adında bir MFC uygulaması oluşturun.

2. Uygulamada kolayca ulaşılabilen bir mola noktası ayarlayın, örneğin **MainFrm.cpp'de**, başında `CMainFrame::OnCreate`.

3. Çözüm Gezgini'nde projeye sağ tıklayın ve **Özellikler'i**seçin. Hata **Ayıklama** sekmesini açın.

4. Hata **Ayıklama'yı** **Uzak Windows Hata Ayıklama'ya**başlatmak için ayarlayın.

    ![Uzaktan Hata DinlemeCPlus](../debugger/media/remotedebuggingcplus.png "Uzaktan Hata DinlemeCPlus")

5. Özelliklerde aşağıdaki değişiklikleri yapın:

   |Ayar|Değer|
   |-|-|
   |Uzaktan Komut|C:\remotetemp\mymfc.exe|
   |Çalışma Rehberi|C:\remotetemp|
   |Uzak Sunucu Adı|MJO-DL:*bağlantı noktası numarası*|
   |Bağlantı|Windows Kimlik Doğrulamalı Uzaktan Kumanda|
   |Hata Ayıklama Türü|Yalnızca Yerel|
   |Dağıtım Dizini|C:\remotetemp.|
   |Dağıtılabilmek Için Ek Dosyalar|C:\data\mymfcdata.txt.|

    Ek dosyalar (isteğe bağlı) dağırsanız, klasörün her iki makinede de bulunması gerekir.

6. Solution Explorer'da, çözüme sağ tıklayın ve **Configuration Manager'ı**seçin.

7. Hata **Ayıklama** yapılandırması için **Dağıt** onay kutusunu seçin.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Hata ayıklama başlatın (**Hata Ayıklama > Başlat Hata Ayıklama**veya **F5**).

9. Çalıştırılabilir otomatik olarak uzak bilgisayara dağıtılır.

10. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.

     Gerekli kimlik bilgileri ağınızın güvenlik yapılandırmasına özgüdir. Örneğin, bir etki alanı bilgisayarında bir güvenlik sertifikası seçebilir veya etki alanı adınızı ve parolanızı girebilirsiniz. Etki alanı olmayan bir makinede, doğru parolayla birlikte makine <strong>MJO-DL\name@something.com</strong>adını ve geçerli bir kullanıcı hesabı adı girebilirsiniz.

11. Visual Studio bilgisayarında yürütmenin kesme noktasında durdurulduğunu görmelisiniz.

    > [!TIP]
    > Alternatif olarak, dosyaları ayrı bir adım olarak dağıtabilirsiniz. Çözüm **Gezgini'nde** **mymfc** düğümüne sağ tıklayın ve ardından **Dağıt'ı**seçin.

    Uygulama tarafından gerekli olan kod dışı dosyalarınız varsa, bunları **Uzak Windows Hata Ayıklayıcı** sayfasında **dağıtılabilen Ek Dosyalar'da** belirtebilirsiniz.

    Alternatif olarak, dosyaları projenize ekleyebilir ve Her dosya için **Özellikler** sayfasında **İçerik** özelliğini **Evet** olarak ayarlayabilirsiniz. Bu dosyalar **Uzak Windows Hata Ayıklama** sayfasında belirtilen **Dağıtım Dizini** kopyalanır. **Ayrıca,** Dosyakopyalama öğesi öğesini değiştirebilir **ve** dosyaların **Dağıtım Dizininin**bir alt klasörüne kopyalanması gerekiyorsa, orada ek özellikler belirtebilirsiniz.

## <a name="set-up-debugging-with-remote-symbols"></a>Uzaktan Sembollerle Hata Ayıklama'yı Ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Uzaktan Hata Ayıklama için Windows Güvenlik Duvarını Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)