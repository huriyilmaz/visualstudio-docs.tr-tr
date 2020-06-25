---
title: Yükleme veya yükseltme sorunlarını giderme
description: Bazen, şeyler yanlış olabilir. Visual Studio yüklemeniz veya yükseltmeniz başarısız olursa, Bu sayfa yardımcı olabilir.
ms.date: 06/24/2020
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
ms.openlocfilehash: 418cc9f75842cb4f3e9d8c0c0753084e2f0633c2
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350816"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Visual Studio yükleme ve yükseltme sorunlarını giderme

> [!IMPORTANT]
> Yükleme sorunu mu yaşıyorsunuz? Yardımcı olabilir. Bir [**yükleme sohbeti**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) için destek seçeneği sunuyoruz.

Bu sorun giderme kılavuzu, çoğu yükleme sorununu çözmek için adım adım yönergeleri içerir.

## <a name="online-installations"></a>Çevrimiçi Yüklemeler

Aşağıdaki adımlar tipik bir çevrimiçi yükleme için iyileştirilmiştir. Çevrimdışı yüklemeyi etkileyen bir sorun için lütfen bkz. [çevrimdışı yükleme sorunlarını giderme](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>1. adım-bu sorunun bilinen bir sorun olup olmadığını denetleyin

::: moniker range="vs-2017"

Microsoft 'un düzeltme üzerinde çalıştığı Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Sorununuz için geçici bir çözüm olup olmadığını görmek için [Sürüm notlarımızın bilinen sorunlar bölümüne](/visualstudio/releasenotes/vs2017-relnotes#-known-issues)bakın.

::: moniker-end

::: moniker range="vs-2019"

Microsoft 'un düzeltme üzerinde çalıştığı Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Sorununuz için geçici bir çözüm olup olmadığını görmek için [Sürüm notlarımızın bilinen sorunlar bölümüne](/visualstudio/releases/2019/release-notes#-known-issues)bakın.

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>2. adım-Visual Studio 'Yu onarmayı deneyin

Onarma birçok yaygın güncelleştirme sorununu düzeltir. Visual Studio 'da onarma işlevinin ne zaman ve nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Visual Studio 'Yu onarma](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>3. adım-geliştirici topluluğuyla denetleme

[Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html)ile hata iletinizde arama yapın. Topluluğun diğer üyeleri sorununuz için bir çözüm belgelenmiş olabilir.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>4. adım-yükseltme sorunlarını giderecek Visual Studio Yükleyicisi dizini silme

Visual Studio Yükleyicisi önyükleyici, Visual Studio Yükleyicisi geri kalanını yükleyen en düşük hafif bir yürütülebilir dosyadır. Visual Studio Yükleyicisi dosyaları silip önyükleyiciyi yeniden çalıştırmak bazı güncelleştirme başarısızlıklarını çözebilir.

> [!NOTE]
> Aşağıdaki eylemlerin gerçekleştirilmesi Visual Studio Yükleyicisi dosyalarını yeniden yükler ve yükleme meta verilerini sıfırlar.

::: moniker range="vs-2017"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio Yükleyicisi dizinini silin. Genellikle dizin olur `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Visual Studio Yükleyicisi önyükleyici çalıştırın. Önyükleyiciyi, bir kalıbı izleyen bir dosya adı ile Indirmeler klasörünüzde bulabilirsiniz `vs_[Visual Studio edition]__*.exe` . Bu uygulamayı bulamazsanız, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına gidip Visual Studio sürümünüz için **İndir** ' e tıklayarak önyükleyici indirebilirsiniz. Sonra, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
4. Visual Studio 'Yu yüklemeyi veya güncelleştirmeyi yeniden deneyin. Yükleyici başarısız olmaya devam ederse, bir sonraki adıma gidin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio Yükleyicisi dizinini silin. Genellikle dizin olur `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Visual Studio Yükleyicisi önyükleyici çalıştırın. Önyükleyiciyi, bir kalıbı izleyen bir dosya adı ile Indirmeler klasörünüzde bulabilirsiniz `vs_[Visual Studio edition]__*.exe` . Bu uygulamayı bulamazsanız, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidip Visual Studio sürümünüz için **İndir** ' e tıklayarak önyükleyici indirebilirsiniz. Sonra, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
4. Visual Studio 'Yu yüklemeyi veya güncelleştirmeyi yeniden deneyin. Yükleyici başarısız olmaya devam ederse, bir sonraki adıma gidin.

::: moniker-end

### <a name="step-5---report-a-problem"></a>5. adım-sorun bildirme

Bozuk dosyalarla ilgili olanlar gibi bazı durumlarda sorunlar, büyük/küçük harfe göre bakıyor olabilir. Size yardımcı olmak için lütfen aşağıdakileri yapın:

::: moniker range="vs-2017"

1. Kurulum günlüklerinizi toplayın. Ayrıntılar için bkz. [Visual Studio yükleme günlüklerini alma](#installation-logs) .
2. Visual Studio Yükleyicisi açın ve ardından Visual Studio geri bildirim aracı 'nı açmak için **sorun bildir** ' e tıklayın.
![Geribildirim aracını açmak için geri bildirim sağla düğmesine Tab ekleyebilirsiniz](media/report-a-problem.png)
3. Sorun için bir başlık bildirin ve ilgili ayrıntıları sağlayın. **Ekler** bölümüne gitmek için **İleri** ' ye tıklayın ve ardından oluşturulan günlük dosyasını (genellikle, dosyanın bulunduğu yer `%TEMP%\vslogs.zip` ) ekleyin.
4. Sorun raporunuzu gözden geçirmek için **İleri** ' ye tıklayın ve ardından **Gönder**' e tıklayın.

::: moniker-end

::: moniker range="vs-2019"

1. Kurulum günlüklerinizi toplayın. Ayrıntılar için bkz. [Visual Studio yükleme günlüklerini alma](#installation-logs) .
2. Visual Studio Yükleyicisi açın ve ardından Visual Studio geri bildirim aracı 'nı açmak için **sorun bildir** ' e tıklayın.
![Geribildirim aracını açmak için geri bildirim sağla düğmesine Tab ekleyebilirsiniz](media/vs-2019/vs-installer-report-problem.png)
3. Sorun için bir başlık bildirin ve ilgili ayrıntıları sağlayın. **Ekler** bölümüne gitmek için **İleri** ' ye tıklayın ve ardından oluşturulan günlük dosyasını (genellikle, dosyanın bulunduğu yer `%TEMP%\vslogs.zip` ) ekleyin.
4. Sorun raporunuzu gözden geçirmek için **İleri** ' ye tıklayın ve ardından **Gönder**' e tıklayın.

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>6. adım-yükleme dosyalarını kaldırmak için InstallCleanup.exe çalıştırma

Son çare olarak, tüm yükleme dosyalarını ve ürün bilgilerini kaldırmak için [Visual Studio 'yu kaldırabilirsiniz](remove-visual-studio.md) .

1. [Visual Studio 'Yu kaldırma](remove-visual-studio.md)bölümündeki yönergeleri izleyin.
2. Adım 4 ' te açıklanan önyükleyiciyi yeniden çalıştırın ve [yükseltme sorunlarını gidermeye yönelik Visual Studio yükleyicisi dizini silin](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Visual Studio 'Yu yüklemeyi veya güncelleştirmeyi yeniden deneyin.

### <a name="step-7---contact-us-optional"></a>7. adım-bizimle Iletişim kurun (isteğe bağlı)

Önceki adımlardan hiçbiri Visual Studio 'Yu başarıyla yüklemenize veya yükseltmenize yardımcı olduysa, daha fazla yardım için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) desteği seçeneğini (yalnızca İngilizce) kullanarak bizimle iletişime geçin.

## <a name="offline-installations"></a>Çevrimdışı yüklemeler

Aşağıda, bir [çevrimdışı yükleme](create-an-offline-installation-of-visual-studio.md) oluştururken ve sonra yerel bir düzenden yüklerken size yardımcı olabilecek bilinen sorunların ve bazı geçici çözümlerin bir tablosu verilmiştir.

| Sorun       | Öğe                   | Çözüm |
| ----------- | ---------------------- | -------- |
| Kullanıcıların dosyalara erişimi yok. | izinler (ACL 'Ler) | Çevrimdışı yüklemeyi paylaşmadan *önce* diğer kullanıcılara okuma erişimi sağlamak için Izinleri (ACL 'ler) ayarladığınızdan emin olun. |
| Yeni iş yükleri, bileşenler veya diller yüklenemez.  | `--layout`  | Kısmi bir düzenden yüklüyorsanız ve bu kısmi düzende daha önce indirilmeyen iş yükleri, bileşenler veya diller ' i seçerseniz Internet erişiminizin olduğundan emin olun. |

Bir [ağ yüklemesiyle](create-a-network-installation-of-visual-studio.md)ilgili sorunları çözme hakkında daha fazla bilgi için bkz. [Visual Studio 'yu yüklerken veya kullanırken ağla Ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Yükleme günlükleri

Kurulum günlükleri, çoğu yükleme sorunlarını gidermek için gereklidir. Visual Studio Yükleyicisi [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) ' i kullanarak bir sorun gönderdiğinizde, bu Günlükler raporunuza otomatik olarak eklenir.

Microsoft Desteği başvurursanız, [Microsoft Visual Studio ve .NET Framework günlük toplama aracını](https://www.microsoft.com/download/details.aspx?id=12493)kullanarak bu kurulum günlüklerini sağlamanız gerekebilir. Günlük toplama aracı, Visual Studio tarafından yüklenen .NET Framework, Windows SDK ve SQL Server dahil tüm bileşenlerin kurulum günlüklerini toplar. Ayrıca, Visual Studio Yükleyicisi, Windows Installer ve sistem geri yükleme için bilgisayar bilgilerini, Windows Installer envanterini ve Windows olay günlüğü bilgilerini toplar.

Günlükleri toplamak için:

1. [Aracı indirin](https://www.microsoft.com/download/details.aspx?id=12493).
2. Bir yönetim komut istemi açın.
3. `Collect.exe`Aracı kaydettiğiniz dizinden çalıştırın.
4. Dizinde elde edilen `vslogs.zip` dosyayı ( `%TEMP%` Örneğin,) bulun `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` .

> [!NOTE]
> Aracın, başarısız olan yüklemenin çalıştırıldığı Kullanıcı hesabı altında çalıştırılması gerekir. Aracı farklı bir kullanıcı hesabından çalıştırıyorsanız, `–user:<name>` başarısız olan yüklemenin çalıştırıldığı Kullanıcı hesabını belirtme seçeneğini belirleyin. `Collect.exe -?`Ek seçenekler ve kullanım bilgileri için yönetici komut isteminden çalıştırın.

## <a name="live-help"></a>Canlı yardım

Bu sorun giderme kılavuzunda listelenen çözümler Visual Studio 'Yu başarıyla yüklemenize veya yükseltmenize yardımcı değilse, daha fazla yardım için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) desteği seçeneğini kullanın (yalnızca İngilizce).

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu onarın](repair-visual-studio.md)
* [Visual Studio 'Yu kaldır](remove-visual-studio.md)
* [Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
