---
title: Yükleme veya yükseltme sorunlarını giderme
description: Bazen işler ters gidebilir. Yükleme veya Visual Studio başarısız olursa, bu sayfa yardımcı olabilir.
ms.date: 06/24/2020
ms.custom: vs-acquisition
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 802e4cfb78a9302bd24bca55cda1bf9eab79f9ef
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387833"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Yükleme Visual Studio yükseltme sorunlarını giderme

> [!IMPORTANT]
> Yüklemeyle ilgili sorun mu var? Size yardımcı olabiliriz. Yükleme sohbeti [**(yalnızca**](https://visualstudio.microsoft.com/vs/support/#talktous) İngilizce) destek seçeneği sunuyoruz.

Bu sorun giderme kılavuzu, yükleme sorunlarının çoğunu çözmesi gereken adım adım yönergeler içerir.

## <a name="online-installations"></a>Çevrimiçi yüklemeler

Aşağıdaki adımlar tipik bir çevrimiçi yükleme için iyileştirilmiştir. Çevrimdışı bir yüklemeyi etkileyen bir sorun için [bkz. Çevrimdışı yükleme sorunlarını giderme.](#offline-installations)

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>1. Adım: Bu sorunun bilinen bir sorun olup olmadığını denetleme

::: moniker range="vs-2017"

Microsoft'un düzeltme üzerinde Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Soruna geçici bir çözüm olup olamay için sürüm [notlarımızın Bilinen Sorunlar bölümüne bakın.](/visualstudio/releasenotes/vs2017-relnotes#-known-issues)

::: moniker-end

::: moniker range=">=vs-2019"

Microsoft'un düzeltme üzerinde Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Soruna geçici bir çözüm olup olamay için sürüm [notlarımızın Bilinen Sorunlar bölümüne bakın.](/visualstudio/releases/2019/release-notes#-known-issues)

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>2. Adım: 2. Adım: Visual Studio

Onarım birçok yaygın güncelleştirme sorununa çözüm sağlar. içinde onarım işlevinin ne zaman ve nasıl kullanılası hakkında daha fazla bilgi Visual Studio bkz. [Visual Studio.](repair-visual-studio.md)

### <a name="step-3---check-with-the-developer-community"></a>3. Adım: Geliştirici topluluğuna göz at

hata iletinizi arama ve [Visual Studio Geliştirici Topluluğu.](https://aka.ms/feedback/suggest?space=8) Topluluğun diğer üyeleri, soruna bir çözüm belgeletirdi.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>4. Adım: Yükseltme Visual Studio Yükleyicisi için Visual Studio Yükleyicisi dizinini silme

Bu Visual Studio Yükleyicisi önyükleyicisi, uygulamanın geri kalanını yüken küçük bir hafif yürütülebilir Visual Studio Yükleyicisi. Dosya Visual Studio Yükleyicisi ve ardından önyükleyiciyi yeniden çalıştırma bazı güncelleştirme hatalarını çözebilir.

> [!NOTE]
> Aşağıdaki eylemlerin gerçekleştirerek Visual Studio Yükleyicisi yeniden yüklenir ve yükleme meta verileri sıfırlanır.

::: moniker range="vs-2017"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio Yükleyicisi silin. Genellikle dizini `C:\Program Files (x86)\Microsoft Visual Studio\Installer` olur.
3. Önyükleyiciyi Visual Studio Yükleyicisi çalıştırın. Önyükleyiciyi İndirilenler klasörünüzde bir desenden sonra bir dosya adıyla `vs_[Visual Studio edition]__*.exe` bulabilirsiniz. Bu uygulamayı bulamazsanız önyükleyiciyi indirmek için Visual Studio indirmeler sayfasına gidip [Visual Studio.](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)  Ardından, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
4. Yeniden yükleme veya güncelleştirme Visual Studio deneyin. Yükleyici başarısız olursa sonraki adıma gidin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio Yükleyicisi silin. Genellikle dizini `C:\Program Files (x86)\Microsoft Visual Studio\Installer` olur.
3. Önyükleyiciyi Visual Studio Yükleyicisi çalıştırın. Önyükleyiciyi İndirilenler klasörünüzde bir desenden sonra bir dosya adıyla `vs_[Visual Studio edition]__*.exe` bulabilirsiniz. Bu uygulamayı bulamazsanız önyükleyiciyi indirmek için Visual Studio indirmeler sayfasına gidip [Visual Studio.](https://visualstudio.microsoft.com/downloads)  Ardından, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
4. Yeniden yükleme veya güncelleştirme Visual Studio deneyin. Yükleyici başarısız olursa sonraki adıma gidin.

::: moniker-end

### <a name="step-5---report-a-problem"></a>5. Adım - Sorun bildirme

Bozuk dosyalarla ilgili olanlar gibi bazı durumlarda, sorunların olay temelinde de bakilmesi gerekir. Size yardımcı olmak için lütfen şunları yapın:

::: moniker range="vs-2017"

1. Kurulum günlüklerinizi toplayın. Ayrıntılar [için bkz. Visual Studio yükleme günlüklerini](#installation-logs) nasıl edinebilirsiniz?
2. Visual Studio Yükleyicisi'yi açın ve sorun **bildirin'e** tıklar ve Visual Studio geri bildirim aracını açın.
![Geri Bildirim Sağla düğmesine tıklayarak geri bildirim aracını açabilirsiniz](media/report-a-problem.png)
3. Sorun raporunuz için bir başlık girin ve ilgili ayrıntıları girin. Ekler **bölümüne** gitmek için **Sonraki'ne** tıklayın ve oluşturulan günlük dosyasını (genellikle dosyanın olduğu yer) iliştirin. `%TEMP%\vslogs.zip`
4. Sorun **raporlarınızı** gözden geçirmek için Sonraki'ne ve ardından **Gönder'e tıklayın.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Kurulum günlüklerinizi toplayın. Ayrıntılar [için bkz. Visual Studio yükleme günlüklerini](#installation-logs) nasıl edinebilirsiniz?
2. Visual Studio Yükleyicisi'yi açın ve sorun **bildirin'e** tıklar ve Visual Studio geri bildirim aracını açın.
![Geri Bildirim Sağla düğmesine tıklayarak geri bildirim aracını açabilirsiniz](media/vs-2019/vs-installer-report-problem.png)
3. Sorun raporunuz için bir başlık girin ve ilgili ayrıntıları girin. Ekler **bölümüne** gitmek için **Sonraki'ne** tıklayın ve oluşturulan günlük dosyasını (genellikle dosyanın olduğu yer) iliştirin. `%TEMP%\vslogs.zip`
4. Sorun **raporlarınızı** gözden geçirmek için Sonraki'ne ve ardından **Gönder'e tıklayın.**

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>6. Adım - Yükleme InstallCleanup.exe kaldırmak için uygulama çalıştırma

Son bir tesis olarak, tüm [yükleme Visual Studio](remove-visual-studio.md) ürün bilgilerini kaldırmak için bu dosyaları kaldırabilirsiniz.

1. Remove [Visual Studio](remove-visual-studio.md).
2. Yükseltme sorunlarını düzeltmek için 4. Adım - Visual Studio Yükleyicisi dizinini silme [konusunda açıklanan önyükleyiciyi yeniden çalıştırma.](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)
3. Yeniden yükleme veya güncelleştirme Visual Studio deneyin.

### <a name="step-7---contact-us-optional"></a>7. Adım - Bize ulaşın (isteğe bağlı)

Önceki adımlardan hiçbiri başarıyla yüklemenizi veya yükseltmenizi Visual Studio, daha [](https://visualstudio.microsoft.com/vs/support/#talktous) fazla yardım için canlı sohbet destek seçeneğimizi (yalnızca İngilizce) kullanarak bizimle iletişime geçin.

## <a name="offline-installations"></a>Çevrimdışı yüklemeler

Burada, çevrimdışı yükleme oluşturmanıza ve ardından yerel bir [](create-an-offline-installation-of-visual-studio.md) düzenden yüklemenize yardımcı olacak bilinen sorunların ve bazı geçici çözümlerin yer almaktadır.

| Sorun       | Öğe                   | Çözüm |
| ----------- | ---------------------- | -------- |
| Kullanıcıların dosyalara erişimi yok. | izinler (ACL'ler) | Çevrimdışı yüklemeyi paylaşmadan önce diğer kullanıcılara Okuma erişimi vermek  için izinleri (ACL' ler) ayarlayasınız. |
| Yeni iş yükleri, bileşenler veya diller yük devretmez.  | `--layout`  | Kısmi bir düzenden yükleniyorsa ve daha önce bu kısmi düzende indirilmiş iş yüklerini, bileşenleri veya dilleri seçerek İnternet erişiminiz olduğundan emin olun. |

Bir ağ yüklemesi ile ilgili sorunları çözme hakkında daha fazla [bilgi için,](create-a-network-installation-of-visual-studio.md)bkz. Ağ yüklemesi yükleme veya kullanma sırasında [ağ ile ilgili Visual Studio.](troubleshooting-network-related-errors-in-visual-studio.md)

## <a name="installation-logs"></a>Yükleme günlükleri

Kurulum günlükleri, yükleme sorunlarının çoğunu gidermek için gereklidir. Sorun Bildir'i kullanarak bir [sorun](../ide/how-to-report-a-problem-with-visual-studio.md) gönderdiğinizde Visual Studio Yükleyicisi günlükler otomatik olarak raporunuza eklenir.

Microsoft Desteği iletişim kurmanız halinde, günlük toplama aracını kullanarak bu kurulum [günlüklerini Microsoft Visual Studio .NET Framework gerekir.](https://www.microsoft.com/download/details.aspx?id=12493) Günlük toplama aracı, .NET Framework, Windows SDK ve Visual Studio tarafından yüklenmiş tüm bileşenlerden kurulum SQL Server. Ayrıca bilgisayar bilgilerini, bir Windows Installer envanterini ve Visual Studio Yükleyicisi, Windows Installer ve Sistem Geri Yükleme için Windows olay günlüğü bilgilerini Sistem Geri Yükleme.

Günlükleri toplamak için:

1. [Aracı indirin.](https://www.microsoft.com/download/details.aspx?id=12493)
2. Yönetici komut istemini açın.
3. Aracı `Collect.exe` kaydeden dizinden çalıştırın.
4. Sonuçta elde `vslogs.zip` edilen dosyayı `%TEMP%` dizininize (örneğin, ) `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` bulun.

> [!NOTE]
> Araç, başarısız yüklemenin altında çalıştır olduğu kullanıcı hesabı altında çalıştırıla çalışmalı. Aracı farklı bir kullanıcı hesabından çalıştıracaksanız, başarısız yüklemenin çalıştır olduğu `–user:<name>` kullanıcı hesabını belirtme seçeneğini ayarlayın. Ek `Collect.exe -?` seçenekler ve kullanım bilgileri için yönetici komut isteminden komutunu çalıştırın.

## <a name="live-help"></a>Canlı yardım

Bu sorun giderme kılavuzunda listelenen çözümler, bu çözümü başarıyla yüklemenize [](https://visualstudio.microsoft.com/vs/support/#talktous) veya yükseltmeye yardımcı Visual Studio, daha fazla yardım için canlı sohbet destek seçeneğimizi (yalnızca İngilizce) kullanın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu onarın](repair-visual-studio.md)
* [Kaldırma Visual Studio](remove-visual-studio.md)
* [Güvenlik duvarı veya ara sunucu Visual Studio azure hizmetlerini yükleme ve kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
