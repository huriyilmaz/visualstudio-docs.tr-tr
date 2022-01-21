---
title: Yükleme veya yükseltme sorunlarını giderme
description: Bazen, şeyler yanlış olabilir. Visual Studio yüklemeniz veya yükseltmeniz başarısız olursa, bu sayfa yardımcı olabilir.
ms.date: 09/14/2021
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
ms.openlocfilehash: 1d1d5571e0f1c781e547203ce11dabbb9e1a4be8
ms.sourcegitcommit: 7746657b87b22a7684e79e508af598b02dfe24b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "137609631"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Visual Studio yükleme ve yükseltme sorunlarını giderme

> [!IMPORTANT]
> Yükleme sorunu mu yaşıyorsunuz? Yardımcı olabilir. Bir [**yükleme sohbeti**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) için destek seçeneği sunuyoruz.

Bu sorun giderme kılavuzu, çoğu yükleme sorununu çözmek için adım adım yönergeleri içerir.

## <a name="online-installations"></a>Çevrimiçi Yüklemeler

Aşağıdaki adımlar tipik bir çevrimiçi yükleme için geçerlidir. Çevrimdışı yükleme için bkz. [çevrimdışı yükleme sorunlarını giderme](#offline-installations).

### <a name="step-1---check-whether-the-problem-is-a-known-issue"></a>1. adım-sorunun bilinen bir sorun olup olmadığını denetleyin

::: moniker range="vs-2017"

Microsoft 'un düzeltme üzerinde çalıştığı Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Sorununuz için geçici bir çözüm olup olmadığını görmek için [Sürüm notlarımızın bilinen sorunlar bölümüne](/visualstudio/releasenotes/vs2017-relnotes#-known-issues)bakın.

::: moniker-end

::: moniker range="vs-2019"

Microsoft 'un düzeltme üzerinde çalıştığı Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Sorununuz için geçici bir çözüm olup olmadığını görmek için [Sürüm notlarımızın bilinen sorunlar bölümüne](/visualstudio/releases/2019/release-notes#-known-issues)bakın.

::: moniker-end

::: moniker range=">=vs-2022"

Microsoft 'un düzeltme üzerinde çalıştığı Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Sorununuzun zaten çözüldü olup olmadığını denetleyin veya [Sürüm notlarımızın bilinen sorunlar bölümünde](/visualstudio/releases/2022/release-notes#-known-issues)geçici çözümler bulun.

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>2. adım-Visual Studio onarmayı deneyin

Onarma birçok yaygın güncelleştirme sorununu düzeltir. Visual Studio nasıl ve nasıl onarılacağı hakkında daha fazla bilgi için bkz. [repair Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>3. adım-geliştirici topluluğuyla denetleme

[Visual Studio geliştirici Community](https://aka.ms/feedback/suggest?space=8) kanalında hata iletinizi arayın. Topluluğun diğer üyeleri, sorununuza yönelik bir çözüm veya geçici çözüm bulunmuş olabilir.

### <a name="step-4---delete-the-visual-studio-installer-folder-to-fix-upgrade-problems"></a>4. adım-yükseltme sorunlarını giderecek Visual Studio Yükleyicisi klasörünü silme

Visual Studio Yükleyicisi önyükleyici, Visual Studio Yükleyicisi yüklemesini başlatan hafif bir yürütülebilir dosyadır. Visual Studio Yükleyicisi dosyalarını silip önyükleyici yeniden çalıştırmak bazı güncelleştirme başarısızlıklarını çözer.

> [!NOTE]
> aşağıdaki eylemlerin gerçekleştirilmesi Visual Studio Yükleyicisi dosyalarını yeniden yükler ve yükleme meta verilerini sıfırlar.

::: moniker range="vs-2017"

1. Visual Studio Yükleyicisi’ni kapatın.
1. Visual Studio Yükleyicisi yükleme dizinini silin. Genellikle dizin olur `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
1. Visual Studio Yükleyicisi önyükleyici çalıştırın. Önyükleyiciyi, bir kalıbı izleyen bir dosya adı ile Indirmeler klasörünüzde bulabilirsiniz `vs_[Visual Studio edition]__*.exe` . bu uygulamayı bulamazsanız, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına gidip Visual Studio sürümünüz için **indir** ' e tıklayarak önyükleyiciyi indirebilirsiniz. Sonra, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
1. Visual Studio yüklemeyi veya güncelleştirmeyi yeniden deneyin. Yükleyici başarısız olmaya devam ederse, bir sonraki adıma gidin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio Yükleyicisi’ni kapatın.
1. Visual Studio Yükleyicisi dizinini silin. Genellikle dizin olur `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
1. Visual Studio Yükleyicisi önyükleyici çalıştırın. Önyükleyiciyi, bir düzeniyle eşleşen bir dosya adı ile Indirmeler klasörünüzde bulabilirsiniz `vs_[Visual Studio edition]__*.exe` . bu uygulamayı bulamazsanız, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidip Visual Studio sürümünüz için **indir** ' e tıklayarak önyükleyiciyi indirebilirsiniz. Sonra, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
1. Visual Studio yüklemeyi veya güncelleştirmeyi yeniden deneyin. Yükleyici başarısız olmaya devam ederse, bir sonraki adıma gidin.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio Yükleyicisi’ni kapatın.
1. Visual Studio Yükleyicisi klasörünü silin. Genellikle, klasör yolu `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
1. Visual Studio Yükleyicisi önyükleyici çalıştırın. Önyükleyiciyi, bir düzeniyle eşleşen bir dosya adı ile **indirmeler** klasörünüzde bulabilirsiniz `vs_[Visual Studio edition]__*.exe` . ya da, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasından Visual Studio sürümünüz için önyükleyici indirebilirsiniz. Sonra, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
1. Visual Studio yüklemeyi veya güncelleştirmeyi yeniden deneyin. Visual Studio Yükleyicisi başarısız olmaya devam ederse [sorun bildir](#step-5---report-a-problem) adımını izleyin.

::: moniker-end

### <a name="step-5---report-a-problem"></a>5. adım-sorun bildirme

Bazı durumlarda (bozuk dosyalar gibi), sorunlar büyük/küçük harfe sorun giderme gerektirebilir. Size yardımcı olmak için şu adımları izleyin:

::: moniker range="vs-2017"

1. Kurulum günlüklerinizi toplayın. ayrıntılar için [Visual Studio yükleme günlüklerini alma](#installation-logs) bölümüne bakın.
1. Visual Studio Yükleyicisi açın ve Visual Studio geri bildirim aracını açmak için **sorun bildir** ' e tıklayın.
![Visual Studio Yükleyicisi geri bildirim sağla düğmesini gösteren ekran görüntüsü.](media/report-a-problem.png)
1. Sorun için bir başlık bildirin ve ilgili ayrıntıları sağlayın. **Ekler** bölümüne gitmek için **İleri** ' ye tıklayın ve ardından oluşturulan günlük dosyasını (genellikle, dosyanın bulunduğu yer `%TEMP%\vslogs.zip` ) ekleyin.
1. Sorun raporunu gözden geçirmek için **İleri** ' ye tıklayın ve ardından **Gönder**' e tıklayın.

::: moniker-end

::: moniker range="vs-2019"

1. Kurulum günlüklerinizi toplayın. ayrıntılar için [Visual Studio yükleme günlüklerini alma](#installation-logs) bölümüne bakın.
1. Visual Studio Yükleyicisi açın ve Visual Studio geri bildirim aracını açmak için **sorun bildir** ' e tıklayın.
![Visual Studio Yükleyicisi geri bildirim sağla düğmesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-report-problem.png)
1. Sorun için bir başlık bildirin ve ilgili ayrıntıları sağlayın. **Ekler** bölümüne gitmek için **İleri** ' ye tıklayın ve ardından oluşturulan günlük dosyasını (genellikle, dosyanın bulunduğu yer `%TEMP%\vslogs.zip` ) ekleyin.
1. Sorun raporunuzu gözden geçirmek için **İleri** ' ye tıklayın ve ardından **Gönder**' e tıklayın.

::: moniker-end

::: moniker range=">=vs-2022"

1. Kurulum günlüklerinizi toplayın. ayrıntılar için [Visual Studio yükleme günlüklerini alma](#installation-logs) bölümüne bakın.
1. Visual Studio Yükleyicisi açın ve Visual Studio geri bildirim aracını açmak için **sorun bildir** ' i seçin.
![Visual Studio Yükleyicisi geri bildirim sağla düğmesini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-report-problem.png)
1. Sorununuz için bir başlık bildirin ve ilgili ayrıntıları sağlayın. Visual Studio Yükleyicisi için en son kurulum günlüğü, sorun raporunuzun **ek ekler** bölümüne otomatik olarak eklenir.
1. **Gönder**' i seçin.

::: moniker-end

### <a name="step-6---remove-visual-studio-installation-files"></a>6. adım-yükleme dosyalarını kaldırma Visual Studio

son çare olarak, tüm Visual Studio yükleme dosyalarını ve ürün bilgilerini kaldırabilirsiniz:

1. bu makaledeki adımları izleyin: Visual Studio sayfasını [kaldırın](uninstall-visual-studio.md#remove) .
1. Visual Studio Yükleyicisi önyükleyiciyi yeniden çalıştırın. Önyükleyiciyi, bir düzeniyle eşleşen bir dosya adı ile **indirmeler** klasörünüzde bulabilirsiniz `vs_[Visual Studio edition]__*.exe` . ya da, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasından Visual Studio sürümünüz için önyükleyici indirebilirsiniz.
1. Visual Studio yeniden yüklemeyi deneyin.

### <a name="step-7---contact-us-optional"></a>7. adım-bizimle Iletişim kurun (isteğe bağlı)

önceki adımlardan hiçbiri Visual Studio başarıyla yüklemenize veya yükseltmenize yardımcı olduysa, daha fazla yardım için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) desteği seçeneğini (yalnızca ingilizce) kullanarak bizimle iletişime geçin.

## <a name="offline-installations"></a>Çevrimdışı yüklemeler

Aşağıda, [çevrimdışı yükleme](create-an-offline-installation-of-visual-studio.md) oluştururken ve yerel bir düzenden yüklerken size yardımcı olabilecek bazı bilinen sorunlar ve geçici çözümler verilmiştir.

| Sorun       | Çözüm |
| ----------- | -------- |
| Kullanıcılar dosyalara erişemez | Çevrimdışı yüklemeyi paylaşmadan *önce* diğer kullanıcılara **okuma** erişimi sağlamak Için izinleri (ACL 'ler) ayarladığınızdan emin olun. |
| Yeni iş yükleri, bileşenler veya dil paketleri yüklenemeyebilir | Kısmi düzenden yüklüyorsanız ve daha önce bu kısmi düzen için indirilmiş olmayan iş yükleri, bileşenler veya diller ' i seçerseniz Internet erişiminizin olduğundan emin olun. |

Bir [ağ yüklemesiyle](create-a-network-installation-of-visual-studio.md)ilgili sorunları gidermek için bkz. [Visual Studio yüklerken veya kullanırken ağla Ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Yükleme günlükleri

Kurulum günlükleri çoğu yükleme sorununu gidermenize yardımcı olur. Visual Studio Yükleyicisi [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) ' i kullanarak bir sorun gönderdiğinizde, Visual Studio Yükleyicisi için en son kurulum günlüğü raporunuza otomatik olarak eklenir.

Microsoft Desteği başvurursanız, [Microsoft Visual Studio ve .NET Framework günlük toplama aracını](https://www.microsoft.com/download/details.aspx?id=12493)kullanarak kurulum günlüklerini toplamanız istenebilir. günlük toplama aracı, .NET Framework, Windows SDK ve SQL Server dahil olmak üzere Visual Studio tarafından yüklenen tüm bileşenlerden kurulum günlüklerini toplar. ayrıca bilgisayar bilgilerini, Windows Installer envanterini ve Visual Studio Yükleyicisi, Windows Installer ve sistem geri yükleme için olay günlüğü bilgilerini Windows toplar.

Günlükleri toplamak için:

1. [Aracı indirin](https://www.microsoft.com/download/details.aspx?id=12493).
1. Bir yönetim komut istemi açın.
1. `Collect.exe`Aracını kaydettiğiniz klasörde çalıştırın.
1. Araç `vslogs.zip` `%TEMP%` , klasörünüzde genellikle adresinde bir dosya oluşturur `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` .

> [!NOTE]
> Aracın, başarısız olan yüklemenin çalıştırıldığı Kullanıcı hesabı altında çalıştırılması gerekir. Aracı farklı bir kullanıcı hesabından çalıştırıyorsanız, `–user:<name>` başarısız olan yüklemenin çalıştırıldığı Kullanıcı hesabını belirtme seçeneğini belirleyin. `Collect.exe -?`Ek seçenekler ve kullanım bilgileri için yönetici komut isteminden çalıştırın.

## <a name="problems-installing-webview2"></a>WebView2 yükleme sorunları

WebView2, Visual Studio için gereken bir bileşendir, ancak bu bileşenin yüklenmesi kuruluşunuzun grup ilkeleri tarafından engellenebilir. WebView2 yüklemesinin engellenmesi, Visual Studio yüklenmesini engeller. 

iki ilke, WebView2 [' ınstall (WebView) ' Microsoft Edge](/deployedge/microsoft-edge-update-policies#install-webview) ve [' ınstalldefault ' Microsoft Edge](/deployedge/microsoft-edge-update-policies#installdefault)yükleyebilme özelliğini denetler.

• Microsoft Edge ' ınstall (WebView) ' ilkesi yapılandırılırsa, WebView2 yüklenip yüklenemeyeceğini tespit eder.
• Microsoft Edge ' ınstall (WebView) ' ilkesi yapılandırılmamışsa, Microsoft Edge ' ınstalldefault ' ilkesi, WebView2 'in yüklenip yüklenmeyeceğini belirlemektir.

> [!NOTE]
> Hiçbiri ilke yapılandırılmamışsa, WebView2 yüklemesine kuruluşunuz tarafından izin verilir.

## <a name="live-help"></a>Canlı yardım

bu sorun giderme kılavuzunda listelenen çözümler Visual Studio başarıyla yüklemenize veya yükseltmenize yardımcı değilse, daha fazla yardım için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) desteği seçeneğini kullanın (yalnızca ingilizce).

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu onarın](repair-visual-studio.md)
* [Visual Studio kaldır](uninstall-visual-studio.md#remove)
* [Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)