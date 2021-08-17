---
title: Yükleme veya yükseltme sorunlarını giderme
description: Bazen, şeyler yanlış olabilir. Visual Studio yüklemeniz veya yükseltmeniz başarısız olursa, bu sayfa yardımcı olabilir.
ms.date: 06/24/2020
ms.custom: vs-acquisition
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 75952c2fc827b5a4e37339e99615ae0447b916c9ac64d21718c59c147456197b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121356678"
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

::: moniker range=">=vs-2019"

Microsoft 'un düzeltme üzerinde çalıştığı Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Sorununuz için geçici bir çözüm olup olmadığını görmek için [Sürüm notlarımızın bilinen sorunlar bölümüne](/visualstudio/releases/2019/release-notes#-known-issues)bakın.

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>2. adım-Visual Studio onarmayı deneyin

Onarma birçok yaygın güncelleştirme sorununu düzeltir. Visual Studio 'de onarma işlevinin ne zaman ve nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [repair Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>3. adım-geliştirici topluluğuyla denetleme

[Visual Studio geliştirici Community](https://aka.ms/feedback/suggest?space=8)hata iletinizde arama yapın. Topluluğun diğer üyeleri sorununuz için bir çözüm belgelenmiş olabilir.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>4. adım-yükseltme sorunlarını giderecek Visual Studio Yükleyicisi dizini silme

Visual Studio Yükleyicisi önyükleyici, Visual Studio Yükleyicisi geri kalanını yükleyen en düşük hafif bir yürütülebilir dosyadır. Visual Studio Yükleyicisi dosyaları silip önyükleyiciyi yeniden çalıştırmak bazı güncelleştirme başarısızlıklarını çözebilir.

> [!NOTE]
> aşağıdaki eylemlerin gerçekleştirilmesi Visual Studio Yükleyicisi dosyalarını yeniden yükler ve yükleme meta verilerini sıfırlar.

::: moniker range="vs-2017"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio Yükleyicisi dizinini silin. Genellikle dizin olur `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Visual Studio Yükleyicisi önyükleyici çalıştırın. Önyükleyiciyi, bir kalıbı izleyen bir dosya adı ile Indirmeler klasörünüzde bulabilirsiniz `vs_[Visual Studio edition]__*.exe` . bu uygulamayı bulamazsanız, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına gidip Visual Studio sürümünüz için **indir** ' e tıklayarak önyükleyiciyi indirebilirsiniz. Sonra, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
4. Visual Studio yüklemeyi veya güncelleştirmeyi yeniden deneyin. Yükleyici başarısız olmaya devam ederse, bir sonraki adıma gidin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio Yükleyicisi dizinini silin. Genellikle dizin olur `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Visual Studio Yükleyicisi önyükleyici çalıştırın. Önyükleyiciyi, bir kalıbı izleyen bir dosya adı ile Indirmeler klasörünüzde bulabilirsiniz `vs_[Visual Studio edition]__*.exe` . bu uygulamayı bulamazsanız, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidip Visual Studio sürümünüz için **indir** ' e tıklayarak önyükleyiciyi indirebilirsiniz. Sonra, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
4. Visual Studio yüklemeyi veya güncelleştirmeyi yeniden deneyin. Yükleyici başarısız olmaya devam ederse, bir sonraki adıma gidin.

::: moniker-end

### <a name="step-5---report-a-problem"></a>5. adım-sorun bildirme

Bozuk dosyalarla ilgili olanlar gibi bazı durumlarda sorunlar, büyük/küçük harfe göre bakıyor olabilir. Size yardımcı olmak için lütfen aşağıdakileri yapın:

::: moniker range="vs-2017"

1. Kurulum günlüklerinizi toplayın. ayrıntılar için [Visual Studio yükleme günlüklerini alma](#installation-logs) bölümüne bakın.
2. Visual Studio Yükleyicisi açın ve Visual Studio geri bildirim aracını açmak için **sorun bildir** ' e tıklayın.
![Geribildirim aracını açmak için geri bildirim sağla düğmesine Tab ekleyebilirsiniz](media/report-a-problem.png)
3. Sorun için bir başlık bildirin ve ilgili ayrıntıları sağlayın. **Ekler** bölümüne gitmek için **İleri** ' ye tıklayın ve ardından oluşturulan günlük dosyasını (genellikle, dosyanın bulunduğu yer `%TEMP%\vslogs.zip` ) ekleyin.
4. Sorun raporunuzu gözden geçirmek için **İleri** ' ye tıklayın ve ardından **Gönder**' e tıklayın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Kurulum günlüklerinizi toplayın. ayrıntılar için [Visual Studio yükleme günlüklerini alma](#installation-logs) bölümüne bakın.
2. Visual Studio Yükleyicisi açın ve Visual Studio geri bildirim aracını açmak için **sorun bildir** ' e tıklayın.
![Geribildirim aracını açmak için geri bildirim sağla düğmesine Tab ekleyebilirsiniz](media/vs-2019/vs-installer-report-problem.png)
3. Sorun için bir başlık bildirin ve ilgili ayrıntıları sağlayın. **Ekler** bölümüne gitmek için **İleri** ' ye tıklayın ve ardından oluşturulan günlük dosyasını (genellikle, dosyanın bulunduğu yer `%TEMP%\vslogs.zip` ) ekleyin.
4. Sorun raporunuzu gözden geçirmek için **İleri** ' ye tıklayın ve ardından **Gönder**' e tıklayın.

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>6. adım-yükleme dosyalarını kaldırmak için InstallCleanup.exe çalıştırma

son çare olarak, tüm yükleme dosyalarını ve ürün bilgilerini kaldırmak için [Visual Studio kaldırabilirsiniz](remove-visual-studio.md) .

1. [Visual Studio kaldır](remove-visual-studio.md)' daki yönergeleri izleyin.
2. adım 4 ' te açıklanan önyükleyiciyi yeniden çalıştırın ve [yükseltme sorunlarını gidermeye yönelik Visual Studio Yükleyicisi dizini silin](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Visual Studio yüklemeyi veya güncelleştirmeyi yeniden deneyin.

### <a name="step-7---contact-us-optional"></a>7. adım-bizimle Iletişim kurun (isteğe bağlı)

önceki adımlardan hiçbiri Visual Studio başarıyla yüklemenize veya yükseltmenize yardımcı olduysa, daha fazla yardım için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) desteği seçeneğini (yalnızca ingilizce) kullanarak bizimle iletişime geçin.

## <a name="offline-installations"></a>Çevrimdışı yüklemeler

Aşağıda, bir [çevrimdışı yükleme](create-an-offline-installation-of-visual-studio.md) oluştururken ve sonra yerel bir düzenden yüklerken size yardımcı olabilecek bilinen sorunların ve bazı geçici çözümlerin bir tablosu verilmiştir.

| Sorun       | Öğe                   | Çözüm |
| ----------- | ---------------------- | -------- |
| Kullanıcıların dosyalara erişimi yok. | izinler (ACL 'Ler) | Çevrimdışı yüklemeyi paylaşmadan  *önce* diğer kullanıcılara okuma erişimi sağlamak için Izinleri (ACL 'ler) ayarladığınızdan emin olun. |
| Yeni iş yükleri, bileşenler veya diller yüklenemedi.  | `--layout`  | Kısmi bir düzenden yüklüyorsanız ve bu kısmi düzende daha önce indirilmeyen iş yükleri, bileşenler veya diller ' i seçerseniz Internet erişiminizin olduğundan emin olun. |

Bir [ağ yüklemesiyle](create-a-network-installation-of-visual-studio.md)ilgili sorunları çözme hakkında daha fazla bilgi için bkz. [Visual Studio yüklerken veya kullanırken ağla Ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Yükleme günlükleri

Kurulum günlükleri, çoğu yükleme sorunlarını gidermek için gereklidir. Visual Studio Yükleyicisi [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) ' i kullanarak bir sorun gönderdiğinizde, bu günlükler raporunuza otomatik olarak eklenir.

Microsoft Desteği başvurursanız, [Microsoft Visual Studio ve .NET Framework günlük toplama aracını](https://www.microsoft.com/download/details.aspx?id=12493)kullanarak bu kurulum günlüklerini sağlamanız gerekebilir. günlük toplama aracı, .NET Framework, Windows SDK ve SQL Server dahil olmak üzere Visual Studio tarafından yüklenen tüm bileşenlerden kurulum günlüklerini toplar. Bu araç bilgisayar bilgilerini, Windows Installer envanterini, ayrıca Visual Studio Installer, Windows Installer ve Sistem Geri Yükleme için Windows olay günlüğü bilgilerini de toplar.

Günlükleri toplamak için:

1. [Aracı indirin](https://www.microsoft.com/download/details.aspx?id=12493).
2. Bir yönetim komut istemi açın.
3. `Collect.exe`Aracı kaydettiğiniz dizinden çalıştırın.
4. Dizinde elde edilen `vslogs.zip` dosyayı ( `%TEMP%` Örneğin,) bulun `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` .

> [!NOTE]
> Aracın, başarısız olan yüklemenin çalıştırıldığı Kullanıcı hesabı altında çalıştırılması gerekir. Aracı farklı bir kullanıcı hesabından çalıştırıyorsanız, `–user:<name>` başarısız olan yüklemenin çalıştırıldığı Kullanıcı hesabını belirtme seçeneğini belirleyin. `Collect.exe -?`Ek seçenekler ve kullanım bilgileri için yönetici komut isteminden çalıştırın.

## <a name="live-help"></a>Canlı yardım

bu sorun giderme kılavuzunda listelenen çözümler Visual Studio başarıyla yüklemenize veya yükseltmenize yardımcı değilse, daha fazla yardım için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) desteği seçeneğini kullanın (yalnızca ingilizce).

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu onarın](repair-visual-studio.md)
* [Visual Studio kaldır](remove-visual-studio.md)
* [Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
