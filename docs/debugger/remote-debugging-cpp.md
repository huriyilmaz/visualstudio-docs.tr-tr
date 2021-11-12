---
title: C++ Project |'da Uzaktan Hata Ayıklama Microsoft Docs
description: Bu adım adım yönergeleri izleyerek Visual Studio bir C++ uygulamasında hata ayıklamayı öğrenin.
ms.custom: remotedebugging
ms.date: 11/11/2021
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: a23952fb49154e288f2de29db4c0893ed9483ecc
ms.sourcegitcommit: 00451b7258ab86e259d0fe787669330b61efa8e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2021
ms.locfileid: "132364988"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Visual Studio'de C++ Project Uzaktan Visual Studio

Farklı bir bilgisayarda Visual Studio uygulamanın hata ayıklaması için, uygulamanızı dağıtacak bilgisayarınıza uzak araçları yükleyin ve çalıştırın, projenizi Visual Studio'den uzak bilgisayara bağlanacak şekilde yapılandırın ve ardından uygulamanızı dağıtın ve çalıştırın.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Universal Windows Apps 'de (UWP) uzaktan hata ayıklama hakkında bilgi için bkz. Yüklü [Uygulama Paketinde Hata Ayıklama.](debug-installed-app-package.md)

## <a name="requirements"></a>Gereksinimler

Uzaktan hata ayıklayıcı Windows 7 ve daha yeni sürümlerde ve Windows Server 2008 Service Pack 2 ile başlayan Windows Server sürümlerinde de desteklemektedir. Gereksinimlerin tam listesi için bkz. [Gereksinimler.](../debugger/remote-debugging.md#requirements_msvsmon)

> [!NOTE]
> Ara sunucu üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmiyor. Çevirmeli İnternet gibi yüksek gecikme süresi veya düşük bant genişliği bağlantısı üzerinden veya ülkeler arasında İnternet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya kabul edilemez düzeyde yavaş olabilir.

## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download-cpp.md)]

> [!TIP]
> Bazı senaryolarda, uzak hata ayıklayıcısını bir dosya paylaşımından çalıştırmak en verimli olabilir. Daha fazla bilgi için [bkz. Bir dosya paylaşımından uzaktan hata ayıklayıcıyı çalıştırma.](../debugger/remote-debugging.md#fileshare_msvsmon)

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izin eklemeniz, uzak hata ayıklayıcı için kimlik doğrulama modunu veya bağlantı noktası numarasını değiştirmenizi gerekirse, bkz. Uzaktan hata [ayıklayıcıyı yapılandırma.](../debugger/remote-debugging.md#configure_msvsmon)

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a> C++ projesinde uzaktan hata ayıklama
 Aşağıdaki yordamda, projenin adı ve yolu C:\remotetemp\MyMfc ve uzak bilgisayarın adı **MJO-DL'dir.**

1. **mymfc** adlı bir MFC uygulaması oluşturun.

2. Uygulamanın herhangi bir yerinde, örneğin **MainFrm.cpp** içinde, uygulamasının başında kolayca ulaşacak bir kesme noktası `CMainFrame::OnCreate` ayarlayın.

3. Bu Çözüm Gezgini projeye sağ tıklayın ve Özellikler'i **seçin.** Hata **Ayıklama sekmesini** açın.

4. Hata **Ayıklayıcı'nın başlatılması için Uzak** **Hata Windows ayarlayın.**

    ![Visual Studio Çözüm Gezgini Özellikler'de Hata Ayıklama sekmesinin ekran görüntüsü. Başlat için Hata Ayıklayıcısı özelliği Uzak Hata Ayıklayıcı Windows ayarlanır.](../debugger/media/remotedebuggingcplus.png)

5. Özelliklerde aşağıdaki değişiklikleri yapın:

   |Ayar|Değer|
   |-|-|
   |Uzak Komut|C:\remotetemp\mymfc.exe|
   |Çalışma Dizini|C:\remotetemp|
   |Uzak Sunucu Adı|MJO-DL:*bağlantı noktası numarası*|
   |Bağlantı|Windows Kimlik Doğrulaması ile uzak|
   |Hata Ayıklayıcı Türü|Yalnızca Yerel|
   |Dağıtım Dizini|C:\remotetemp.|
   |Dağıtılan Ek Dosyalar|C:\data\mymfcdata.txt.|

    Ek dosyalar dağıtırsanız (isteğe bağlı), klasör her iki makinede de mevcut olması gerekir.

6. Bu Çözüm Gezgini, çözüme sağ tıklayın ve **Yapılandırma Yöneticisi.**

7. Hata **ayıklama yapılandırması** için Dağıt **onay kutusunu** seçin.

    ![Uygulamanın Yapılandırma Yöneticisi ekran Visual Studio Çözüm Gezgini. Hata ayıklama yapılandırması seçilidir ve Dağıt seçeneği işaretlidir.](../debugger/media/remotedebugcplusdeploy.png)

8. Hata ayıklamayı başlatma (**Hata ayıklama > Hata Ayıklamayı Başlat** veya **F5**).

9. Yürütülebilir dosya otomatik olarak uzak bilgisayara dağıtılır.

10. İstendiğinde, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.

     Gerekli kimlik bilgileri, ağ güvenlik yapılandırmanıza özeldir. Örneğin, bir etki alanı bilgisayarda bir güvenlik sertifikası seçebilir veya etki alanı adınızı ve parolanızı girebilirsiniz. Etki alanı olmayan bir makinede, makine adını ve gibi geçerli bir kullanıcı hesabı adını ve <strong>MJO-DL\name@something.com</strong> doğru parolayı girebilirsiniz.

11. Bu Visual Studio kesme noktası üzerinde yürütmenin durdurulmuş olduğunu görüyor olun.

    > [!TIP]
    > Alternatif olarak, dosyaları ayrı bir adım olarak dağıtabilirsiniz. Uygulama Çözüm Gezgini **mymfc** düğümüne sağ tıklayın ve dağıt'ı  **seçin.**

    Uygulama için gerekli olan kod dışı dosyalarınız varsa, bunları Uzak Dosya Hata Ayıklayıcısı  sayfasında dağıtıla diğer dosyalar'da noktalı virgülle ayrılmış **bir Windows belirtebilirsiniz.**

    Alternatif olarak, dosyaları projenize dahil edebilirsiniz ve  her  dosyanın Özellikler sayfasında İçerik **özelliğini Evet** olarak ayarlayın. Bu dosyalar Uzak Sunucu Hata **Ayıklayıcısı sayfasında** belirtilen **Dağıtım Windows kopyalanır.** Ayrıca, Dosyaların Dağıtım **Dizini'nin** bir alt klasörüne kopyalanmış olması gerekirse Öğe Türü'nü Dosya Kopyala olarak değiştirebilir ve ek özellikler  **belirtebilirsiniz.**

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak Sembollerle Hata Ayıklamayı Ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Uzaktan Hata Windows Güvenlik Duvarı'nı yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)