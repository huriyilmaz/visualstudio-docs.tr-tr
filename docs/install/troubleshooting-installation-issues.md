---
title: Sorun giderme yükleme veya yükseltme sorunları
description: Bazen işler ters gidebilir. Visual Studio yüklemeniz veya yükseltmeniz başarısız olursa, bu sayfa yardımcı olabilir.
ms.date: 03/23/2020
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 97cc0dd72b54795342d8c4f66a90bbd1ae4a7272
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233108"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Sorun Giderme Visual Studio yükleme ve yükseltme sorunları

> [!IMPORTANT]
> Yükleme sorunu yaşıyor musunuz? Yardım edebiliriz. Yükleme [**sohbeti**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) destek seçeneği sunuyoruz.

Bu sorun giderme kılavuzu, çoğu yükleme sorunlarını çözmesi gereken adım adım yönergeleri içerir.

## <a name="online-installations"></a>Çevrimiçi kurulumlar

Aşağıdaki adımlar tipik bir çevrimiçi yükleme için optimize edilebiyi optimize edin. Çevrimdışı yüklemeyi etkileyen bir sorun için lütfen [çevrimdışı yüklemenin nasıl giderilengiderilen giderilene](#offline-installations)bakın.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Adım 1 - Bu sorunun bilinen bir sorun olup olmadığını kontrol edin

::: moniker range="vs-2017"

Visual Studio Installer ile Microsoft'un düzeltmeye çalıştığı bilinen bazı sorunlar vardır. Sorununuz için geçici çözüm olup olmadığını görmek [için, sürüm notlarımızın Bilinen Sorunlar bölümünü kontrol edin.](/visualstudio/releasenotes/vs2017-relnotes#-known-issues)

::: moniker-end

::: moniker range="vs-2019"

Visual Studio Installer ile Microsoft'un düzeltmeye çalıştığı bilinen bazı sorunlar vardır. Sorununuz için geçici çözüm olup olmadığını görmek [için, sürüm notlarımızın Bilinen Sorunlar bölümünü kontrol edin.](/visualstudio/releases/2019/release-notes#-known-issues)

::: moniker-end

### <a name="step-2---check-with-the-developer-community"></a>Adım 2 - Geliştirici topluluğuna danışın

[Visual Studio Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html)ile hata iletinizi arayın. Topluluğun diğer üyeleri sorununuzun bir çözümünün belgelenmiş olabileceğini bilir.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Adım 3 - Yükseltme sorunlarını gidermek için Visual Studio Installer dizinini silin

Visual Studio Installer bootstrapper Visual Studio Installer geri kalanını yükler minimal hafif çalıştırılabilir. Visual Studio Installer dosyalarını siler ve sonra bootstrapper yeniden bazı güncelleme hataları çözebilir.

> [!NOTE]
> Aşağıdaki eylemleri gerçekleştirmek Visual Studio Installer dosyalarını yeniden yükler ve yükleme meta verilerini sıfırlar.

::: moniker range="vs-2017"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio Yükleyici dizinini silin. Genellikle, dizin `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Visual Studio Installer bootstrapper çalıştırın. Bootstrapper'ı İndirilenler klasörünüzde bir desen `vs_[Visual Studio edition]__*.exe` izleyen bir dosya adı içeren bir dosya adı ile bulabilirsiniz. Bu uygulamayı bulamazsanız, [Visual Studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) giderek ve Visual Studio sürümünüz için **İndir'e** tıklayarak bootstrapper'ı indirebilirsiniz. Ardından, yükleme meta verilerinizi sıfırlamak için yürütülebilir çalıştırın.
4. Visual Studio'yı yeniden yüklemeyi veya güncelleştirmeyi deneyin. Yükleyici başarısız olmaya devam ederse, bir sonraki adıma geçin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio Yükleyici dizinini silin. Genellikle, dizin `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Visual Studio Installer bootstrapper çalıştırın. Bootstrapper'ı İndirilenler klasörünüzde bir desen `vs_[Visual Studio edition]__*.exe` izleyen bir dosya adı içeren bir dosya adı ile bulabilirsiniz. Bu uygulamayı bulamazsanız, [Visual Studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) giderek ve Visual Studio sürümünüz için **İndir'e** tıklayarak bootstrapper'ı indirebilirsiniz. Ardından, yükleme meta verilerinizi sıfırlamak için yürütülebilir çalıştırın.
4. Visual Studio'yı yeniden yüklemeyi veya güncelleştirmeyi deneyin. Yükleyici başarısız olmaya devam ederse, bir sonraki adıma geçin.

::: moniker-end

### <a name="step-4---report-a-problem"></a>Adım 4 - Bir sorunu bildirin

Bozuk dosyalarla ilgili olanlar gibi bazı durumlarda, sorunlara duruma göre bakılması gerekebilir. Size yardımcı olmak için lütfen aşağıdakileri yapın:

::: moniker range="vs-2017"

1. Kurulum günlüklerinizi toplayın. Ayrıntılar için [Visual Studio yükleme günlüklerini nasıl alacağına](#installation-logs) bakın.
2. Visual Studio Installer'ı açın ve ardından Visual Studio Geri Bildirim aracını açmak için **bir sorunu Bildir'i** tıklatın.
![Geri bildirim aracını açmak için Geri Bildirim Ver düğmesine basabilirsiniz](media/report-a-problem.png)
3. Sorun raporunuza bir başlık verin ve ilgili ayrıntıları sağlayın. **Ekler** bölümüne gitmek için **İleri'yi** tıklatın ve ardından oluşturulan günlük dosyasını `%TEMP%\vslogs.zip`(genellikle dosya şu anda) ekler.
4. Sorun raporunuzu gözden geçirmek için **İleri'yi** tıklatın ve sonra **Gönder'i**tıklatın.

::: moniker-end

::: moniker range="vs-2019"

1. Kurulum günlüklerinizi toplayın. Ayrıntılar için [Visual Studio yükleme günlüklerini nasıl alacağına](#installation-logs) bakın.
2. Visual Studio Installer'ı açın ve ardından Visual Studio Geri Bildirim aracını açmak için **bir sorunu Bildir'i** tıklatın.
![Geri bildirim aracını açmak için Geri Bildirim Ver düğmesine basabilirsiniz](media/vs-2019/vs-installer-report-problem.png)
3. Sorun raporunuza bir başlık verin ve ilgili ayrıntıları sağlayın. **Ekler** bölümüne gitmek için **İleri'yi** tıklatın ve ardından oluşturulan günlük dosyasını `%TEMP%\vslogs.zip`(genellikle dosya şu anda) ekler.
4. Sorun raporunuzu gözden geçirmek için **İleri'yi** tıklatın ve sonra **Gönder'i**tıklatın.

::: moniker-end

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Adım 5 - Yükleme dosyalarını kaldırmak için InstallCleanup.exe'yi çalıştırın

Son çare olarak, tüm yükleme dosyalarını ve ürün bilgilerini kaldırmak için [Visual Studio'u kaldırabilirsiniz.](remove-visual-studio.md)

1. Görsel Studio [Kaldır](remove-visual-studio.md)yönergeleri izleyin.
2. Adım 3 açıklanan bootstrapper rerun [- Yükseltme sorunlarını gidermek için Visual Studio Installer dizini silin.](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)
3. Visual Studio'yı yeniden yüklemeyi veya güncelleştirmeyi deneyin.

### <a name="step-6---contact-us-optional"></a>Adım 6 - Bize ulaşın (isteğe bağlı)

Önceki adımlardan hiçbiri Visual Studio'yu başarılı bir şekilde yüklemenize veya yükseltmenize yardımcı olmazsa, daha fazla yardım için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) destek seçeneğimizi (yalnızca İngilizce) kullanarak bizimle iletişime geçin.

## <a name="offline-installations"></a>Çevrimdışı yüklemeler

Burada, [çevrimdışı yükleme](create-an-offline-installation-of-visual-studio.md) oluşturup yerel bir düzenden yüklediğinizde size yardımcı olabilecek bilinen sorunlar ve bazı geçici geçici çözüm lerle ilgili bir tablo ve bir tablo bulunmaktadır.

| Sorun       | Öğe                   | Çözüm |
| ----------- | ---------------------- | -------- |
| Kullanıcıların dosyalara erişimi yoktur. | izinler (ALA)'lar | Çevrimdışı yüklemeyi paylaşmadan *önce* diğer kullanıcılara Okuma erişimi verecek şekilde izinleri (AA'lar) ayarladığınızdan emin olun. |
| Yeni iş yükleri, bileşenler veya diller yüklenemedi.  | `--layout`  | Kısmi bir düzenden yüklediğinizde ve bu kısmi düzende daha önce indirilmeyen iş yüklerini, bileşenleri veya dilleri seçerseniz Internet erişimine sahip olduğunuzu unutmayın. |

[Bir ağ yüklemesiyle](create-a-network-installation-of-visual-studio.md)ilgili sorunları nasıl çözeceğiniz hakkında daha fazla bilgi için [Visual Studio'yu yüklediğinizde veya kullandığınızda ağla ilgili hataları giderme](troubleshooting-network-related-errors-in-visual-studio.md)konusuna bakın.

## <a name="installation-logs"></a>Yükleme günlükleri

Kurulum günlüklerinin çoğu yükleme sorunlarını gidermek için gereklidir. Visual Studio Installer'da [Sorun Bildir'i](../ide/how-to-report-a-problem-with-visual-studio.md) kullanarak bir sorun gönderdiğinizde, bu günlükler otomatik olarak raporunuza dahil edilir.

Microsoft Support'a başvurursanız, [Microsoft Visual Studio ve .NET Framework Log Collection Tool'u](https://www.microsoft.com/download/details.aspx?id=12493)kullanarak bu kurulum günlüklerini sağlamanız gerekebilir. Günlük toplama aracı, .NET Framework, Windows SDK ve SQL Server dahil olmak üzere Visual Studio tarafından yüklenen tüm bileşenlerden kurulum günlükleri toplar. Ayrıca bilgisayar bilgileri, Windows Installer envanteri ve Visual Studio Installer, Windows Installer ve System Restore için Windows olay günlüğü bilgilerini toplar.

Günlükleri toplamak için:

1. [Aracı indirin.](https://www.microsoft.com/download/details.aspx?id=12493)
2. Bir yönetim komut istemi açın.
3. Aracı `Collect.exe` kaydettiğiniz dizinden çalıştırın.
4. Örneğin, dizininizde `vslogs.zip` `%TEMP%` ortaya çıkan dosyayı `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`bulun.

> [!NOTE]
> Araç, başarısız yüklemenin çalıştırıldığı kullanıcı hesabı altında çalıştırılmalıdır. Aracı farklı bir kullanıcı hesabından çalıştırıyorsanız, başarısız yüklemenin çalıştırıldığı kullanıcı hesabını belirtme `–user:<name>` seçeneğini belirleyin. Ek `Collect.exe -?` seçenekler ve kullanım bilgileri için yönetici komut isteminden çalıştırın.

## <a name="live-help"></a>Canlı yardım

Bu sorun giderme kılavuzunda listelenen çözümler Visual Studio'yu başarıyla yüklemenize veya yükseltmenize yardımcı olmazsa, daha fazla yardım için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) destek seçeneğimizi (yalnızca İngilizce) kullanın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yı Kaldır](remove-visual-studio.md)
* [Güvenlik duvarı veya proxy sunucusunun arkasına Visual Studio ve Azure Hizmetleri yükleme ve kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
