---
title: Bir C++ projede uzaktan hata ayıklama | Microsoft Docs
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
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730319"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Visual Studio 'da C++ bir projede uzaktan hata ayıklama
Farklı bir bilgisayardaki Visual Studio uygulamasında hata ayıklamak için, uygulamanızı dağıtacağınız bilgisayara Uzak araçları yükleyip çalıştırın, projenizi Visual Studio 'dan uzak bilgisayara bağlanacak şekilde yapılandırın ve ardından uygulamanızı dağıtıp çalıştırın.

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

## <a name="remote_cplusplus"></a>Bir C++ projede uzaktan hata ayıklama
 Aşağıdaki yordamda, projenin adı ve yolu C:\remotetemp\MyMfc olur ve uzak bilgisayarın adı **Mjo-DL**' dir.

1. **Mymfc** ADLı bir MFC uygulaması oluşturun.

2. @No__t_1 başlangıcında **MainFrm. cpp**gibi kolayca erişilen uygulamada herhangi bir yere bir kesme noktası ayarlayın.

3. Çözüm Gezgini, projeye sağ tıklayın ve **Özellikler**' i seçin. **Hata ayıklama** sekmesini açın.

4. Hata ayıklayıcıyı **uzak Windows hata ayıklayıcıya** **başlatılacak şekilde** ayarlayın.

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. Özelliklerde aşağıdaki değişiklikleri yapın:

   |Ayar|Değer|
   |-|-|
   |Uzak komut|C:\remotetemp\mymfc.exe|
   |Çalışma dizini|C:\remotetemp|
   |Uzak sunucu adı|MJO-DL:*BağlantıNoktasıNumarası*|
   |Bağlanma|Windows kimlik doğrulaması ile uzaktan|
   |Hata ayıklayıcı türü|Yalnızca yerel|
   |Dağıtım dizini|Ni c:\remotetemp|
   |Dağıtılacak ek dosyalar|C:\data\mymfcdata.exe.|

    Ek dosyalar dağıtırsanız (isteğe bağlı), klasörün her iki makinede de mevcut olması gerekir.

6. Çözüm Gezgini, çözüme sağ tıklayın ve **Configuration Manager**' i seçin.

7. **Hata ayıklama** yapılandırması için **Dağıt** onay kutusunu seçin.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Hata ayıklamayı Başlat (hata ayıklama **> başlatın**veya **F5**).

9. Yürütülebilir dosya otomatik olarak uzak bilgisayara dağıtılır.

10. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.

     Gerekli kimlik bilgileri ağınızın güvenlik yapılandırmasına özgüdür. Örneğin, bir etki alanı bilgisayarında bir güvenlik sertifikası seçebilir veya etki alanı adınızı ve parolanızı girebilirsiniz. Etki alanı olmayan bir makinede, makine adı ve <strong>MJO-DL\name@something.com</strong>gibi geçerli bir kullanıcı hesabı adı doğru parolayla birlikte girebilirsiniz.

11. Visual Studio bilgisayarında yürütmenin kesme noktasında durdurulduğunu görmeniz gerekir.

    > [!TIP]
    > Alternatif olarak, dosyaları ayrı bir adım olarak dağıtabilirsiniz. **Çözüm Gezgini,** **mymfc** düğümüne sağ tıklayın ve ardından **Dağıt**' ı seçin.

    Uygulama için gerekli kod olmayan dosyalarınız varsa, bu dosyaları **uzak Windows hata ayıklayıcı** sayfasında **dağıtılacak ek dosyalar** içinde belirtebilirsiniz.

    Alternatif olarak, dosyaları projenize dahil edebilir ve her bir dosyanın **Özellikler** sayfasında **içerik** özelliğini **Evet** olarak ayarlayabilirsiniz. Bu dosyalar, **uzak Windows hata ayıklayıcı** sayfasında belirtilen **dağıtım dizinine** kopyalanır. Ayrıca, **dosya kopyalamak** Için **öğe türünü** değiştirebilir ve dosyaların **dağıtım dizininin**bir alt klasörüne kopyalanması gerekiyorsa ek özellikler belirtebilirsiniz.

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak simgelerle hata ayıklamayı ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Windows Güvenlik Duvarı’nı Uzaktan Hata Ayıklama İçin Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)